---
title: "no boot menu"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by dimitars on 2007-07-26
i formated my windows, and  now there is no grub booter, just windows is booted autoamicaly. What should i do???

---

### Post by Cypher on 2007-07-26
If you formatted windows, it shouldn't be booting Windows. How did you format it?

---

### Post by cek on 2007-07-26
If you install windows AFTER linux, the Windows bootloader will overwrite the MBR (overwrite grub or lilo).  That is why most suggestions for dual boot suggest to install Windows first.

Boot from your ubuntu CD and go into rescue mode.  There should be an option to reinstall the bootloader (reinstall GRUB).

---

### Post by dimitars on 2007-07-26
i put windows cd in cd rom. then i restart my pc. then a menu iss showed(blue screen). I formated the partition where windows was instaled. Then i instaled windows on the same partition. I think linux is on other hdd. no grub menu is showed. JUST LIKE I have no ubuntu

---

### Post by Cypher on 2007-07-26
OK..you didn't say that you re-installed Windows. That's a key piece, like **cek** said, Windows overwrote the GRUB bootloader.

Lemme find the link to the instructions for GRUB recovery, but hopefully someone else will provide the link before long..

Found it: Check out [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/).

---

### Post by MQMike on 2007-07-26
This basic How-To deals with exactly your situation:

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

### Post by ajgreeny on 2007-07-26
Rather than use supergrub, it's much easier to do the following:-


Boot into the ubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

I've done this a few times myself so I know it works a dream.  Good luck.

---

### Post by dimitars on 2007-07-27
it seems that linux partition is gone. I tried with 2 bootloaders(one is grub) but my pc displayed error.

REINSTAL WILL FIX THE PROBLEM.

---

### Post by MQMike on 2007-07-27
ajgreeny’s post and my how-to (see above) both exactly do that – re-install GRUB.

---

