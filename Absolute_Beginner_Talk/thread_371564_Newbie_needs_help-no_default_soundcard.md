---
title: "Newbie needs help-no default soundcard"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by chemtut on 2007-02-27
I have installed dapper on a Compaq Armada 1750 laptop which has soundblaster16/pro soundcard, but i have no sound!
Preferences>sounds>shows no default sound card
Rhythmbox>cannot establish connection to sound server
speaker icon>no volume control Gstreamer plugins and/or devices

the card worked with XP Pro which i have overwritten
i would appreciate any advice and thanks in advance

---

### Post by fdrake on 2007-02-27
start the terminal and type this:
alsamixer
now use the arrows up-down to set the volume and right-left to change the device.

---

### Post by Kateikyoushi on 2007-02-27
This guide is very useful for locating the source of the problem and installing the driver. [LINK]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

---

### Post by chemtut on 2007-02-27
thanks for your help will try when i return from work!

---

### Post by chemtut on 2007-02-27
sadly no luck!
alsamixer >function_snd_ctl_open failed for default :No such device

---

