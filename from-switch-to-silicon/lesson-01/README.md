<!-- Draft content for lessons/l1-1/README.md in the public practice repo. Not created or pushed. -->
# Lesson 1 · What is electricity? Voltage, current and resistance

**Path:** From Switch to Silicon (step 1 of 10) · **Skill:** HW-01 · **Level:** Beginner · **Time:** about 1.5 hours (video + lab + quiz)
**Video:** link added after the video is published.
**Prerequisites:** none. You need a computer with a web browser. No kit, no account and no install are needed.

## What you will be able to do
- Explain voltage (push), current (flow) and resistance (squeeze) in your own words.
- Use Ohm's law, **V = I × R**, to work out one value from the other two.
- Show that current only flows in a closed loop (closed = on, open = off).

## 0. Get your own copy (fork)
1. Click **Fork** at the top of this repository to make your own copy.
2. Clone your fork: `git clone https://github.com/<your-username>/<repo-name>.git`
3. Go to this lesson: `cd <repo-name>/lessons/l1-1`
4. Optional: make a branch for your notes: `git checkout -b my-l1-1-notes`
You keep your work in your fork. There is no need to send changes back.

## 1. Open the free simulator
Open **PhET Circuit Construction Kit: DC** (University of Colorado Boulder) in your browser:
https://phet.colorado.edu/en/simulations/circuit-construction-kit-dc
Choose the **Lab** screen.

## 2. Build a loop
Drag in a **battery**, a **switch**, a **light bulb** and a **resistor**. Join them with wires into one full loop. Add an **ammeter** (it measures current) inside the loop.

## 3. Measure and check Ohm's law
Fill in `results.md` (copy the table below).

| Try | Battery V (volts) | Resistor R (ohms) | Measured I (amps) | V ÷ R (amps) | Match? |
|---|---|---|---|---|---|
| 1 | | | | | |
| 2 (double R) | | | | | |
| 3 (double V) | | | | | |

Tip: use the resistor alone (remove the bulb) if you want the numbers to match V ÷ R closely, because the bulb adds its own resistance. If your numbers differ a little, write down why you think so.

## 4. Open the switch
Open the switch. Write down what the ammeter shows and what the bulb does.

## 5. Optional: check your table with code
`check_ohms.py` (in this folder) reads your numbers and tells you if they fit V = I × R.
```bash
python3 check_ohms.py 9 3 3.0     # volts ohms measured_amps
```
```python
# check_ohms.py — MIT License (see repo LICENSE)
import sys
def expected_current(volts: float, ohms: float) -> float:
    if ohms <= 0:
        raise ValueError("Resistance must be more than 0 ohms.")
    return volts / ohms
if __name__ == "__main__":
    v, r, measured = map(float, sys.argv[1:4])
    exp = expected_current(v, r)
    ok = abs(exp - measured) <= 0.05 * exp
    print(f"Expected {exp:.3f} A, measured {measured:.3f} A -> {'close enough' if ok else 'check your circuit'}")
```

## 6. Quiz (answers below, try first)
1. If voltage doubles and resistance stays the same, what happens to current?
2. If the switch is open, does current flow?
3. What is the unit of current?

<details><summary>Answers</summary>

1. It doubles. 2. No. 3. The ampere (amp).
</details>

## Check your work
- [ ] My table has three rows, and V ÷ R is close to the measured current each time.
- [ ] I saw current drop to 0 when the switch was open.
- [ ] I can say what voltage, current and resistance mean without notes.

## Next lesson
**Lesson 2 · Switches and semiconductors** (`lessons/hw-02`, merged from old lessons 1.2 and 1.3).

## Sources
- NIST, "Ampere: Introduction": https://www.nist.gov/si-redefinition/ampere
- Wikipedia, "Ohm's law": https://en.wikipedia.org/wiki/Ohm%27s_law
- PhET, Circuit Construction Kit: DC: https://phet.colorado.edu/en/simulations/circuit-construction-kit-dc

## Safety and scope
This lab is simulation only. Do not experiment with mains (wall socket) power. All data here is your own. Never commit passwords, keys or tokens.

## Licence
Code in this folder (for example `check_ohms.py`) is under the **MIT License**. Lesson text and diagrams are under **Creative Commons Attribution 4.0 International (CC BY 4.0)**. See `LICENSE` and `LICENSE-docs` at the repo root. PhET simulations belong to PhET Interactive Simulations, University of Colorado Boulder, and are linked, not copied.
