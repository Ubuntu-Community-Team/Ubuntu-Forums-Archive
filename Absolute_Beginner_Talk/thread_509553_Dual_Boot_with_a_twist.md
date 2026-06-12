---
title: "Dual Boot with a twist"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by llzero1337 on 2007-07-25
hello as you may or may not know i tried to dual boot once but something happend and my windows hdd messed up today i got it all working again with all my fiels yay !!!

anyway i was wondering how i can dual boot from 2 ide hdd's without formatting and keeping all my files untouched i want to turn my computer on and pck what Os to boot from is this possible thanks for any help ps i have Windows XP on a 200GB and Ubuntu fawn on a 120gb hdd

---

### Post by llzero1337 on 2007-07-25
bump

---

### Post by w4ett on 2007-07-25
Here is a how-to to install grub to is will work with your additional OS:

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Here are the steps

   1. Boot your computer with Ubuntu CD.
   2. Go through the install process until you reach "[!!!] Disk Partition."
   3. Select Manually Partition.
   4. Mount the appropriate linux partions:
      /
      /boot
      swap
      DO NOT FORMAT THEM
   5. Finish the manual partitioning.
   6. Select "Yes" when it asks you to save the changes.
   7. It will give you errors saying that "The system couldn't install ....." after that; ignore them. Proceed with selecting "continue" until you get back to the Ubuntu installation menu.
   8. Jump to "Install GRUB."
   9. Once it is finished, simply restart your computer.

---

### Post by MQMike on 2007-07-25
If those two OSs are already there, as you say, and both HDs are IDEs, then all you have to do is re-install GRUB to the Master Boot Record of the Windows XP drive (which is the first HD in BIOS boot order, right?).
It’s easy.  Basically, get a grub prompt (by typing sudo grub at a regular Terminal), and type a few commands, like:
grub> root (hdx, y)
grub> setup (hd0)
grub> quit
$ exit

(hdx, y) is where your Ubuntu is.  If, for example, it is on the second hard drive, the first partition, then (hdx, y) = (hd1, 0)  (note:  GRUB counts hard drives and partitions starting from zero)
Also, (hd0) refers to the MBR of your Windows XP drive (the first HD in BIOS order).

See my How-To for the steps and details:
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

(The second Post there shows how to change the default OS and  the timeout.)

---

### Post by KimoSaber on 2007-07-25
Try this link  ([http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu](http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu)), that is the tutorial I used to install Ubuntu 7.04. Follow the steps and you will not go wrong.

I have two separate drives:
1. Ubuntu (Master)
2. Windows XP (Slave)

You don't have to mess with partitioning your Windows XP drive. You can remove/upgrade Ubuntu later. I hope it helps.

---

### Post by llzero1337 on 2007-07-25
ok here is some info i have ubuntu on master and windows on a slave will i need to format or reinstall anything and will i need to back up ? im so sorry for being a nusense but i sdont wanna go through what happend the first time but thanks for the help i appricicate it all

---

### Post by MQMike on 2007-07-25
In that tutorial I mentioned:
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/inde...opic=3081671.0](http://kubuntuforums.net/forums/inde...opic=3081671.0)

If XP is on a non-first HD, then you simply use map commands in the boot menu, and that, too, is explained if your scroll down through the subsequent posts following the first/main post there.  Easy.

---

### Post by MQMike on 2007-07-25
"ok here is some info i have ubuntu on master and windows on a slave will i need to format or reinstall anything and will i need to back up ? im so sorry for being a nusense but i sdont wanna go through what happend the first time but thanks for the help i appricicate it all"

If you just simply install/re-install GRUB, that should not affect or damage anything.  I do it all the time.  It only concerns the MBR of the drives, where the bootloader is.  (And with XP, you can always restore the MBR using the XP CD; in Linux, with GRUB. it's not a problem either.)  If I correctly understand your question here.

---

### Post by KimoSaber on 2007-07-25
Backing up your Windows XP is always a good idea. However, if you use the tutorial by Alexander Grunder, you only need to make a few minor adjustments. The tutorial was done for Ubuntu 6.06. 

For example:
Once the CD has fully loaded, it's a good idea to check if you configured your hard drives correctly before installing. You don't want to wipe out your Windows operating system and important files! To do this, go to SYSTEM > ADMINISTRATION > DISKS. 

With Ubuntu 7.04, you go SYSTEM>ADMINISTRATION> SYSTEM MONITOR> RESOURCES.  You should be able to see both drives. 

Second correction:
This image shows what's on /dev/hda1 (in Windows terms this would be considered drive C:). It also tells me what format the drive is. Here it shows Extended 3 (aka ext3 – the default format for Linux). If you just bought a fresh drive, hda1 may not be formatted at all. 

On my computer, its shows my Ubuntu linux (Master) drive as /dev/sda 1. The Windows XP drive shows as /dev/sdb 1.

Important: When you reinstall Ubuntu with the Live CD, that it shows that the Master drive is Ubuntu.  If you go an read the tutorial again it will make sense.

---

### Post by llzero1337 on 2007-07-25
ok thanks i will try later after i back up my things thanks again for ptting up with me and all the help!

---

