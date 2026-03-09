# Darkwar Zombie Auto-Bot

This is a Python-based automation script that uses `pyautogui` to automatically find and attack zombies in the game. 

## Features
- **Auto-Attack Routine**: Automatically searches for zombies on the map, clicks to rally/attack, and sends troops.
- **Energy Checking**: Monitors the energy bar to check if there is enough energy to launch an attack.
- **Auto-Recovery**: Recovers from stuck states by navigating back, opening the world map, or analyzing the screen to click on empty green ground.
- **Auto-Energy Replenishment**: Uses energy items when energy is low.

## Requirements

You need Python installed along with the following packages:

```bash
pip install pyautogui opencv-python Pillow
```
*(Note: OpenCV is usually required by PyAutoGUI for image recognition when using the `confidence` parameter).*

## Setup

The program relies on image recognition to know where to click. You must capture small screenshot snippets of the game's UI and save them in the same directory as the script. 

Required images:
- `profile_anchor.png` - Player's profile picture used as an anchor to calculate the energy bar location.
- `zoom.png` - The search/radar button to open the search menu.
- `join.png` - The active zombie/rally tab.
- `joininactive.png` - The inactive zombie/rally tab.
- `find.png` - The search confirmation button.
- `rally.png` - The rally or attack button that appears on the zombie.
- `start-rally.png` - The button to confirm troop deployment.
- `cancle.png` - A cancel button used to detect if the target is already engaged.
- `back.png` - The back button to exit menus.
- `world.png` - The button to switch to the world map.
- `add-energy.png` - The button to prompt adding energy.
- `energy20.png` - The button to consume a 20-energy item.

*(Note: The script also uses OpenCV color detection to find and click empty green ground to clear pop-ups, so `empty_ground.png` is no longer used for image recognition.)*

## How to Run

1. Open your terminal or command prompt.
2. Navigate to the folder containing the script.
3. Run the script:
   ```bash
   python darkwar-zombie.py
   ```
4. **Important**: You have exactly **5 seconds** after starting the script to bring your game window to the foreground. The script will take control of your mouse after the countdown.

## Troubleshooting

- **Script not clicking anything**: Ensure the game window is fully visible and not covered by other windows. Try retaking the screenshot snippets (`.png` files) so they accurately match how they look on your current screen resolution.
- **ImageNotFoundException**: Make sure all the `.png` files are named correctly and located in the same folder as the Python script.
- **Tuning**: You might need to adjust the `confidence` values in the `find_and_click` calls (e.g., `0.8` or `0.75`) to make the image recognition more or less strict depending on your screen settings.

## Disclaimer
Use this script at your own risk. Automating gameplay may be against the Terms of Service of the game and could result in account bans.
