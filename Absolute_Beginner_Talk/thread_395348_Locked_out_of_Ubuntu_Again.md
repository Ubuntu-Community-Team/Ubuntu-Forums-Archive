---
title: "Locked out of Ubuntu Again"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-28
Every time that I install the following, my program will not reboot. It shows it starting, but then hangs up with a video resolution error. It did not do this on the first few installs. Nothing has been changed on my system. I am installing Ubuntu with only one hdd attached to computer.

I have uncommented all the debs in menu.lst before I do the following.

Here are the commands that I am entering: Like I say, they used to work. 

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
**?**
sudo shutdown -r now

Is there a way to fix this without reinstalling even though I can't get into Ubuntu?
kh

Edit: I was leaving out this line: [B]sudo aticonfig --overlay-type=Xv where you see the "?" above.
[/B]Right now it seems to be working. So, I'm checking this resolved.

---

### Post by mahy on 2007-03-28
Judging by this (the howto i followed) [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI), there should be something like sudo aticonfig --overlay-type=Xv and

Section "Extensions"
        Option      "Composite" "0"
EndSection

Anyway, try booting to the recovery mode and check the xorg.conf

---

### Post by kittyhawk63 on 2007-03-28
> **mahy said:**
> Judging by this (the howto i followed) [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI), there should be something like sudo aticonfig --overlay-type=Xv and

Section "Extensions"
        Option      "Composite" "0"
EndSection


Anyway, try booting to the recovery mode and check the xorg.conf


The line you gave is on the page, but that didn't make any difference when I entered it.
I can't see any GRUB when rebooting.
Edit: Yes I can see the grub. I'll be back.

---

### Post by david_kt on 2007-03-28
I guess you have an ATI video card but there is no direct rendering although the driver is install. 
I have tried to use envy, and many other method. All did not work, except the following:

Go back to default ubuntu driver for ATI:

[INDENT]

sudo dpkg-reconfigure xserver-xorg[/INDENT]

Choose defaultdepth 16 (instead of 24).

After that, follow below instruction, the one written by kultuur.

[http://www.ubuntuforums.org/showthread.php?t=7200&page=2](http://www.ubuntuforums.org/showthread.php?t=7200&page=2)

DK

---

### Post by kittyhawk63 on 2007-03-28
> **david_kt said:**
> I guess you have an ATI video card but there is no direct rendering although the driver is install. 
I have tried to use envy, and many other method. All did not work, except the following:

Go back to default ubuntu driver for ATI:
[INDENT]

sudo dpkg-reconfigure xserver-xorg[/INDENT]Choose defaultdepth 16 (instead of 24).

After that, follow below instruction, the one written by kultuur.

[http://www.ubuntuforums.org/showthread.php?t=7200&page=2](http://www.ubuntuforums.org/showthread.php?t=7200&page=2)

DK

I'm making note of this and printing it out. Thank you. I got it working this morning. If it fouls up again, I will try out your suggestion.
kh

---

