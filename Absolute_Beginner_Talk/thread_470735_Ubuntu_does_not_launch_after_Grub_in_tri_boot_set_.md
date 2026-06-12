---
title: "Ubuntu does not launch after Grub in tri boot set up"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by ilovebsod on 2007-06-11
I set up a workstation w/ 2 80GB hard drives.  the primary has a 40GB partition w/ XP (Xp was installed first) and a 40GB partition unformatted.  The 2nd drive is all Vista (Vista was installed 2nd).  Both Vista and XP can be selected and booted in the Windows boot loader.

Then I installed Ubuntu 7.04, in the partition config I selected 'guided - use largest continuous space'.  The install completed successfully.

upon reboot Grub loads, I have the normal options Ubuntu, Ubuntu recovery mode, memtest and I an option to launch the Windows boot loader.  When I select either Ubuntu or Ubuntu recovery mode Grub attempts to launch, but just sits @ a black screen with a blinking cursor.  I am unable to type anything or reboot w/ ctrl alt del.  I must hold the power button in to power the machine down.

if I select the Windows option in Grub it loads the Windows boot loader which gives me the XP and Vista option.  Both of these load w/o issue.

any ideas on how I can get ubuntu to load?

---

### Post by logos34 on 2007-06-11
from the ubuntu love cd, open a terminal and type
sudo fdisk -l

post it please

---

### Post by ilovebsod on 2007-06-12
I formatted and started over again, I installed Vista on the SATA0 drive, then turned off SATA0 in the bios and installed XP on SATA1 disk w/ a 38GB partition and then installed Ubuntu on the remaining 39GB.  Grub loads, I see the normal options and an option for XP.  I can boot into XP fine, but when I select any of the Ubuntu options again the screen just stays at a black cursor.  I'm thinking x or ubuntu can't run on this workstation (Dell Optiplex 320 pentium D 3.4ghz w/ a Nvidia 8600GT video card)

here is the fdisk -l from the current set up

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4972    39937558+   7  HPFS/NTFS
/dev/sda2            4973        9528    36596070   83  Linux
/dev/sda3            9529        9729     1614532+   5  Extended
/dev/sda5            9529        9729     1614501   82  Linux swap / Solaris

---

### Post by ilovebsod on 2007-06-12
just to rule out the multiple booting being the problem, I formatted again and installed only Ubuntu.  Grub doesn't even load now, just a black screen with a blinking cursor

---

### Post by dstew on 2007-06-12
I think you are confusing the installer by changing you BIOS setup. I recommend setting your BIOS to be the way you want it to be when the system is running. The problem is that grub and linux identify your disks using different techniques. Linux, which is what is running when you do your installation, has its own routines for identifying disks. It passes these to grub in a file, called device.map that is in the /boot/grub directory. When grub boots, it identifies the disks by looking at the BIOS disk table, and then it looks at the device.map file to figure out where the drives are. However, if the drive configuration has changed, grub can get lost.

If the Live CD runs on your system, then so will an installed Ubuntu system. It is just a matter of getting it installed correctly. One way to do this is to install Ubuntu without installing grub, and then take care to install grub correctly by hand. For example, with your first install, where grub would boot to the windows boot loader, we could have worked a bit and probably staightened grub out. Since you want a triple boot system, why don't you go back and re-install XP and Vista, and then we can try to install Ubuntu again, and take some care to make grub work properly. I would recommend that you not install grub at the end of the Ubuntu install, which I think is an option when installing from the Live CD (the alternate install CD doesn't give you a choice).

---

### Post by ilovebsod on 2007-06-12
I'm not changing the bios settings between the install and attempt to run.  

I disabled SATA0, booted from the live CD, installed Ubuntu to SATA1, rebooted (with SATA0 still disabled), Grub launches.  I'm unable to get into Ubuntu from that point.

I even moved the drive to SATA0, enabled it (while disabling SATA1, which doesn't have a drive attached at this point) and ran through the install process.  the same problem occurs.

---

### Post by dstew on 2007-06-12
Can you boot your Ubuntu installation from the Live CD opening menu?

---

### Post by logos34 on 2007-06-12
The fact that your getting the grub menu screen at least shows that grub stage1 on the mbr can find the root partition to bring up the menu.lst with the options to boot windows and ubuntu...but then it just stops at a blinking cursor, which would seem to indicate that it can't find or load/decompress the kernel via initrd.gz and vmlinuz.  Maybe someone else can explain exactly what happens at this stage.  There's no output as it checks the filesystem and hardware, let alone an x server error...never even gets that far.

Given that this problem manifests itself over repeated installs and varying configurations indicates that there could be corrupted files on the cd and/or on the original downloaded iso, or maybe it's a bad burn.  Did your verify the md5sums of the iso and do a cd integrity check before install?

Or maybe the debian installer got the ubuntu entries wrong (unlikely) in /boot/grub/menu.lst, or device.map is wrong.

Quick test:
boot to the grub menu, then select the ubuntu entry, hit 'e', then 'e' again to edit the path.  change root from '(hd0,x)' to '(hd1,x)' or vice-versa.  You could also try editing the kernel line to use 'root=/dev/sdx' instead of the UUID format.

That's my best stab at the matter.

---

### Post by o0maverick0o on 2007-07-25
I am having all the same problems.  Replace root(hd0,0) with root(hd1,0) and it said the disk was not found.  I changed it back and then added then modifieid the line root=/dev/sdx - but still no dice.  I am not trying to do a dual boot or anything.  All I want it s to run Ubuntu Server 7.04 on a Dell Optiplex - didn't think that it was going to be this big of an issue.

Any other thoughts?

---

### Post by o0maverick0o on 2007-07-25
Success! Lilo is in fact the key.

Once the server install interface asks for the language, select the Go Back option - all the way untill you get to the main menu.  There is an option on there that mentions something like download or copy "Installation files".  Select that.  Once that happens, then there will be option on the main menu to install Lilo (you will have to scroll down).  Select that and proceed as normal.  

Worked like a charm.  I've spent so much time on getting it to work, I forgot what I wanted to do with it. lol!

---

### Post by e_james on 2007-07-25
I have installed 7.04 on 3 different computers using the alternate CD. Two of them worked fine, no problems. The third, over several attempts, consistently gets the location of the boot partition wrong. I can get ubuntu to start by editing the grub menu before booting and then editing menu.lst to keep it that way, but if a new kernel is installed I have to do it all again. I had suspected that it was something to do with the fact that the third PC was a triple boot setup with one distro using a boot partition (Ubuntu) and one not (KnoppMyth).

---

