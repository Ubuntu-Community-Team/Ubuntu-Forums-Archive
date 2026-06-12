---
title: "GRUB doesn't display any thing"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by karim5 on 2006-08-20
Hello,

I just installed ubuntu 6.06 on my laptop which has many partitions (Windows XP professiona and Linux Mandriva).
I overited Mandriva partitions with Ubuntu (/dev/hda7 for the "/" and /dev/hda6 for the "swap", /dev/hda1 remains reserved for Windows).
The installation process went fine, but when I restart my laptop, I get a king of a prompt which dispalys "GRUB" and freeze the computer without allowing me to do any thing.

On the opposit when I boot with ubunto installation CD I can access to GRUB menu version 0.97 and get access to a choice menu with all the available OS and I can boot Windows or Ubunto...

Just to mention that before installing ubunto I was booting with LILO to choose between Windows or Mandriva and i was working well.

This problem occurs only with grub installed on my hard drive, even if I checked the menu.lst file and it seems containing the right references for ubunto and Windows.

Any advise ?

Regards

---

### Post by kebes on 2006-08-20
First thing to try is to reinstall grub. Boot off the Ubuntu 6.06 CD. When the LiveCD is booted, you can run (on the commandline) "grub-install" (or just "grub" if you want more control over what happens). This should re-install the GRUB bootloader into the master boot record (MBR). These instructions:
[http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation)
Refer to fixing the MBR after a Windows install changes it, but the same command should work for you here.

Another thing to try is to install LILO instead of GRUB. If you have an older motherboard but a big hard-drive, grub will have problems booting. It usually issues an error code ("Error 18" or whatever). You can view my previous post here:
[http://www.ubuntuforums.org/showthread.php?t=230384](http://www.ubuntuforums.org/showthread.php?t=230384)
There, I explain in detail how to get LILO installed instead of GRUB. This is what worked for me on an older machine that had a large hard drive. Since LILO worked for you in the past, it's worth a shot.

Hope that helps.

---

### Post by karim5 on 2006-08-21
I downloaded and installed lilo, but still getting the pseudo menu "GRUB" which freeze the computer if I don't insert the installation CD.

I have three (3) partitions :
/dev/hda1 (40 Gb) for Windows
/dev/hda2 (35 Gb) for ubuntu
/dev/hda3 (2 Gb) Swap for ubuntu

Following your recommandation I have resized the linux partition to 20 Gb to be under the 32 Gb, and will try.
Unless it's due to the fact that the MBR which is located on the /dev/hda2 is too far from the beginig of the hard disk, because it's the second partition after the Windows one (/dev/hda1) ???!!!

Any other clue ?

---

### Post by karim5 on 2006-08-21
When I run the command : setup (hd0,1) I get the following error during the process, is it really non fatal and without impact ?

Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
[COLOR="Red"]Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal
Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal[/COLOR]Running "install /boot/grub/stage1 (hd0,1) "/boot/grub/stage2 p "/boot/grub/menu.lst"... succeeded
Done

Does the failing embed explain my problem or just a warning ?

---

### Post by kebes on 2006-08-21
> **karim5 said:**
> When I run the command : setup (hd0,1) I get the following error during the process, is it really non fatal and without impact ?

I'm pretty sure that error message *is* fatal! Look here for instance:
[http://www.syllable.org/discussion.php?id=1030](http://www.syllable.org/discussion.php?id=1030)

Apparently the problem may occur when there is not enough space in the master boot record (MBR) to fit the entire GRUB bootloader. This is your problem.

What did you use to partition your hard drive originally? Did you let the Ubuntu install wipe the drive, or is the allocated based on a previous (e.g. Windows) install? That might explain why the MBR is not "big enough". You have a couple of options:

1. Reinstall GRUB. Do it manually this time. Don't use "grub-install". Instead go into the grub interactive system by going "sudo grub". See instructions here:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
Make sure to specify the right syntax for your hard drives and partitions. Grub uses a special convention that counts from zero. So hda1 is hd0,0 in grub. hdb3 is hd1,2 in grub, and so on.
If this fails, paste the error messages here, or try one of the following:

2. Install GRUB not to the MBR, but to a different partition. For this to work the partition must be "close" to the beginning of the disk (1st partition). You can decide this when doing the grub-install. Instead of selecting the MBR for your first disk using "/dev/hda" you could select a specific partition using "/dev/hda1". (Or in grub manually instead of doing "setup (hd0)" I guess you go "setup (hd0,0)") I've never done this but I believe it's possible.

3. Move the 1st partition on the disk so that there is some free space in front of it. I don't think you need much (<1Mb?). This may involve resizing and moving other partitions. Backup your data first. Reinstall grub and see if it works now (the "not fatal" error should go awa).

4. Install LILO. I know you said you already installed it... but it must have failed during the installation. (Otherwise you wouldn't see the grub boot menu.) Did it give you an error message? It's quite possible that there is not enough space for LILO in the MBR either, but the error message might help.

Hope one of those works...

---

### Post by karim5 on 2006-08-23
I wiped the hole disk yesterday (70 Gb) re-installed Windows XP (familial edition) , and shrinked it's partition with magic partition to 20 Gb, so leting 50 Gb free.
I then installed ubunto, by choosing the secong option (use all the free space available).

I was sure this would help, but still the same problem :-(
, After rebboting I get a message in the upper left corner "GRUB" and the laptop freeze. When I boot with the CD, I have access to both Windows and Linux !

I also accessed to the command line before booting any OS from grub and issue :
root (hd0,0)
setup (hd0,0)
And worked as expected

Any other suggestion ?

---

