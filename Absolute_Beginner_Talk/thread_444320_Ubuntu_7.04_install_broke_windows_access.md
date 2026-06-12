---
title: "Ubuntu 7.04 install broke windows access"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by femens on 2007-05-15
I tried to install Ubuntu 7.04 on my Compaq SR1550NX desktop system and all went well until I tried to restart at the end of the process. I got the Grub menu showing I could boot to windows or to Ubuntu, but neither option worked. I've subsequently reinstalled Dapper Drake on the system's external USB HD and that boots OK. If I 
try to enter Windows by booting from the internal HD, I get a Grub error 21, which means the command referred to a non-existent HD. That's as close as I can get to Windows.

Can anyone tell me how I can edit that grub entry to cause it to boot to windows XP?  

I've got some time critical stuff hanging over head and need to get access to that windows install to get it done.

---

### Post by dstew on 2007-05-15
We need to get information about your system. Boot an Ubuntu Live CD and open a terminal window. Enter the command sudo fdisk -l and post the result to the forum. Then, try to mount your linux install partition onto the Live CD filesystem:```
sudo mkdir /media/ubuntu
sudo mount /dev/sdaX /media/ubuntu
```
Of course, the device name /dev/sdaX will have to be changed to the real name of the partition that has the linux install. Once your linux install file system is mounted on the Live CD file system, you will be able to look at and edit the grub menu.lst file:
```
sudo nano /media/ubuntu/boot/grub/menu.lst
```

---

### Post by sandman55 on 2007-05-15
You could boot with your XP CD and choose fixmbr to repair your Master Boot Record see this [Link](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console)  You will only be able to boot into 
xp and when you are ready you can try again with Ubuntu
Even the old win98 boot floppy will fix it with fdisk /mbr
There is also the [Super Grub Disk](http://supergrub.forjamari.linex.org/?section=features) I think you can get in with that it is supposed to do all sorts of things

---

### Post by femens on 2007-05-15
Yah Hoo!!! That did it. I dug out the XP install CD and used fixmbr to reinstate the boot record on the internal disk. I can still access Ubuntu by intercepting the boot process and telling it to boot from the external USB disk. 

Next step is to see if Partition Magic's boot manager system will let me set up a dual boot.  Then it is to get busy with all the stuff that's been backing up while I search my bals head for hair to tear out over losing Windows.

Thanks to both of you answerers. You've been a great help to a desperate newbie.

---

### Post by femens on 2007-05-15
Make that "bald head"!

---

### Post by sandman55 on 2007-05-16
When you use parition Magic set up three partitions one for swap usually double your ram one for root (known as / ) and one for home then when you do an install and you get to choose about partitions choose the third option and do a manual install and format Home and / as ext3 and swap as swap. The advantage of having a separate partition for home is when you reinstall or upgrade to a new version you only do it to / (root) and leave your home with your documents untouched.
Before you do any of this back up anything important.

---

