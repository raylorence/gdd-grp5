# Core Loop
> [!info] Guideline
> Map the primary cyclical sequence of gameplay actions, rewards, and progression steps. What does the player do repeatedly every 2 to 5 minutes?
> > [!tip] You can create your flowcharts using [mermaid](https://mermaid.js.org/) or [draw.io](https://draw.io) as they are compatible within Obsidian. (draw.io requires a community plugin)

```mermaid
graph TD
    recon[1. Reconnaissance<br>Scout patrol routes, flashlight sweeps, and choke points]
    explore[2. Exploration & Movement<br>Sneak through narrow alleys and gather intel/tools]
    distract[3. Environmental Distraction<br>Throw bottles, trigger generators, throw switchboards]
    hide[4. Active Hiding & Suppression<br>Conceal in barrels/alcoves, suppress breathing and panic]
    
    recon --> explore
    explore --> distract
    distract --> hide
    hide --> recon
```

- **[[Reconnaissance]]:** Players observe enemy patrol trajectories, study flashlight patterns, and selectively utilize their smartphone to reveal objective headings and radio chatter, balancing exposure against signal interception.
- **[[Exploration]]:** Navigating narrow alleyways, squatter corridors, zinc roof overhangs, and dead ends of Tondo while scavenging one-time bypass tools (crowbars, wire cutters) and narrative evidence.
- **[[Distraction]]:** Interacting with physical debris (throwing empty bottles, dislodging hanging galvanized metal sheets, tampering with wiring) to peel guards away from essential doorways and corridors.
- **[[Active Hiding]]:** Slipping behind clotheslines, interior alcoves, or beneath empty water drums when line of sight is broken. Shifts perspective to a first-person dynamic vignette where panic level and breathing must be held manually to avoid alerting passing guards.

# Controls & [[Player Actions]]
> [!info] Guideline
> Map system inputs to specific in-game actions, output behavior, and operational constraints.
> > [!tip] Attach an image of the controller you wish to use with the actions mapped out.

- **Camera View:** 2D Top-Down perspective during movement and navigation; switches dynamically to an immersive, claustrophobic 1st-Person Vignette during Active Hiding states.
- **Movement Profile:** Precise multi-directional grid/free 8-way movement; distinct noise footprint contrast between crouching/slow walking and sprinting.

| Input               | Action                      | Context / Notes                                                                                                    |
| ------------------- | --------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| `W / A / S / D`     | [[Movement]]                | Standard walking speed; minimal sound emission radius ($r = 1.5\text{ m}$).                                        |
| `Left Shift`        | [[Sprint]]                  | Increases traversal speed by 80%; expends stamina and dramatically increases audio footprint ($r = 6.0\text{ m}$). |
| `E`                 | [[Interact]]                | Operates doors, gathers collectible documents, throws switches, and Enters/Exits hiding spots.                     |
| `Right Click` / `F` | [[Aim & Throw Distraction]] | Displays targeted trajectory arc to toss scavenged debris (bottles, stones, scrap).                                |
| `Space` (Hold)      | [[Breath Suppression]]      | Active during Hiding state; stops protagonist's heavy breathing while slowly building the Panic meter.             |
| `Tab`               | [[Toggle Smartphone]]       | Opens digital map and intercepted radio feeds; continuously raises the enemy Digital Trace Level while deployed.   |
## Game Rules & Logic
> [!info] Guideline
> Define the operational boundary rules, victory/defeat criteria, and state-persistence systems governing the game session.
- **Win Condition:** Safely traverse all urban sectors (Alleyways, Commercial Market, Drainage Canal, Safehouse Perimeter) without full apprehension, delivering intact evidence to the resistance safehouse.
- **Fail Condition:**
  1. Caught within the capture perimeter of a militarized police officer.
  2. Sustaining direct line of sight in open light without cover for longer than the detection grace timer.
  3. Failure of the Breath Suppression minigame while an investigator searches the immediate hiding radius.
- **Failure Penalty:** Session reloads at the most recent Sector Safe Zone / Infiltration Checkpoint. Run statistics penalize "Times Spotted" and calculate lower end-of-run stealth ratings.
- **Save & Persistence System:** Segment-based automatic checkpointing when transitioning major sector gates. System preserves collected documents, unlocked shortcut gates, and unlocked branch paths into the profile save file.
