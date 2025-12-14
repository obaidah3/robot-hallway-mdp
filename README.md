# 🤖 Robot Hallway MDP - Interactive Reinforcement Learning Simulator

An interactive visualization tool for understanding Markov Decision Processes (MDPs) through a simple robot navigation problem. This project demonstrates both the theoretical algorithms and practical simulation of reinforcement learning concepts.

---
<img width="1887" height="1053" alt="Image" src="https://github.com/user-attachments/assets/0cf2aa54-48e4-4581-965b-74e0ac969b3e" />

<img width="1894" height="1079" alt="Image" src="https://github.com/user-attachments/assets/c7069811-8ef0-4ae8-935e-d85557a43616" />

---
## 📋 Table of Contents

- [Overview](#overview)
- [Problem Description](#problem-description)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [MDP Formulation](#mdp-formulation)
- [Algorithms](#algorithms)
- [Project Structure](#project-structure)
- [Scenarios](#scenarios)
- [Technologies](#technologies)

## 🎯 Overview

This project implements a **Markov Decision Process (MDP)** solver with an interactive React-based visualization. A robot navigates a 1D hallway with 4 positions, aiming to reach a charging station while dealing with uncertain movements and various environmental challenges.

The project includes:
- ✅ **Python implementation** (Jupyter Notebook) - Core MDP algorithms
- ✅ **React web application** - Interactive visualization and simulation
- ✅ **Multiple scenarios** - Different reward structures and obstacles
- ✅ **Two algorithms** - Value Iteration and Policy Iteration

## 🚀 Problem Description

### Scenario
A robot moves along a hallway with 4 positions: `[0, 1, 2, 3]`

**Goal:** Reach the charging station at position 3

### MDP Components

#### States (S)
The robot's position: `S = {0, 1, 2, 3}`

#### Actions (A)
At each step, the robot can choose:
- `LEFT` - Attempt to move left
- `RIGHT` - Attempt to move right

#### Transition Probabilities (T)
Motion is **stochastic** (noisy):
- **Intended action succeeds:** 80% probability
- **Robot stays in place:** 20% probability (slips)
- Boundaries are enforced (cannot move outside [0,3])

#### Rewards (R)
- **Reaching charging station (state 3):** +10
- **Every other move:** -1 (step cost)
- **Terminal state:** State 3 (episode ends)

#### Discount Factor (γ)
- Default: 0.9 (adjustable in web app)
- Balances immediate vs. future rewards

## ✨ Features

### Interactive Web Application
- 🎮 **Real-time simulation** - Watch the robot navigate using the optimal policy
- 🎨 **Visual feedback** - Color-coded states (goals, hazards, rewards)
- 📊 **Algorithm comparison** - Switch between Value Iteration and Policy Iteration
- ⚙️ **Configurable parameters** - Adjust discount factor and animation speed
- 📈 **Performance metrics** - Track steps, rewards, and stuck instances
- 🎯 **Multiple scenarios** - 6 pre-built scenarios with different challenges
- 📝 **Movement history** - Detailed log of robot's actions and outcomes

### Python Implementation
- 🐍 **Clean NumPy implementation** - Easy to understand and modify
- 📓 **Jupyter Notebook** - Step-by-step explanation with outputs
- 🔄 **Simulation testing** - Verify policy from different starting positions
- 📊 **Value convergence** - Visualization of learning process

## 📦 Installation

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn
- Python 3.7+ (for notebook)

### React Application Setup

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/robot-hallway-mdp.git
cd robot-hallway-mdp
```

2. **Install dependencies**
```bash
npm install
```

3. **Install Tailwind CSS**
```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

4. **Configure Tailwind**

Create/edit `tailwind.config.js`:
```javascript
module.exports = {
  content: ["./src/**/*.{js,jsx,ts,tsx}"],
  theme: { extend: {} },
  plugins: [],
}
```

5. **Update CSS**

In `src/index.css`:
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

6. **Start the application**
```bash
npm start
```

The app will open at `http://localhost:3000`

### Python Notebook Setup

1. **Install required packages**
```bash
pip install numpy jupyter
```

2. **Launch Jupyter**
```bash
jupyter notebook MDP.ipynb
```

## 🎮 Usage

### Web Application

1. **Select a scenario** from the scenario selector
2. **Configure settings** (optional):
   - Adjust discount factor (γ)
   - Change animation speed
   - Switch between algorithms
3. **Choose starting position** (0, 1, or 2)
4. **Click "Start"** to watch the robot navigate
5. **Observe**:
   - Optimal policy (π*) for each state
   - Q-values (state-action values)
   - Real-time statistics
   - Movement history

### Python Implementation

Run cells sequentially in the Jupyter notebook:
1. **Define MDP components** (states, actions, transitions, rewards)
2. **Run Value Iteration** algorithm
3. **Extract optimal policy**
4. **Simulate** robot behavior from different starting positions

## 🧮 MDP Formulation

### Mathematical Representation

**State Value Function:**
```
V(s) = max_a Σ P(s'|s,a)[R(s,a,s') + γV(s')]
```

**Optimal Policy:**
```
π*(s) = argmax_a Σ P(s'|s,a)[R(s,a,s') + γV(s')]
```

**Q-Value (Action-Value Function):**
```
Q(s,a) = Σ P(s'|s,a)[R(s,a,s') + γV(s')]
```

### Example Results

**Optimal Values (γ=0.9):**
```
State 0: V(0) = 5.04
State 1: V(1) = 7.13
State 2: V(2) = 9.51
State 3: V(3) = 0.00 (terminal)
```

**Optimal Policy:**
```
State 0: RIGHT
State 1: RIGHT
State 2: RIGHT
State 3: TERMINAL
```

## 🔄 Algorithms

### 1. Value Iteration

**Bellman Optimality Update:**
```python
V(s) ← max_a Σ P(s'|s,a)[R(s,a,s') + γV(s')]
```

**Convergence:** When `max|V_new(s) - V_old(s)| < θ`

**Complexity:** O(|S|²|A|) per iteration

### 2. Policy Iteration

**Two phases:**
1. **Policy Evaluation:** Compute V^π for current policy π
2. **Policy Improvement:** Update π to be greedy w.r.t. V^π

**Convergence:** Typically faster than Value Iteration in practice

## 📂 Project Structure

```
robot-hallway-mdp/
├── src/
│   ├── App.js                 # Main React component
│   ├── index.js               # Entry point
│   └── index.css              # Tailwind imports
├── public/
│   └── index.html
├── MDP.ipynb                  # Python implementation
├── package.json
├── tailwind.config.js
├── README.md
└── .gitignore
```

## 🎯 Scenarios

### 1. Goal on Right ⚡
- **Goal:** Position 3 (+10)
- **Challenge:** Navigate from left to right

### 2. Goal on Left ⚡
- **Goal:** Position 0 (+10)
- **Challenge:** Navigate from right to left

### 3. Middle Treasure 💎
- **Rewards:** Position 1 (+5), Position 3 (+10)
- **Challenge:** Decide whether to collect treasure first

### 4. Avoid Hazard ☠️
- **Goal:** Position 3 (+10)
- **Hazard:** Position 2 (-8)
- **Challenge:** High penalty zone - risk vs. reward

### 5. Two Goals 🎯
- **Rewards:** Position 0 (+3), Position 3 (+10)
- **Challenge:** Choose between nearby small reward or distant large reward

### 6. Expensive Path 💰
- **Goal:** Position 3 (+10)
- **Cost:** Position 2 (-5)
- **Challenge:** Expensive intermediate state affects optimal policy

## 🛠️ Technologies

### Frontend
- **React 18** - UI framework
- **Tailwind CSS** - Styling
- **Lucide React** - Icons
- **JavaScript ES6+** - Core language

### Backend/Algorithm
- **Python 3** - Algorithm implementation
- **NumPy** - Numerical computations
- **Jupyter** - Interactive notebooks

## 📊 Performance Metrics

The application tracks:
- **Steps Taken** - Number of moves to reach goal
- **Total Reward** - Cumulative reward collected
- **Stuck Count** - Times robot failed to move (20% probability)
- **Convergence Time** - Algorithm computation time in milliseconds
- **Iterations** - Number of iterations until convergence

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs
- Suggest new scenarios
- Improve algorithms
- Enhance UI/UX

## 📝 License

This project is licensed under the MIT License.

## 👨‍💻 Author

Created as an educational tool for understanding Markov Decision Processes and Reinforcement Learning fundamentals.

## 📚 References

- Sutton, R. S., & Barto, A. G. (2018). *Reinforcement Learning: An Introduction*
- Bellman, R. (1957). *Dynamic Programming*
- Russell, S., & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach*

## 🎓 Educational Use

This project is ideal for:
- Computer Science students learning RL
- AI/ML course demonstrations
- Self-study and experimentation
- Teaching MDP concepts interactively

---

**⭐ If you find this project helpful, please star the repository!**

## 🐛 Known Issues

- None currently reported

## 🔮 Future Enhancements

- [ ] Add Q-Learning visualization
- [ ] Implement SARSA algorithm
- [ ] 2D grid world environment
- [ ] Policy gradient methods
- [ ] Deep Q-Network (DQN) comparison
- [ ] Export simulation data

---

**Made with ❤️ for Reinforcement Learning Education**
