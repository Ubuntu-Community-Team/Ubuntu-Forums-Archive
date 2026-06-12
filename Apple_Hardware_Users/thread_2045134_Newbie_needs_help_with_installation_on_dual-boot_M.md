---
title: "Newbie needs help with installation on dual-boot Mac  - fails at boot"
date: 2012-08-20
forum: Apple Hardware Users
---

### Post by gmusser on 2012-08-20
I'm trying to install 12.04 onto a MacBook as a dual-boot system (with Lion) and have followed the instructions at [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation).  Adjusting for the newer installer, everything goes as instructed, but the system freezes on booting into Ubuntu, giving either a gray penguin screen or a text error.

This problem has been reported by other people and the usual advice is to reinstall grub, but there are lot of differing instructions for how to do so floating around on this board and others. Many simply do not work at all (e.g. running 'grub' with a 'find' command) and are presumably out of date.  Others apply to a single-boot system where the bootloader goes in the MBR, rather than a dual-boot system where I want to install it to the Linux partition.  'grub-install /dev/sda5' gives an error message that the /dev should be mounted, even though the /dev *is* mounted.

---

### Post by jackdaniels123123 on 2012-08-21
I am also having this problem. Im dual booting  on a macbook pro and decided to upgrade to mountain lion. After the upgrade I tried booting into 12.04 and I get a message telling me filesystem is unknown and grub rescue. Through searching I found out it was an issue with grub but I have not found a working solution either to repair on dual boot mac.

---

### Post by miguelbaines on 2012-08-22
Well, i just reinstalled on my ppc and am still having the same problem. I can get to the dual boot screen to select the mac os x or linux (ubuntu) harddrive icons, when I select ubuntu, it takes me to the first stage boot screen where I enter the letter 'L' to select linux and it kicks me back out to the dual boot screen... 

Help me please.

thx.

---

### Post by rsavage on 2012-08-23
@miguelbaines Start a new thread and I will help you.  List any unusual hardware you have - a disk drive controller card, a v large hard drive, an external hard drive etc

Also, what in the PowerPC FAQ have you tried?  And what have you tried from a random search (which will be wrong) - have you also done this with your re-installation?

---

### Post by gmusser on 2012-08-23
I'm delighted that @miguelbaines is getting help.

As for me, I have given up on Ubuntu and removed it from my machine.  Every couple of years for the past decade or so, I have decided to give Linux another go, put in an inordinate amount of time making sense of inconsistent documentation, and failed in the installation or configuration. This time, I was so close, yet so far away.  GRUB was the only thing stopping me. I hope that, the next time I try in two years or so, GRUB will finally be fixed.

---

### Post by miguelbaines on 2012-08-23
@gmusser I know how you feel, this is my second attempt at Ubuntu on this mac in the last two years. I too gave up. This time around, I'm sooooooo close to getting this thing booted up...

---

