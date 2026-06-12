---
title: "Two Input Languages in GG, how to?"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by retrosteve on 2008-03-22
Adding input language switch
After adding "language support" for Swedish on ubuntu,nothing happened.  I still don't see any way to switch from english to swedish input.

So I ran around on the internet and found this known bug:

[https://bugs.launchpad.net/ubuntu/+s...rg/+bug/196277](https://bugs.launchpad.net/ubuntu/+s...rg/+bug/196277)

and tried changing the x config file as recommended, adding the last three lines to the keyboard config.

Then I restarted Ubuntu, and it didn't like it at all... First it complained that my GNU settings conflictedwith my new X settings (and I didn't know I had GNU settings for this, or how to find them)

Then I told it to use the X settings and it complained:

"Error activating XKB configuration. X server version data the X.org Foundation 10300000

If you report this situation as a bug, please include:
The result of xprop -root | grep XKB
The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd "x

So here they are:

home@steve-desktop:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "gb,sw", ",winkeys", "grp:ctrl_shift_toggle,grp_led:scroll"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "gb,se", ",", "grp:alts_toggle"
home@steve-desktop:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
layouts = []
model =
overrideSettings = true
options = []

Now oh great gurus, what shall I try?  I checked a couple of similar threads and found similar questions but must have missed the answer.

Thanks to anyone in advance... Steve

---

### Post by zvacet on 2008-03-22
**system>preferences<keyboard>second tab**(I don´t know how it i named in English,because I don´t use English version)>add  Swedish and make it default.After reboot you should have Swedish as default language.

---

### Post by retrosteve on 2008-03-22
Thanks, zvacet, but I've already done that, though I left English as default.

I now have two layouts.

My question is now how to switch back and forth.

---

### Post by zvacet on 2008-03-22
Right click on top panel>add to panel and you will find keyboard indicator (or something similar).Ad that applet to panel and from that you will be able to swich languages by selecting groups.

---

