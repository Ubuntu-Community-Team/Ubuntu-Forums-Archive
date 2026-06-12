---
title: "disablling left tap click only"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by chris200x9 on 2008-01-23
Hi I'm on a macbook so I only have 1 button on my trackpad but I hate tap click and need right click is there anyway to turn off the tap click for the left click ONLY

---

### Post by willmcgree on 2008-02-24
Hey. I had the same problem, but it has since been solved.

I currently have this set-up:

- Press the trackpad button to left-click
- Tap the trackpad surface with two fingers to middle-click
- Tap the trackpad surface with three fingers to right-click

The last two could be swapped (I remember the old hold-two-fingers-and-click thing for Ctrl-click under Tiger) if you want.

Open a terminal through Applications - Accessories - Terminal (then remember to breathe; it's not scary) and type the following to make a backup of the file involved in case it all goes wrong. (If I were you, I'd read this whole post and take notes, or, you know, print it, just in case)

```
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.safe
```

You'll be asked for your password. Enter that and you'll have made a copy of "xorg.conf" with ".safe" on the end so we know which is which. You don't actually enter the "$" (just in case you didn't know). That just tells you that the terminal is ready to accept commands. (Sorry if you knew that - I can never gauge how experienced people are.)

Next, we need to edit that file.

```
$ sudo gedit /etc/X11/xorg.conf
```

Find the section that begins:

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
...
... (not actually "..." but a list of Options)
...
EndSection
```

and replace it with the following block. Make sure you replace everything from Section "InputDevice" right down to "EndSection" with all of the following block.

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "on"
	Option          "TapButton1"            "0"
        Option          "TapButton2"            "2"
        Option          "TapButton3"            "3"
        Option          "VertEdgeScroll"   "1"
        Option          "HorizEdgeScroll"  "1"
EndSection
```

The bits we're interested in are the "TapButton1", "TapButton2" and "TapButton3" options. The numbers 0, 2 and 3 show how many fingers are required for that action. 0 means that it's disabled.

If you wanted two fingers for right-click and three for middle-click, swap the 2 and 3. If not, that'll all work. Also, the right edge of the trackpad will scroll up and down and the bottom edge left and right. Curiously, and I don't know why this happens, when I touch the bottom-right corner of my trackpad, that's the same as right-clicking. Ah well...

Save the file and close gedit. Now make sure you have no unsaved work and press Ctrl-Alt-Backspace to restart your session using the new file. You'll need to login again.

If, for whatever reason, that breaks your trackpad (not physically), do the following:

Boot up.
Open a terminal (press Alt-F1 to get to the menu and use the arrow keys and Enter)
Type:
```
sudo mv /etc/X11/xorg.conf.safe /etc/X11/xorg.conf
```
That replaces the "experimental" version with the known-to-be-safe backup.
Type your password and press Enter. Wait until the prompt appears again (should be instant).
Restart the graphical server (and in doing so, change which configuration file your computer uses) by pressing Ctrl-Alt-Backspace or by restarting your machine.

Hope that helps. Any questions, please ask.
Will

---

