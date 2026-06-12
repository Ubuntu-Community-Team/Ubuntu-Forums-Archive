---
title: "Error 15"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by jec1521 on 2007-04-28
Hey guys,

I'm trying linux out for the first time.  I installed Ubuntu with basically no problems, but for one reason or another, I had to reinstall Ubuntu, but for some reason, after I reinstall it, I get a grub error code 15 when trying to boot for the first time.  The live CD works fine, it just can't boot.  I've tried three times now.  Anyone have any suggestions?

---

### Post by Herman on 2007-04-28
Hello jec1521,
Quoted from the Gnu/Grub Manual,
> 15 : File not foundThis error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.Maybe Grub is trying to tell you it can't find the exact kernel or initrd.img file specified in your /boot/grub/menu.lst. 
Usually this is because of a mistake in your menu.lst file, for example, the exact path or name of your kernel or initrd.img contains an error of some kind.
                             [Super Grub Disk]("http://supergrub.forjamari.linex.org/") can boot your operating system by symlinks to the kernel if you use, from the 'English' Menu,--> Gnu/Linux  --> Boot Gnu/Linux Directly -->...
                                       Boot with Super Grub Disk instead, and then with your operating system running you can check your file and correct your menu entry for Linux.
                           Open your menu.lst file with 'sudo gedit /boot/grub/menu.lst'.
                                       Use the command 'ls /boot' to check for the correct name for your Linux kernel and initrd.img.
                                       Copy the correct name from the terminal output to the menu.lst file and paste it to avoid typos. Don't forget to save the changes in your menu.lst file before you close it.
                           
                                       This error can also occur if the files needed to boot with are missing or corrupt in the /boot/grub directory. Refer to             [Grub loading stage1.5]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_loading_stage1.5") for how to completely delete possibly corrupted grub files and restore them again from /sbin/grub.

---

### Post by MartenH on 2007-04-28
HI,

I had the exact same problem when doing a fresh install of Feisty on my machine. I tried re-writing the mbr as suggested in a thread somewhere but it did no good. I finally found the solution:

Download and burn the 6.10 desktop CD and the 7.04 alternate CD which enables you to do an offline update. Install 6.10, pop in the 7.04 CD and let it update your system to 7.04. No more error 15!

---

