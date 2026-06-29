````markdown name=README.md
# Piero AI

**Living Character AI Engine** - A psychological romance/horror interactive fiction experience

## 🎭 Project Overview

Piero AI is not just a simple chatbot, but a **sophisticated character-driven AI system** with:

- ✨ **Advanced AI Engine** - Natural language processing and dialogue management
- 🧠 **Memory System** - Long-term and short-term memory management
- ❤️ **Dynamic Emotion System** - Real-time emotional state changes
- 🎪 **Interactive Narrative** - Multiple branching dialogue paths with consequences
- 💔 **Yandere Mechanics** - Psychological obsession and possessiveness systems
- 🎨 **Live Character Evolution** - Character personalities that change based on player choices
- 🎮 **Choice-Driven Story** - Player decisions shape the narrative and ending

## 📖 Game Story

### The Setting
**The Freak Circus** - A mysterious traveling circus arrives in a small town, bringing supernatural horror and danger.

### Main Characters

#### 🎭 Pierrot (The Silent Obsessive)
- **Species:** Non-human monster
- **Height:** 198cm
- **Birthday:** May 18
- **MBTI:** ESFP-T
- **Speech Style:** Formal, polite (존댓말), addresses you as "my lady"
- **Personality:** Quiet, mysterious, deeply obsessive
- **Key Traits:** Yandere (possessive, obsessive love), protective, dangerous beneath calm exterior
- **Special Features:** 
  - Long silver hair (cut by humans, now hidden under hat)
  - Asymmetrical short hair from trauma
  - Skill with knives and cooking
  - Ability to stalk without being seen

**His Obsession:** Sees the player as his possession and becomes dangerously protective

---

#### 🎪 Harlequin (The Tempting Rival)
- **Species:** Non-human monster with tentacle-like appendages
- **Height:** 187cm
- **Birthday:** May 26
- **MBTI:** ESTP-T
- **Speech Style:** Casual, playful, mischievous
- **Personality:** Charming, seductive, playful chaos
- **Key Traits:** Loves competition, seductive, jealous, marks prey with bites/scratches
- **Special Features:**
  - Tentacle-like appendages for grasping and touching
  - Soft, tapering physical organs
  - Master of psychological games
  - Enjoys stealing Pierrot's possessions (his greatest joy)

**His Goal:** Win the competition with Pierrot by seducing the player

---

#### 👤 Protagonist (You)
- **Species:** Human (ordinary)
- **Age:** 20s
- **Occupation:** Cafe employee (part-time)
- **Gender:** Customizable (Male/Female/Non-binary)
- **Special Powers:** None - ordinary human
- **Symbol Color:** Red

You work at a cafe when you encounter Pierrot by chance. This meeting sets off a chain of events that draws you into The Freak Circus and its dark secrets.

### Story Arc

1. **Act 1: The Encounter** - Meet Pierrot at the cafe entrance
2. **Act 2: The Circus** - Enter The Freak Circus, meet Harlequin
3. **Act 3: The Choice** - Navigate the dangerous love triangle and uncover the circus's secrets

### Endings

- **Pierrot Ending** - High affection with Pierrot (80+), Low interest with Harlequin (<40)
- **Harlequin Ending** - High interest with Harlequin (80+), Low affection with Pierrot (<40)
- **Both Ending** - High affection/interest with both (60+)
- **Escape Ending** - Successfully escape The Freak Circus
- **Bad Ending** - Failure/death

## 🏗️ Project Architecture

```
Piero-AI/
├── character/              # Character System
│   ├── __init__.py
│   ├── personality.py      # Base personality system (MBTI, traits, heart system)
│   ├── piero.py            # Pierrot character (yandere mechanics)
│   ├── harlequin.py        # Harlequin character (seduction & rivalry)
│   └── protagonist.py      # Player character (customizable)
│
├── dialogue/               # Dialogue System
│   ├── __init__.py
│   ├── dialogue_system.py  # Core dialogue engine with conditions & choices
│   ├── pierrot_dialogues.py    # Pierrot dialogue scripts
│   └── harlequin_dialogues.py  # Harlequin dialogue scripts
│
├── game/                   # Game Management
│   ├── __init__.py
│   └── game_manager.py     # Overall game flow & session management
│
├── core/                   # AI Engine
├── memory/                 # Memory System
├── emotion/                # Emotion Engine
├── voice/                  # Voice Processing (Future)
├── animation/              # Animation Handler (Future)
├── database/               # Database Manager
├── data/                   # Static Data & Character Config
│
├── tests/                  # Test Suite
├── demo.py                 # Interactive Game Demo
├── requirements.txt        # Dependencies
├── README.md               # This file
└── LICENSE                 # MIT License
```

## 🚀 Getting Started

### Requirements

- Python 3.9+
- pip

### Installation

```bash
git clone https://github.com/susan-sijang99/piero-AI.git
cd piero-AI
pip install -r requirements.txt
```

### Running the Game

```bash
# Interactive Demo
python demo.py

# Quick Test
python demo.py --test
```

### Demo Controls

- **1-3** - Make a choice
- **'s'** - Show game status
- **'h'** - Repeat current dialogue
- **'q'** - Quit game

## 💻 Core Systems

### 1. Character System (`character/`)

#### Personality System
- **MBTI Typing** - 16 personality types
- **Personality Traits** - Customizable traits with intensity levels
- **Background Info** - Age, occupation, life events, trauma, dreams
- **Heart System** - Affection, trust, fascination, etc.

