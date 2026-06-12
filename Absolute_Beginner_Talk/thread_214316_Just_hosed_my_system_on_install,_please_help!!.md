---
title: "Just hosed my system on install, please help!!"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by mezzers on 2006-07-12
Hi all, I'm an absolute newbie who's been wanting to try Linux for a while. After looking around here for a few days and pouring over the advice and documentation, I installed Dapper off the LiveCD this morning and somehow still managed to kill my system. I'm running:

Windows XP
AMD 64 3000
1Gb Ram
2 hard drives, IDE
Onboard SiS graphics
Via K8M800
Ethernet

Here's what happened: I created the partitions I wanted beforehand using GParted off the LiveCD, then installed. When it got to the partitions part for some reason it didn't create /dev/hda2 as a fat32 partition as I wanted; it made it ext3 instead. So me, being a smarty pants, let the install finish and then stayed on the LiveCD, went back into GParted, and tried to reformat /dev/hda2 as fat32. It gave me an error saying it couldn't complete the operation because the device was busy, and suggested I reboot. So I did, into GRUB, and started my newly installed Ubuntu.

It got to Checking all filesystems...and then said:

fsck.ext3: Bad magic number in superblock while trying to open /dev/hda2
/dev/hda2:
The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>
/dev/hda5: clean
root@mary-desktop:~# t from this shell and continue system startup

Not knowing what this meant, I pressed enter. It died. So I rebooted using the LiveCD, checked the forum, and tried to unmount then e2sfsck /dev/hda2. It said it wasn't mounted, then started asking a lot of questions about inodes and stuff. I looked on the forum again and answered yes to all, then rebooted again...But this time (fearing the worst) I tried to get into XP. It got past the blue bar to where it should have given me my XP desktop, but the screen stayed dark. I rebooted and tried XP again. Same thing. 

Then I tried rebooting into Ubunto (from GRUB) and got the same error as above. e2fsck /dev/hda2 again (now realizing I could do it from the command line), whole bunch of questions and yeses again, and once more it wouldn't go any further.

So I'm on the forum now via the LiveCD, which is now the only part of my system that's working!! :sad: 

I do have a backup of XP, but do I have any other options?? Or have I totally hosed everything? I'm off to bed now but will check back this evening. Thanks in advance for any and all help!

---

### Post by steve.horsley on 2006-07-12
You don't describe all your partitions, so this is a guess, but here goes...

Linux cannot run on a FAT drive - cannot use FAT as the system disk, the root of the file tree, although it can mount FAT drives at less important places. Fat cannot store the necessary files permissions flags. This will be why the installer used ext3 instead. 

The GRUB bootloader is a complex multi-part thingy. It starts with some code in the bootsector of the disk, but it uses a menu file that is located at /boot/grub/menu.lst on one of the partitions - normally the root Linux partition - probably hda2 in your case. 

Formatting hda2 to FAT will have hosed the Linux install and the menu file that GRUB looks for. Grub cannot offer you a menu any longer. 

I suggest you re-run the installer and let it use ext3 for the root filesystem. It should find Windows and add that as a menu option for GRUB. Alternatively, use the Windows installer disk to restore the original Windows bootloader.

---

### Post by richbarna on 2006-07-12
> **steve.horsley said:**
> You don't describe all your partitions, so this is a guess, but here goes...

Linux cannot run on a FAT drive - cannot use FAT as the system disk, the root of the file tree, although it can mount FAT drives at less important places. Fat cannot store the necessary files permissions flags. This will be why the installer used ext3 instead. 

The GRUB bootloader is a complex multi-part thingy. It starts with some code in the bootsector of the disk, but it uses a menu file that is located at /boot/grub/menu.lst on one of the partitions - normally the root Linux partition - probably hda2 in your case. 

Formatting hda2 to FAT will have hosed the Linux install and the menu file that GRUB looks for. Grub cannot offer you a menu any longer. 

I suggest you re-run the installer and let it use ext3 for the root filesystem. It should find Windows and add that as a menu option for GRUB. Alternatively, use the Windows installer disk to restore the original Windows bootloader.

Now that is some sound advice !!!!

>  The GRUB bootloader is a complex multi-part thingy

I couldn't have put it better myself :)

Good work Steve, I'm hunting down the partition threads myself. Maybe this should be a seperate section for the new users, with a direct link to [http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html) :-k

---

### Post by mezzers on 2006-07-12
Fixed with a reinstall! And it's a thing of beauty! :-D 

Thank you, Steve, I hadn't realized that /dev/hda2 MUST be the root. (So that's why it kept trying to make it ext3!) I confused myself with some graphical representations of various partition setups on another site, which led me to believe any fat share needed to be sandwiched - literally - between XP and Ubuntu's /. 

I really should stop following directions quite so closely....

XP came up fine afterwards, and I can't wait to dig into Ubuntu and see what else I can screw up. I'm sure I'll be back! 

Many thanks again.

---

