---
title: "Cant boot linux"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by bigben on 2006-07-05
In my previous thread i asked how to reinstall grub.i formatted my c(xp) drive and couldnt boot grub anymore but thats fixed.
But now when the os slection screen comes up and i select ubuntu the following msg appears:

root(hd0,2)
Filesystem unknown,partition type 0x5
Kernel /boot/vmlinuz -2.6.12-9-386
root=/dev/hda3 ro quiet splash
Error 17: cant select partition

(my hd has 3partitions: C(xp),d(linux) e,(free space)
wheres im not sure wether e or d has linux on it)

Can anyone help me fixing this problem?
TIA

---

### Post by richbarna on 2006-07-05
Hmm.
Ok, so is it like this?
C = No xp, formatted (are you posting from another computer?)
D = Ubuntu ,3 partitions, Boot, Home, Swap.
E = Nothing 

I think you should have 5 partitions in all, so to check this, when you boot and GRUB comes up you need to go to the os that your trying to boot and press Ctrl+Alt+F1 to get to the Grub prompt.

Here is a guide on how to edit your menu.lst from there:-

> TROUBLESHOOTING GRUB AT BOOT MENU
1) Assumes you a menu item that no longer boots or you get to a screen that says grub at a prompt or command line. Press C for commands and press enter.
2) To find available hard drives.....and then partition info
root (hd then press tab I get 2 responses as I have 2 drives hd0 and hd1
I now type
$ root (hd0, then press tab your responses about what grub finds may be
hd0,0 ext2
hd0,1 reiserfs
etc
hd0,5 filesystem type unknown partition type 0x82 (my swap file)
You may of course get fat vfat type responses or ntfs responses for Microsoft types.

3) To find my kernel.
$ find /boot/vmlinuz and press enter
The response was (hd0,0) for me but you can have more if you have a multiboot linux system.
I tried to trick grub by command root (hd1) and then using the find command but grub still gave the correct response.....what a beauty...

4) To find my initrd
$ find /boot/initrd.gz
response for me was (hd0,0)

ALTERNATIVELY now that you know that hd0,0 is your /boot partition (in this example)
$ root (hd0,0)
$ kernel /boot/ and press TAB to show files in boot folder and I find my initrd.gz listed

The info you have just gained can now be used to either create commands to boot your linux kernel or to edit a line or two that contained some error without having to load rescue cds etc

---

### Post by cotcot on 2006-07-05
Can you post your partition table ? (in terminal : sudo fdisk -l) You can use the liveCD/installCD for that.

---

### Post by richbarna on 2006-07-05
[QUOTE=cotcot]Can you post your partition table ? (in terminal : sudo fdisk -l) You can use the liveCD/installCD for that.[/QUOTE]

coctcot is right, if editing from grub prompt is difficult, you can pop in the live cd, go to System/Administration/Disks to find the Linux partition.

Also you can use gparted System/Administration/Gnome Partition Editor

But basically you need to edit your Boot/Grub/menu.lst

So that you can correct the mistake that makes it look for your linux kernel in the wrong place.

The last option is, if you have actually got rid of Xp and this is a new Ubuntu install, is to start from fresh using this guide :- [http://www.psychocats.net/ubuntu/installing.html]("http://www.psychocats.net/ubuntu/installing.html")

Remember that when you dual boot Linux with Windows, you should install windows first.

Good Luck :)

---