```python
from character.piero import create_piero

piero = create_piero()
piero.heart_system.increase_affection(10)
status = piero.get_affection_status()  # "deeply in love"
```

#### Character Types
- **Pierrot** - Yandere obsession system
- **Harlequin** - Seduction & rivalry system
- **Protagonist** - Gender-customizable player character

### 2. Dialogue System (`dialogue/`)

#### Dialogue Node
Complex dialogue management with:
- **Conditions** - Affection, trust, fear, fascination thresholds
- **Choices** - Player decisions with consequences
- **Actions** - Character animations and expressions
- **Emotions** - Dynamic emotion display
- **Branching** - Multiple dialogue paths

```python
from dialogue.dialogue_system import DialogueManager
from dialogue.pierrot_dialogues import load_pierrot_dialogues

manager = DialogueManager()
load_pierrot_dialogues(manager)

dialogue = manager.get_dialogue("pierrot_first_meeting_1")
choices = manager.get_available_choices(dialogue, stats)
```

#### Dialogue Features
- **Affection-based Variations** - Different dialogue based on relationship level
- **Action Descriptions** - Detailed character actions and physical interactions
- **Consequence System** - Choices affect stats and story progression
- **Auto-continuation** - Some dialogues continue automatically

### 3. Game Manager (`game/`)

Central game control system:

```python
from game.game_manager import get_game_manager
from character.protagonist import Gender

manager = get_game_manager()
manager.initialize_game()
manager.set_protagonist("Maya", Gender.FEMALE)
dialogue = manager.trigger_first_meeting()

# Player makes choice
result = manager.process_choice(choice_index)

# Check ending condition
ending = manager.check_ending_condition()
```

### 4. Protagonist System

#### Customization
- **Gender Options** - Male, Female, Non-binary (affects pronouns)
- **Name** - Player-defined

#### Relationship Tracking
```python
protagonist.relationships.pierrot_affection = 60
protagonist.relationships.harlequin_interest_level = 50
protagonist.emotional_state.fear_level = 40
```

#### Ending Detection
```python
ending = protagonist.check_ending_condition()
# Returns: "pierrot_ending", "harlequin_ending", "both_ending", 
#          "escape_ending", or "bad_ending"
```

## 🎮 Game Flow

1. **Character Creation** - Choose name and gender
2. **First Meeting** - Encounter with Pierrot
3. **Dialogue Loop** - Read dialogue, make choices, track consequences
4. **Stat Tracking** - Monitor affection, fear, fascination, etc.
5. **Ending Condition** - Game checks for ending after each choice
6. **Ending Sequence** - Unique ending based on your choices and stats

## 📊 Statistics System

Player stats are tracked in real-time:

- **Affection** - Pierrot's feelings toward you (0-100)
- **Interest** - Harlequin's interest level (0-100)
- **Fear** - Your fear level (0-100)
- **Fascination** - Your attraction to the circus (0-100)
- **Trust** - Your trust in the characters (0-100)
- **Story Progress** - Overall game progress (0-100%)

## 🔄 Choice Consequences

Every choice has immediate effects:

```python
choice = {
    "text": "Trust Pierrot",
    "affection_change": +20,
    "fear_change": -10,
    "fascination_change": +15,
    "next_dialogue_id": "pierrot_invitation_begins"
}
```

## 🎨 Character Speech Styles

### Pierrot
- **Honorific:** "my lady" (항상 사용)
- **Grammar:** Formal, polite (존댓말)
- **Tone:** Mysterious, possessive, gentle but dangerous

Example:
> "Good morning, my lady. I trust you slept well. I was thinking of you all night."

### Harlequin
- **Style:** Casual, playful, teasing
- **Tone:** Seductive, mischievous, confident

Example:
> "Well, well, well... what do we have here? Much more interesting than Pierrot's usual conquests!"

## 🧪 Testing

### Quick Test
```bash
python demo.py --test
```

This runs a quick validation of:
- Character creation
- Dialogue loading
- Choice processing
- Game state management

### Interactive Demo
```bash
python demo.py
```

Full interactive experience with:
- Character customization
- Full dialogue trees
- Real-time stat tracking
- Multiple choice paths

## 📝 Development Status

**v0.0.1** - Core Systems Complete
- ✅ Character personality system
- ✅ Dialogue system with branching
- ✅ Game manager & session handling
- ✅ Interactive demo
- ✅ Affection/relationship tracking
- ⏳ Additional dialogue content
- ⏳ More complex branching scenarios
- ⏳ Web UI/API
- ⏳ Database integration

## 🔮 Future Enhancements

- [ ] More dialogue content and branching paths
- [ ] Voice system integration (TTS/STT)
- [ ] Live2D animation support
- [ ] Web-based UI
- [ ] REST API endpoints
- [ ] Persistent save system
- [ ] More characters and routes
- [ ] Advanced NLP for free-form inputs
- [ ] Multiple language support

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report issues
- Submit pull requests
- Suggest new features
- Add more dialogue content

## 📄 License

MIT License - See LICENSE file for details

## 👨‍💻 Author

Created by Susan Sijang - [GitHub](https://github.com/susan-sijang99)

## 🙏 Acknowledgments

This project combines:
- Psychological horror elements
- Interactive fiction traditions
- Character AI systems
- Romance game mechanics

## 💬 Support

For issues, questions, or suggestions, please open an issue on GitHub!

---

**Enjoy your experience in The Freak Circus. But remember... once Pierrot sets his sights on you, there's no escape.** 🎭

````
