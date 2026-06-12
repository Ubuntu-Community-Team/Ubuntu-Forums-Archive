---
title: "Keyboard shortcut shows volume increasing--but no change in volume"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by wilberfan on 2006-12-10
I set up a keyboard shortcut to increase and decrease volume (Ctrl-up, Ctrl-down).   When I use the shortcut, I get an icon in the center of the screen showing the volume increasing and decreasing--but the volume doesn't change?   The shortcut seems to be adjusting something that's not linked to my actual volume slider...

What do I need to change?  :???:

---

### Post by Zzl1xndd on 2006-12-17
Im having the same problem have yet to figure it out

---

### Post by runris on 2007-12-25
having the same problem. my Fn-keys for volume are suddenly controlling the CD-volume. kinda happened for no reason. 
Thought I'd bring up this tread again to see if anyone here got some new ideas?

---

### Post by LinuxIsInnovation on 2007-12-25
Try changing the controller device: 
Double click on the volume icon in the notification area
Goto File->Change Device
Change to the other available alternatives.

---

### Post by runris on 2007-12-25
tried it. that only changes what the slider on the panel controls. not what my shortcut-keys on the keyboard controls :\

---

### Post by LinuxIsInnovation on 2007-12-25
Check for the default values in the keyboard shortcuts:
Volume up: 0xb0
Volume down: 0xae
Volume mute: 0xa0

---

### Post by runris on 2007-12-25
> **sayakb said:**
> Check for the default values in the keyboard shortcuts:
Volume up: 0xb0
Volume down: 0xae
Volume mute: 0xa0

there's a point.. they have been modified, and now I can't get them restored. I can only type in a new shortcut like Ctrl+Alt+whatever... not type in "0xb0". you don't happend to know this as well? :)

---

### Post by zeddock on 2008-02-07
Where can I find the config file for these settings?

zeddock

---

### Post by zeddock on 2008-02-07
> **runris said:**
> there's a point.. they have been modified, and now I can't get them restored. I can only type in a new shortcut like Ctrl+Alt+whatever... not type in "0xb0". you don't happend to know this as well? :)

This post fixed it for me...
> My shortcut keys worked fine for next/back, volume up/down and mute. I do NOT have a fancy multimedia keyboard - just a regular one.

I ran a system update a few days ago around the 10th of January, 2008????

Now today I'm playing music in Rhythmbox and next back shortcuts work, but not volume or mute - strange...

I can see the volume control go up and down in the middle of my screen when I press the keys - so the actual key mapping appears to work - but still no volume change.

So I found this posting and simply went into the sound preferences link (ubuntu Gutsy), clicked test on a few items, exited, and voila - it works now - volume, mute, etc. work like a charm again.

Very strange but I hope this helps somebody.



Makes no sense but it fixed it.

zeddock

---

### Post by emakarov on 2008-02-08
> So I found this posting and simply went into the sound preferences link (ubuntu Gutsy), clicked test on a few items, exited, and voila - it works now - volume, mute, etc. work like a charm again.Well, of course! I also was puzzled by this issue. In the System | Preferences | Sound, under Default Mixer Tracks, one has to select Master. It says explicitly: Select the device and tracks to control with the keyboard.

---

