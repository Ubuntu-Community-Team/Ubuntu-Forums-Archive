---
title: "Dual boot Ubuntu 11.10 &amp; Win 7"
date: 2011-12-06
forum: Any Other OS
---

### Post by thug_serbia on 2011-12-06
hi guys, i am new on Ubuntu (Linux in general). I have installed Ubuntu 11.10 and because of college needs i must install win 7. and i install it. Now i have problem my win 7 won't start. always starts Ubuntu. I don't have boot menu to choose which system will start. i hope you understand my problem, i am from Serbia so do not blame my bad English! :D ps. i installed Ubuntu first, then win 7.

---

### Post by Drone4four on 2011-12-08
thug_serbia: What you want to do is install Windows 7 first.  But before you do, create the Windows partition with a program called 'gparted' that comes on the Ubuntu LiveCD.  Install Windows 7 on one of the newly created partitions and then install Ubuntu on a different partition.  Are you familiar with the program, gparted, thug_serbia?

---

### Post by Ricx94 on 2011-12-11
if at all possible, I'd suggest starting over by installing windows on entire drive, and then when installing ubuntu, you can shrink windows partition to whatever size you want (keeping in mind windows cannot access ubnutu's partition, but ubuntu can access windows'.)

to start things off, backup anything important, then boot to a livecd of ubuntu (Might have one hanging around from when you installed ubuntu). boot to the disc, and open gparted partition editor. delete all the partitions on your main hard drive, and then make on big ntfs partition.

next, install windows 7. delete the partition you made, and tell windows to partition the drive any way it likes, using the whole thing. get all the drivers working and everything. don't move in backed up files just yet, in case something goes wrong. 

now install ubuntu. choose to install ubuntu alongside windows 7, and adjust the size of the windows partition to whatever you like. keep in mind ubuntu requires 8 or 9 gigs of hard drive space or more. finish installing ubuntu. near the end of the installation, the text on the bottom that says what it is working on should say something about GRUB. this is your boot manager, and will allow you to boot to whichever. when booting, you have 10 seconds to choose windows, or it will auto-boot to ubuntu.

the first time you boot to windows after doing this, it will want to scan for errors. let it do so, it won't take very long. then everything should be working fine, and you can restore any backed up files.

---

### Post by BC59 on 2011-12-11
I'm sure the OP finally did something to fix his problem, because his first and last post was 5 days ago.

---

