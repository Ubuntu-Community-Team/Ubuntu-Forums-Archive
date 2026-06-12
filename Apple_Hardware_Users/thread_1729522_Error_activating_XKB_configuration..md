---
title: "Error activating XKB configuration."
date: 2011-04-15
forum: Apple Hardware Users
---

### Post by bleu_canary on 2011-04-15
I am obviously a total newb to all of this and rather than just reinstalling the newly installed Ubuntu 10.10 on my MacBook Pro 13" (5,5), I want to use this opportunity to learn exactly what I'm doing here. 

I recently was trying to go about changing the control key function to the command key so that I could be more comfortable as an Apple user. When I thought I had finished the needed changes there was this error dialog box that said: 

Error activating XKB configuration.
It can happen under various circumstances:
 • a bug in libxklavier library
 • a bug in X server (xkbcomp, xmodmap utilities)
 • X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10900000

If you report this situation as a bug, please include:
 • The result of xprop -root | grep XKB
 • The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


Now my keyboard doesn't work unless I change the keyboard model after having logged using the on screen keyboard. I have noticed that if I try to  input any information in the log in menu with the physical keyboard, all the keys turn straight into question marks. I'm a little frustrated here because a lot of the help that I find is still above my head when it comes to troubleshooting some issues with Ubuntu. I know I'm a total newb but don't want to stay that way.

---

### Post by samhdaniel on 2011-05-02
I'm having the same problem with 11.04 (Natty), but I'm using a Mac aluminum keyboard on a regular Intel-based PC. I did **not** have this problem with 10.10.

X.org version is 11001000.

xprop output:

_XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "pc105", "us", "mac", ""
_XKB_RULES_NAMES(STRING) = "evdev", "pc105", "us", "mac", ""

gconftool-2 output:

 model = applealu_iso
 options = [terminate	terminate:ctrl_alt_bksp,lv3	lv3:ralt_switch]
 layouts = []

---

### Post by lincolnlad on 2011-05-06
I'm also having this problem since the Natty upgrade with an aluminium keyboard. I filed a bug report [here]("https://bugs.launchpad.net/ubuntu/maverick/+source/xkeyboard-config/+bug/696232"), but nothing has come of it. It's a nuisance. I've also lost the ability to press right-alt and 3 to get the # key on my GB keyboard. I seem to be able to get SHIFT-3 to provide # or £ but I can't have both.

---

### Post by ripounet on 2011-05-18
Exact same problem as samhdaniel, and i'm sooo sad.

 xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "pc105", "fr", "oss", ""
_XKB_RULES_NAMES(STRING) = "evdev", "applealu_jis", "fr", "oss", ""

gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 model = applealu_jis
 layouts = [fr	mac,fr	oss]
 options = [caps	caps:none,altwin	altwin:swap_lalt_lwin,compat	apple:alupckeys,grp	grp:alts_toggle]

---

### Post by ripounet on 2011-05-18
Found [>here<]("https://bugs.launchpad.net/ubuntu/+source/x11-xkb-utils/+bug/742380") a solution that worked for me :

Change the keyboard model from "Apple Aluminium Keyboard" to "Apple" in the Keyboard Preferences solved this error.

---

### Post by chrismacp on 2011-06-16
Thanks ripounet!! 

So simple but this was really annoying me, have had the same problem since the upgrade too but this works well. I have a British aluminium keyboard and all my keys are working correctly, even the # (right-alt + 3)

Excellent :) 

> **ripounet said:**
> Found [>here<]("https://bugs.launchpad.net/ubuntu/+source/x11-xkb-utils/+bug/742380") a solution that worked for me :

Change the keyboard model from "Apple Aluminium Keyboard" to "Apple" in the Keyboard Preferences solved this error.

---

