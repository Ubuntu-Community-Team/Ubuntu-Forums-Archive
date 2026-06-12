---
title: "Dual Boot"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by V1ru586 on 2007-07-04
Okay i just finishes installing the second hard drive into my system...now i have the Ubuntu OS as Slave, i want my Windows OS to be the master...now i have to fix the BIOs in Order to boot from my Slave HD Which s Ubuntu....Is there anything i can do to Be able to choose which OS to boot from without goinng to the BIOS??? remember i have Ubuntu as a Slave and Windrows as Master. Thanks you very much!!:p

---

### Post by lisati on 2007-07-04
I don't have any experience with one OS on one HD, and another OS on another HD. My experience relates to installing different OSes on different paritions of the same physical HD.

My  and laptop are both "Dual boot" with Ubuntu 7.04 as the default OS, the Ubuntu installer set up  the "GRUB" boot loader, which takes care of many of the details of sorting out which OS to boot.  The process was relatively painless, with only a minor tweak on my laptop to make sure my USB mouse kept on working.

Don't be alarmed if you need to do some tinkering and tweaking.

---

### Post by iramhernandez on 2007-07-04
You need to have something set up to let you choose the OS.  Ubuntu includes grup, but you can also use lilo, or if you want to use a commercial  type product, partition magic includes a utility to you can install.  Grub is pretty easy to configure -- I would recommend that..  There is tons of documentation on how to do this with grub on these forums.  Config files are in the  the /boot/grub directory.

---

### Post by lisati on 2007-07-04
a quick "off the top of my head" answer about going through BIOS is that once you've got the boot loader stuff sorted, and appropriate settings in BIOS, you probably won't have to touch the BIOS again.....I'm not sufficiently clued up on using separate HD for separate OSes to give more details..... Anyone else?

---

### Post by gn2 on 2007-07-04
If you can access a "Boot Sevice Selection Menu" by pressing F8, F2 (or whatever key) at boot time, then you can use that to select which drive to boot from.

This works where each OS is installed along with it's own bootloader on separate hard drives.

The default OS can be set by the BIOS boot order, and the other OS can be selected by using the F8, F2 (or whatever key) to select the other hard drive.

---

### Post by V1ru586 on 2007-07-04
How can i configure grub? if Ubuntu is not the Master HD???Do i have to configure Windows??? plzz help me out!

---

### Post by gn2 on 2007-07-04
If you can get a boot device selection menu, by pressing F8 or whatever, that's all you need if Grub is on the Ubuntu slave drive.

It just works.

---

### Post by coolen on 2007-07-04
> **V1ru586 said:**
> Okay i just finishes installing the second hard drive into my system...now i have the Ubuntu OS as Slave, i want my Windows OS to be the master...now i have to fix the BIOs in Order to boot from my Slave HD Which s Ubuntu....Is there anything i can do to Be able to choose which OS to boot from without goinng to the BIOS??? remember i have Ubuntu as a Slave and Windrows as Master. Thanks you very much!!:p

Set up the hard drives, make sure your BIOS recognises them correctly, and run the Ubuntu installer (or reinstall Grub).
Works for me.
If not, try installing Grub to hd0,0. That's the equivalent to hda1, in Grub terms.
Google for more instructions. I've never installed Grub manually.

---

### Post by confused57 on 2007-07-04
> **V1ru586 said:**
> Okay i just finishes installing the second hard drive into my system...now i have the Ubuntu OS as Slave, i want my Windows OS to be the master...now i have to fix the BIOs in Order to boot from my Slave HD Which s Ubuntu....Is there anything i can do to Be able to choose which OS to boot from without goinng to the BIOS??? remember i have Ubuntu as a Slave and Windrows as Master. Thanks you very much!!:p
The grub entry in this thread "should" boot Windows on your master drive:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by V1ru586 on 2007-07-05
thanks confused57, but it only says instructions about  changing the meny.lst If ubuntu is set as a master i repeat i have windows as a master not a slave!.... the reason i have windows as a master is bcuz i have a SATA(red cable that connects to my hd) HD i dont know how ot make it a slave

---

### Post by gn2 on 2007-07-05
All SATA drives are master, slaves only exist on IDE channels.

---

### Post by confused57 on 2007-07-05
> **V1ru586 said:**
> thanks confused57, but it only says instructions about  changing the meny.lst If ubuntu is set as a master i repeat i have windows as a master not a slave!.... the reason i have windows as a master is bcuz i have a SATA(red cable that connects to my hd) HD i dont know how ot make it a slave

Don't worry about master/slave drives, the Window's entry should still work if you're able to boot to your Ubuntu drive by booting to it first in bios....place the Window's entry at the very bottom of your menu.lst file in grub, instead of above the ###BEGIN AUTOMAGIC,  if it doesn't work, you can just delete it.

---

### Post by V1ru586 on 2007-07-05
so i just type this in terminal
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```

and this in the menu.lst
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

just above ###BEGIN AUTOMAGIC KERNEL LIST
????

---

### Post by confused57 on 2007-07-05
> **V1ru586 said:**
> so i just type this in terminal
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```

and this in the menu.lst
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

just above ###BEGIN AUTOMAGIC KERNEL LIST
????
You might want to place it at the very end of the menu.lst file to start with...if it works, then you can move it above ###BEGIN AUTOMAGIC KERNEL LIST...if you want, then go ahead and place the Window's entry above this line, this way Windows will boot by default, unless you select Ubuntu.

---

### Post by V1ru586 on 2007-07-06
I dont seem to be able to open it in termianl....when i copy and paste it asks me for a password, even when i type it manually! any help?

[[IMG]http://img106.imageshack.us/img106/5897/screenshotoa9.th.png[/IMG]](http://img106.imageshack.us/my.php?image=screenshotoa9.png)

---

### Post by confused57 on 2007-07-06
Sudo gives you temporary root privileges, which you must do to edit files outside your /home directory, and you'll need to enter your user password...you won't actually see any indication you're entering it, but you'll need to in order to edit your /boot/grub/menu.lst...type in your password, then press "enter".

---

