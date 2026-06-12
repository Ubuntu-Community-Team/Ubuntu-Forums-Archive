---
title: "Is there a way to CYCLE through workspaces in GNOME?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Taxi on 2007-12-11
Does anyone know how to set up a keyboard shortcut in Ubuntu (Gutsy) that will *cycle* through the workspaces the way Alt-Tab cycles through windows (ie when it reaches the end will go back to the beginning)?  Ever since I installed Ubuntu I've been wishing it could do this, but I've only been able to find out how to make it go in a single direction, without the looping I want.  On a side note, I'd also like to make Super+Tab the shortcut for this, but the "Keyboard Shortcuts" window in Ubuntu won't wait for the second key, it just makes Super the keystroke.  I did figure out how to change it with gconf-editor, though, at least in Feisty.

I recently tried the Live CD of Xubuntu Gutsy and was able to do it by combining a keyboard shortcut for "Next Workspace" in the "Window Manager Settings" with the "Wrap workspaces when the first or last workspace is reached" setting in "Window Manager Tweaks".  It didn't mind the Super+Tab combo, either.  I'm really considering switching to Xfce just for this - well, the speed has something to do with it also - but would really appreciate if someone can tell me how to make it happen in GNOME.  Oh yeah, and I have desktop effects disabled, if that makes the slightest bit of difference.

---

### Post by SupaSonic on 2007-12-11
Doesn't Ctrl+Alt+arrow keys do that? If you have desktop effects on 'High' in Gutsy that will definitely work

---

### Post by jamescondron on 2007-12-11
Yes, ctrl+alt+arrow should, else ctrl+alt+mouse in compiz-fusion etc.

---

### Post by Rhubarb on 2007-12-11
Ctrl + Alt + left or right arrow cursor key does change desktops in Ubuntu whether desktop effects are turned on or not.

---

### Post by discoade on 2007-12-11
mouse center button drag left or right, mouse scroll wheel on desktop with qube,  the possibilities are endless!

---

### Post by eldragon on 2007-12-11
ive asigned the following keyboard shortcuts, they are extremely useful

alt-1 = workspace 1
alt-2 = workspace 2
alt-3 = workspace 3
alt-4 = workspace 4

and of course
ctlr-alt-1 = move window to workspace 1
ctlr-alt-2 = move window to workspace 2
ctlr-alt-3 = move window to workspace 3
ctlr-alt-4 = move window to workspace 4


they dont seem to work with compiz, too bad..

---

### Post by Taxi on 2007-12-11
I appreciate the help, but I'm already aware of those shortcuts.  The thing I'm looking for is a way to *cycle* through them.  The difference is that I don't want it to reach an end and stop.  If I have four workspaces and keep hitting the shortcut, I would like it to go from 1 -> 2 -> 3 -> 4 -> 1 -> 2 -> 3 -> 4 -> 1 -> 2 -> 3, etc.  Just like how if you hit Alt+Tab it will cycle through all your windows and go back to the first if you go all the way around instead of stopping at the last one.  This is doable in Xubuntu via the method I posted above.  I feel like it's gotta be possible in GNOME, too; does anyone know how to do it?

---

### Post by drs305 on 2007-12-11
> **Taxi said:**
> I appreciate the help, but I'm already aware of those shortcuts.  The thing I'm looking for is a way to *cycle* through them.  The difference is that I don't want it to reach an end and stop.  If I have four workspaces and keep hitting the shortcut, I would like it to go from 1 -> 2 -> 3 -> 4 -> 1 -> 2 -> 3 -> 4 -> 1 -> 2 -> 3, etc.  Just like how if you hit Alt+Tab it will cycle through all your windows and go back to the first if you go all the way around instead of stopping at the last one.  This is doable in Xubuntu via the method I posted above.  I feel like it's gotta be possible in GNOME, too; does anyone know how to do it?

CTRL-ALT- Left/Right does just what you are describing on my Gutsy 64-bit. After 4 it goes back to 1 - it doesn't dead end. Or do I misunderstand what you want?

---

### Post by PhoenixP3K on 2007-12-11
I'm using three workspaces, but when I am using the cube effect it allows me to cycle through. However, when going from 3 to 1 with the shortcuts it's flips back to 2 and quickly up to space 1.

---

### Post by Taxi on 2007-12-11
> **drs305 said:**
> CTRL-ALT- Left/Right does just what you are describing on my Gutsy 64-bit. After 4 it goes back to 1 - it doesn't dead end. Or do I misunderstand what you want?
Nope, that's exactly what I'm looking for, but mine dead ends.  From the last two posts it sounds like it works that way with desktop effects enabled, so maybe that's where the confusion is coming from - am I right in thinking yours are enabled?  Mine are disabled; does anyone know if it's possible to make it work this way without enabling Compiz?

---

### Post by drs305 on 2007-12-11
I have desktop cube and rotate cube enabled. I do have compiz-gnome installed.

---

### Post by Taxi on 2007-12-13
I spent some time in the GNOME IRC channel today. They said they made the conscious policy decision not to include a shortcut or option for that (I guess not enough people want it), but they still came up with a solution for me. It's a little hacky, but it gets the job done.

First of all, you have to have the wmctrl package installed, at least for this solution. Create the following script, and make it executable:
#!/bin/sh
num=$(wmctrl -d | wc -l)
wmctrl -s $(wmctrl -d | awk '/[0-9]+ +\*/ {print ($1+1)%'$num' }')

(I put mine at ~/.metacity/cycle_workspaces)
Open gconf-editor. Browse to /apps/metacity/global_keybindings. Set run_command_1 to the key combination you want to bind it to. (The other shortcuts there should give you an idea of the syntax.) Then browse to /apps/metacity/keybinding_commands and set command_1 to /full/path/to/script, which in my case was /home/*user*/.metacity/cycle_workspaces.

And there you have it!

Once they had come up with the solution for me, I only had a couple minor hang-ups. First, I accidently set the keybinding with angle brackets around the "Tab" because a lot of keys require them. Tab, however, does not, so if you have problems try to verify the syntax for each key. Second, they had assumed I had wmctrl installed already, which I didn't, but the error messages when I tried to run the script directly from a terminal made the problem pretty clear; make sure you install the package first.

---

