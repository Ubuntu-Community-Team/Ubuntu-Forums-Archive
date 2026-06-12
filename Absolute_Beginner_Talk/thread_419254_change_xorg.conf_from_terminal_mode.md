---
title: "change xorg.conf from terminal mode"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by mills on 2007-04-22
messing about with mouse settings and i messed up a little and now none of my mouse buttons work at all (iam in windows at the moment) 

how can i change xorg.conf from terminal mode?

---

### Post by Seisen on 2007-04-22
You can do two things.

```
sudo dpkg-reconfigure xserver.org 
``` or

```
sudo vim /etc/X11/xorg.conf
```

The first one is easier to use because it ask you question and then rewrites your xorg.conf file. I recommend that one.

---

### Post by mills on 2007-04-22
cheers seisen

apreciate it

---

### Post by mabelrxu on 2007-04-22
ooo ... i feel your pain ... first of all, here's some keyboard shortcuts to help you survive for a while ...

either ctrl + F1 gives you the applications menu ... that'll help a lot!
use tabs to move to the next field, and ctrl + tab to move back a field

here's how to do it from terminal:

ctrl + alt + F1 or F2 or F3 or F4 or F5 or F6 to switch to terminal
if you have internet, then sudo apt-get install nano (nano has all it's commands on the bottom of the screen, so no learning required)
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup (it may be broken, but at least doesn't crash ur comp)
now, you can either manually edit ... sudo nano /etc/X11/xorg.conf, or regenerate it ... sudo dpkg-reconfigure xserver-xorg-input-all (for some reason, this regenerating thing, even when you do dpkg-reconfigure xserver-xorg-all, manages to keep your edits and customizations, althought it may not preserve it all, so you should still use cp to make a backup)

use tab complete to help you "remember" everything (you type the first few letters, then press tab, if it doesn't automatically come up, then press it again, and it'll display a list of auto-complete options)

also, you can sudo apt-get install links2 or sudo apt-get install links to get a text-based web browser for googling any further problems (hit esc for the menu / main toolbar in links)

hope that helps!

---

### Post by mills on 2007-04-22
nice tips mabelrxu, i'll need em

but for the meantime what do i do if "sudo dpkg-reconfigure xserver.org"
says that xserver.org isnt installed?

i tried sudo apt-get install xserver.org just in case but nothing

and that vim code in p1 returned a blank screen, i think it was expecting me to write it from scratch

EDIT: should i try sudo apt-get install xserver ?

---

### Post by Seisen on 2007-04-22
Do this to install it

```
sudo aptitude x-window-system-core
```

or apt-get whichever one you prefer.

---

### Post by mills on 2007-04-22
installed the x-window-system-core

then tried sudo dpkg-reconfigure xserver.org again but its tellin me 
package 'xserver.org' is not installed and no info available

repeated the process but same story, should i be getting worried?

---

### Post by mills on 2007-04-22
burrrppp

---

### Post by pppetter on 2007-04-22
don't worry, Seisen just made a typo.
it should be > sudo dpkg-reconfigure xserver-xorg

and not
> sudo dpkg-reconfigure xserver.org

And just as mabelrxu said, next time - do a backup with the "cp" (cp=copy) command before you start.

---

### Post by mills on 2007-04-22
arggghhhhhh i just reinstalled lol

nevamind :lolflag:

so glad  i got a home partition

---

### Post by kerry_s on 2007-04-22
run this to rebuild xorg.conf-> sudo dpkg-reconfigure -phigh xserver-xorg

Key board mouse control is shift+alt+num lock

use the numbers for direction, 5 is the clicker, / is to set it to left click, * sets it for middle click, - sets it for right click, + is double click, 0 is lock drag, . release lock drag.

---

### Post by mabelrxu on 2007-04-22
yay for home partitions!

oops, they're right, it is dpkg-reconfigure **-phigh** xserver-xorg-whatever
oh yeah, you can use tab complete to help find out what "whatever" is supposed to be ... just hit tab once, and if nothing comes up (aka more than one possible auto-complete available), just hit tab again (so it's kinda like a double tab) and it'll give you a list of possible auto-completes ... :)

---

