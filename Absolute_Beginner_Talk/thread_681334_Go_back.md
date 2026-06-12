---
title: "Go back"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by h5290 on 2008-01-28
I installed Ubuntu, but could not get it to work with my internal modem.  I've decided to reinstall Windows XP, but the computer keeps telling me that there is no program to read the installation disk.  How can I get Windows back on my computer and get rid of Ubuntu?

---

### Post by overdrank on 2008-01-28
> **h5290 said:**
> I installed Ubuntu, but could not get it to work with my internal modem.  I've decided to reinstall Windows XP, but the computer keeps telling me that there is no program to read the installation disk.  How can I get Windows back on my computer and get rid of Ubuntu?

HI and I do not understand. When you boot to the win cd you are not able to install windows?

---

### Post by h5290 on 2008-01-28
When I put the Windows Installation CD in the CD Drive and try to open/run it, a msg pops up that says there is no program installed to read the CD.  Just so you will know, it does read most other CDs.

---

### Post by nat6138 on 2008-01-28
Something could possibly be wrong with the XP disc.

---

### Post by crjackson on 2008-01-28
Okay, lets make sure of some basic stuff...

1) Your BIOS is set to BOOT from CD
2) You are attempting to cold boot from a Windows CD, and the message is comming from there or BIOS
3) The CD you are trying to boot is an original MS CD and not a copy

---

### Post by overdrank on 2008-01-28
> **crjackson said:**
> Okay, lets make sure of some basic stuff...

1) Your BIOS is set to BOOT from CD
2) You are attempting to cold boot from a Windows CD, and the message is comming from there or BIOS
3) The CD you are trying to boot is an original MS CD and not a copy

Agreed, It sounds like the OP is opening the cd in Ubuntu.

---

### Post by broekskw on 2008-01-28
h5290 what version of windows 98? xp? visa?
anyhow most the time if you want to reinstall window over ubuntu  you would do a reboot with the windows cd in the cd rom and then go into your bios setup and select boot from cd rom first, then save and exit
then reboot with cd in your cd drive and follow the directions from the cd

now if this dose not work (because grub is present on your hard drive and you get an grub loading please wait, error code21) you will have to try to run the win cd and select r for repair, i had kind of the same problem and followed the advise of Rocket2DMn and finally got my hd back with a fresh win xp installed
 
[http://ubuntuforums.org/showthread.php?t=681189&goto=newpost](http://ubuntuforums.org/showthread.php?t=681189&goto=newpost)

---

### Post by h5290 on 2008-01-29
I am a TRUE BEGINNER, so you may have to explain a couple things to me.  I don't have a clue what a BIOS is.  All I know, is when I try to boot the original XP CD, I get the error msg.  I can open the CD once it is in the drive, but when I try to run any of the files, I get the error msg.  

By the way, thanks for all the quick responses!

---

### Post by h5290 on 2008-01-29
I printed this one out so I can try it when I get back on my computer.  I appreciate your attempt to help.

---

### Post by broekskw on 2008-01-29
h5290 if you are running win xp put in your cd into the cd drive and reboot,when your bootup screen comes up (the screen that shows all your hardware memory, drives, etc) please press you  DEL  key on your keyboard, this should bring up your bios screen, from this screen you will use the arrow keys on your key board to select one of the menus.just arrow down to one and hit the enter key, your are looking for the one (menu) that shows how your system first looks at to boot up,its set to hd 0 you have to change that the cdrom to boot from first, once done you have to arrow over to save and exit, hit enter and select Y for yes to save, then you should be able to run your win xp cd installer

if you keep getting error21 follow the instructions in the post that i did and you should be good to go, it did take me some time to get my hard drive back, you have to get rid of the grub boot from the h/drive before you can reload win xp

hope you can make some sense out of this, good luck:guitar:

---

### Post by broekskw on 2008-01-29
did a google on win xp repair and came up with this, so take a look should help

[http://www.techspot.com/vb/topic8356.html](http://www.techspot.com/vb/topic8356.html)


good luck:popcorn:

look under this section to set your boot up to cdrom

CDROM NOT BOOTABLE: If the XP/2000 CD does not boot...

---

