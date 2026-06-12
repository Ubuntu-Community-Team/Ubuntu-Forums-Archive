---
title: "Failed to start the xServer - black screen"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by bwallum on 2007-03-23
Hello

I changed my monitor, 640x480 res on start up. Reconfigured xserver. Monitor and res fine, keyboard numlock failed. Ran lots of code snippets as suggestions for fix, they didn't. Ran reconfig xserver again, tried vga as set up and now get the message 'Failed to start the Xserver'. The screen is black. I can type into it. The keyboard is now fine (numlock works)

I'm typing this from my XP machine (yes I know I'm regressing but when I get into a car I want to drive it, not dismantle it and try this component with that component just to see what happens - if you get my drift)

Can you help me get Ubuntu running again please?

My graphic chip is on board Intel 82845G/GL/GE/PE/GV

Rgds
Bob

---

### Post by Blutack on 2007-03-23
Start in recovery mode
dpkg-reconfigure xserver-xorg
Pick vesa as the graphics driver.
Run through all the options, make sure they are correct.
Reboot and pray!

---

### Post by bwallum on 2007-03-23
It must be in the 'make sure they are correct' interpretation. The screen stays black and empty after rebooting following reconfigure.

I only changed my Monitor!

I have researched the specs for it, entered them in 'reconfig' and ....black screen. It did work before perfectly well. Nothing further added since.

Anything else to try before I reformat the hard drive?

Rgds
Bob

---

### Post by bwallum on 2007-03-23
Nil desperandum....

Manged to get Ubuntu up with trial and error in 'config'. The key seemed to be when choosing the options for monitor display modes to go for 'simple' choice. I am now back to where i was this morning with the following error message appearing on the desk top following a boot:-

BEGINNING OF ERROR MESSAGE
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70101000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
END OF ERROR MESSAGE

xprop -root | grep XKB result:-

_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc104", "uk", "", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "uk", "", "lv3:ralt_switch"

gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd result:-

layouts = []
model = compaqeak8
options = []
overrideSettings = true

Where to now?

Regards
Bob

---

### Post by AndyCooll on 2007-03-23
Rather than trial and error, try just accepting the defaults except for the graphics card where you should choose "vesa". For monitor settings choose "Generic Monitor".

:cool:

---

### Post by bwallum on 2007-03-23
Ok, done the 'just accept the defaults bit' and absolutely no change. Still get 'Error activating XKB configuration...' at boot just after desktop loaded.

Ubuntu is a good techies Sudoku but no good to use in production. The simplest things just lead to a spiral of malfunction. Change a monitor and everything goes pear shaped!

How can I check the xserver configuration files and preferably remove them and start afresh? (My cursor has developed a little dot at the bottom now..)

Thanks for the responses by the way, I am trying but this OS will never fly if it can't be set up easy for newbies. Four weeks and no faith at all in that it will ever be useful for work.

Graphics have now ground down to a series of stills for the screen saver. Something very wrong here.

Whats next? 

Kind Regards
Bob

---

### Post by bwallum on 2007-03-24
This could be my real problem:-

> The current X.Org configuration mechanism is not good. It was heavily derived from Debian's XFree86 configuration, which has very little autoconfiguration infrastructure and has since had full autoconfiguration totally bolted on to it. It requires many hacks and special cases, and barely hangs together. It is exceptionally fragile, and often breaks unexpectedly.

Thats from the Wiki and a Matt Zimmerman who appears to be vastly more knowledgeable than I.

So, to move forward. I have found the x11 config file(s) I have loads because every time I reconfigure The system saves the duff configuration that I am moving from. Very helpful that, in case I want to screw up the system again in future I guess.

I have tried to delete the surplus (and a custom version) so that I have only one xserver configuration file. I have tried the gui approach and cannot delete the files it seems.

I have tried the terminal with 'cd etc' to try to get to the files using the terminal but no luck.

Can you help me delete the unwanted configuration files please. thay are lying in etc/x11/ and called xorg.conf and loads of xorg.conf(with lots of numbers) and xorg.conf.custom.

How do I delete all the files bar xorg.conf please?

Does xserver choose xorg.conf.custom in preference over xorg.conf? If so it may explain why all the changes suggested have not worked because they would have gone into xorg.conf and good 'ol xserver continually loads xorg.conf.custom??

AGGGGGGHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHH!!!!!!

Thats better, I'm ready to continue now..

---

### Post by AndyCooll on 2007-03-24
To remove old files the action is:
```
sudo rm /etc/X11/file_to_remove
```

And no xserver doesn't look to the custom one AFAIK. The active one is xorg.conf. The others are just sitting there as backup.

You can manually edit xorg.conf:
```
sudo vi /etc/X11/xorg.conf
```
Replace vi with nano or pico if you prefer these.

:cool:

---

