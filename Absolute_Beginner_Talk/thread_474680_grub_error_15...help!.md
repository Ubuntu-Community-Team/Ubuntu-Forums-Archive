---
title: "grub error 15...help!?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by fwuffycloud on 2007-06-15
Well i left my sister to sort out my partitions ( i needed to resize the windows one 0)

And now i get GRUB loading please wait...
Error 15

Finally thought i had my windows and ubuntu dual boot fixed then this happens...

Is there a relatively do-able solution to this?

Please help.

Thanks

---

### Post by Malibu Illusion on 2007-06-15
Posting the output of:

```
cat /boot/grub/menu.lst
```

Would help people assist in diagnosis.

---

### Post by fwuffycloud on 2007-06-15
I type that in the terminal?

because when i do i get "No such file or directory"

I'm using the live cd because i cant get past the error at startup.

---

### Post by fwuffycloud on 2007-06-15
bump

---

### Post by confused57 on 2007-06-15
Here's a description of grub error 15:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15)

From the live cd, open a terminal, post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

From the results of "fdisk -l", determine which is your root partition, then mount it in the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Then you can post the output of your menu.lst.

You might also want to run this command in the terminal:
```
blkid
```

compare the UUID's from the "blkid" command to the UUID's listed in your menu.lst kernel line and also in your /etc/fstab(the link explains how to access your fstab).

---

### Post by fwuffycloud on 2007-06-15
Ok, would be a lot easier to do this without that USB mouse problem i cant fix in ubuntu...

But anyhow, the output of sudo fdisk -l is:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11635    93458106    c  W95 FAT32 (LBA)
/dev/sda2           11636       15632    32105902+   b  W95 FAT32
/dev/sda3           18751       19452     5638815    5  Extended
/dev/sda4           15633       18750    25045335   83  Linux
/dev/sda5           19102       19452     2819376   82  Linux swap / Solaris
/dev/sda6           18751       19101     2819344+  82  Linux swap / Solaris

How do i determine my root partition?

---

### Post by confused57 on 2007-06-15
> **fwuffycloud said:**
> Ok, would be a lot easier to do this without that USB mouse problem i cant fix in ubuntu...

But anyhow, the output of sudo fdisk -l is:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11635    93458106    c  W95 FAT32 (LBA)
/dev/sda2           11636       15632    32105902+   b  W95 FAT32
/dev/sda3           18751       19452     5638815    5  Extended
/dev/sda4           15633       18750    25045335   83  Linux
/dev/sda5           19102       19452     2819376   82  Linux swap / Solaris
/dev/sda6           18751       19101     2819344+  82  Linux swap / Solaris

How do i determine my root partition?
It looks like your root partition is /dev/sda4...you "might" be able to go into bios and enable USB legacy, which might help your mouse problem.

You can always restore your Window's IPL to the mbr, so you can boot Windows:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Another thing you can try first is to reinstall grub, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by fwuffycloud on 2007-06-15
Right, thanks a lot for all the ideas.

I'm going to try to reinstall grub like you said first, if that works will that restore my PC to normal?

Also, could you quickly tell me how to get into/what is BIOS, is it the boot options? or setup? i never quite understood that :)

---

### Post by fwuffycloud on 2007-06-15
Argh, none of my commands seem to work in the terminal!

for example when in the grub shell, find /boot/grub/stage1 doesnt work, just says error 15 file not found.

---

### Post by confused57 on 2007-06-15
Looks like you'll need to mount your root partition(see the link), something like this:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda4 /media/ubuntu
```

then you access your menu.lst & fstab:
```
gedit /media/ubuntu/boot/grub/menu.lst
gedit /media/ubuntu/etc/fstab
```

When your computer is booting up, there should be a prompt to press a certain key(F2, Del, Esc) to enter bios setup...once you're in bios setup, you'll need to navigate the different menus to find where to enable USB legacy...if you think you made a mistake, you can always exit setup without saving.  Whatever you change & save...be sure to write down what you changed & don't change but one thing at a time.  That way, you can always enter setup & change it back if doesn't work.

---

### Post by fwuffycloud on 2007-06-15
Yeah, i tried to do that too, but the sudo mkdir /media/ubuntu didnt work either :S

---

### Post by confused57 on 2007-06-15
> **fwuffycloud said:**
> Yeah, i tried to do that too, but the sudo mkdir /media/ubuntu didnt work either :S

About the only thing I can suggest is if you have access to another computer...download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's a small download(5-7 Mb), SGD might be able to boot your Windows or Ubuntu

I see your Windows is on a FAT32 partition, if it's Win98 & you have a boot floppy, you can try booting it and entering:
```
fdisk /mbr
```
this will restore your Window's IPL to the mbr so you can at least boot Windows

or if it's Win2000 or XP and you have an install cd(not a recovery cd)...you can enter recovery console by pressing "r", then entering FIXMBR to restore your mbr.

I'm about out of ideas, since none of the commands you're entering in the terminal are working, other than reinstalling Ubuntu...good luck with it.

---

### Post by fwuffycloud on 2007-06-15
i was gonna say, since the whole grub thing seems to be Linux related, if i just delete the Ubuntu partition would that get rid of the problem'?

And is my Dell reinstallation disk ok to use the recovery console? or is it just a recovery cd?

Because i'm using Win XP

---

### Post by fwuffycloud on 2007-06-15
Also i appreciate your help confused, thanks.

---

### Post by fwuffycloud on 2007-06-15
eek, did not know that FIXMBR means i have to install Windows again... but fine. That seemed to work, now im pretty much back to where i was a week ago :P

---

### Post by confused57 on 2007-06-15
> **fwuffycloud said:**
> eek, did not know that FIXMBR means i have to install Windows again... but fine. That seemed to work, now im pretty much back to where i was a week ago :P

FIXMBR should have just reinstalled Window's IPL to the mbr, not reinstall Windows...it might have been a recovery cd & somehow reinstalled Windows.  Sorry I couldn't help you with your Ubuntu problem, but at least you have an OS that you can use.   Look at all you're learning in the process of troubleshooting your boot problems & you're getting a fresh start with setting up Ubuntu, it's usually easier the 2nd time.

---

