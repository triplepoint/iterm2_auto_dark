# Intro
Lifted with thanks from:
https://gitlab.com/snippets/1840760

The idea here is to set up a watcher, which looks for the Iterm2 application's `Theme` setting to change, and to then update all the profiles currently open on a terminal to have appropriate color profiles.

You can then set Iterm2's `Theme` setting to follow MacOS's setting, and automatically swap dark/light at dawn and dusk.

# Setup
Configure Iterm2 to enable the Python API, and install the Python runtime.  I won't repeat the documentation here, but you can read about it in [the Iterm2 Python API documentation](https://iterm2.com/python-api/tutorial/index.html#tutorial-index).

Create a new Profile in Iterm2, with a name like `Something Useful (Auto)`.  This will be the profile you'll assign to any terminal you want to be tracked and modified by this utility script.  Look at the Iterm2 documentation for more information on how that's done.

Copy the `auto_dark_mode.py` script in this repository into `~/Library/ApplicationSupport/iTerm2/Scripts/AutoLaunch/auto_dark_mode.py`.  This will set up the script to auto run when Iterm2 starts.

Modify the copy you just made, and edit the `PROFILE_PRESETS` define.  This dict maps a Profile name to a pair of color preset names, one for the light mode and the other for the dark mode.  Add a new element to this dict, with the key being the name of the Profile you created above.  Be sure to set the color presets in the right order (light first), and pick the names from the set of color presets in the Profile's `Color Presets` drop down on the `Colors` tab.

You should be able to test this out by making sure a test console is using the new Profile, starting the new script from `Scripts` status bar drop down menu, and changing the Iterm2 application's `Theme` from dark to light and back.  The console should change its color presets, after a bit of delay (it takes a second).

The Iterm2 app should follow MacOS's overall theme setting, if you don't select the `light` or `dark` theme in Iterm2.  This OS theme can be set to toggle automatically at dawn and dusk.
