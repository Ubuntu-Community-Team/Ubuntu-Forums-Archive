---
title: "just installed ubuntu and get Error 22:No such partition"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by ajlinzey on 2008-04-15
I just installed ubuntu to a new hard drive om a PC running XP professional. GRUB comes up and when I select ubuntu I get the error 'Error 22: no such partition 'checking the grub command that is trying to boot ubuntu there is toot=/dev/sdb3. if I boot from the ubuntu bible CD(which is where I did the install from and run the partition tool it sees the new partition as /dev/sdb3. Note my system uses SATA drives which  according to the ubuntu bible can complicate the install. Also I had the installer put grub on the new hard drive, I was paranoid about messing with the boot sector on my windows drive. Any ideas?
Thanks
Andy

---

### Post by zwygart on 2008-04-15
Hi,

I don't have a lot of time. But I can say you that Ubuntu and GRUB don't call the partition the same way. sdb1 on ubuntu is not sdb1 on grub. You may try hdb1 on grub, If not other threads or user may help.

---

### Post by torgrot on 2008-04-16
Try going into the BIOS screen and selecting the other hard drive as the first one in the boot order, if you can.

torgrot

---

### Post by ajlinzey on 2008-04-17
zwygart:
There are a few windows partions on the drive I installed ubutntu onto so should I change the grub command line to /boot=/dev/hdb1 or /boot=/dev/fdb3 ?
torgrot:
the other hard drive has windows XP on it with no grub so if I boot from there I get my normal XP system which is how I'm posting this.
Thanks

---

### Post by bodhi.zazen on 2008-04-17
My guess is that when you boot the Ubutu hard drive Grub is seeing your hd as (hd0)

You can probably boot from the grub command line. You can use tab completion.

At the grub menu type c

This will bring you to a grub prompt.

Then type

root (hd0)
kernel /boot/vml<tab>

If you get file not found,

root (hd1)
kernel /boot/vm<tab>

The write down the proper partition for your root (hd0 or hd1)

Then boot the live CD , mount your Ubuntu installation, and check /boot/grub/menu.lst

Make sure the Ubuntu stanza points to the proper hard drive, both root and kernel lines.

===========

Of course the simple solution is to install grub into your MBR on your first partition. Like this :

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

So it looks like pick your poison, learn to configure grub or install it to the MBR and use the defaults, which should work.

If you have problems we can easily configure grub and/or restore your windows boot loader.

---

### Post by ajlinzey on 2008-04-19
I couldn't figure out how to get the command to span 2 lines so I tried 
root (hd0) kernel /boot/vml<tab>
and got 'Error 17:Cannot mount selected partition'
and tried 
root (hd1) kernel /boot/vml<tab>
and got 'Error 17:Cannot mount selected partition'
in the Ubuntu Bible there is mention of how grub sees SATA drives which I have. from what I've been able to find out SATA drives are labled sda,sdb,... and the partitions sdb0,sdb1 etc. ubuntu is on the 3rd partition of of my new (2nd) drive, so I retried the grub command with (sdb0), (sdb1),and (sdb2) and got the same result. I think I'm going to blow away every thing on the new drive and reinstall ubuntu with no windows partitions on the drive.

---

### Post by bodhi.zazen on 2008-04-19
You need to know the partition you are trying to boot.

root (hd0,0) or root (hd1,0) would be my guess.

Each line is separate and you can use tab completion.

root (hd<tab>

kernel  /boot/vmlin<tab>

If you get nothing with the first tab, hit it the tab key twice.

Did I give you a link on partitions ?

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by ajlinzey on 2008-04-21
thanks it looks like 
root (hd0,0)
works when I inline edited the grub comand line
now I've just fix menu.1st
-Andy

---

