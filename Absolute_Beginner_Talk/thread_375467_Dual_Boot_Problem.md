---
title: "Dual Boot Problem"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by BriS on 2007-03-03
I installed Ubuntu Ultimate Edition 1.2 last week, as I've been meaning to switch for a long time. Yesterday, I decided to permanently switch to Ubuntu but have the option to still boot up windows. Of course, being a complete newbie at Linux, I ran into a lot of problems and read a lot of tutorials. Right now, my real problem is just booting up. Grub doesn't load up when I boot, it just blinks until i get an error saying my computer can't boot from hard disk.

When i install Ubuntu, the installer asks me where to install Grub, I've tried leaving it at (hd0) or (hd0,1) but I'm never able to boot up. I'm assuming that the Ultimate Edition installs differently than just the normal Ubuntu because every tutorial I've read differs from what I have to do, which makes it hard on me since I don't really know what I'm doing. 

In my latest attempt, i had grub be installed onto (hd0,1) and as i said, it didn't load up Grub. I just deleted my Ubuntu partitions using a rescue CD, and windows booted up just fine.  With that, can someone guide me through installing Ubuntu Ultimate Edition (live cd) so i don't have to waste my entire day just trying to get my computer to work?

---

### Post by Amenemhet on 2007-03-03
Sigh search this forum or google...there are literally dozens of walkthroughs out there.

---

### Post by BriS on 2007-03-03
Like I said, I did. Some tutorials tell me to direct grub into the MBR while others warn me not to. I tried both, but grub never loads up on boot.

Cut that, windows doesn't boot, my XP pro CD was on there, and i guess it booted from that.

---

### Post by confused57 on 2007-03-03
You can try reinstalling Ubuntu(I don't know anything about the Ultimate Edition), installing grub to (hd0)...sometimes(not often), grub doesn't install properly.  The live cd can be used to reinstall grub on a hard drive installation:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Here's how to restore your Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You might want to check out the GAG bootloader, see the index of the homepage of the hermanzone website:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
the GAG bootloader works if grub is installed to the root partition, e.g. (hd0,1)...you can make a GAG boot floppy, cd, or install to mbr.

Also, the Super Grub Disk...also listed in the index of the above site is an excellent boot utility to have...it can restore your mbr(Windows or Linux), as well as boot either OS.

---

### Post by rsambuca on 2007-03-03
Do you have just one hard drive, or more than that?  also, how is it partitioned?

---

### Post by BriS on 2007-03-04
I have 4 hard drives, 3 IDE and 1 SATA. I just finished starting everything all over, and it still doesn't work. I installed windows on a 30/80 gig partition, then installed Ubuntu on the rest of it (something like 45gig for the main and 510mb for the swap), leaving grub to (hd0). When i rebooted, grub didn't load and i was stuck with a boot error. So, I'm completely stuck right now, and I really don't want to sit through another windows or Ubuntu installation. Any suggestions?

---

### Post by rsambuca on 2007-03-04
What is the boot error that you are getting.  Do you see the grub loader at all?

---

### Post by BriS on 2007-03-04
I tried reinstalling grub like the link above said, following the steps exactly, but it still doesn't load up grub.

After I boot up and it says boot from CD/DVD, it's supposed to load up grub like it did before, but it doesn't. Then after I leave it for a couple minutes it says "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"

---

### Post by Patrick K on 2007-03-04
Check that the BIOS boot drive is set correctly. I inadvertently set mine to HDD1 and had boot problems. It needs to be set to HDD0.

---

### Post by rsambuca on 2007-03-04
What order are your drives in your Bios?

EDIT:  Patrick beat me to it.  Looks like we are thinking along the same lines, though.

---

### Post by BriS on 2007-03-04
I'm not sure how I'm supposed to term this since I'm still new to this, but...

1) Main drive 80gb (HD0)
2) Empty IDE 40gb (HD2?)
3) SATA 300gb (SDA0?)
4) IDE 120gb (HD1?)

Basically, it's the three masters, each on channels 0 -2, then the slave from channel 0.

---

### Post by BriS on 2007-03-04
Sorry for the double post, but i need a BUMP. 

OK, so i installed GAG, added windows and ubuntu to it, then saved to hard disk. When I booted up Ubuntu, it actually loaded grub, so I could choose all the ubuntu options or windows. I was able to get into ubuntu, but after i rebooted my computer, nothing loaded up, no grub or GAG. So once again, I'm stuck.

---

### Post by confused57 on 2007-03-04
Using the live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

---

### Post by BriS on 2007-03-04
I can get into ubuntu though GAG but i have to boot through a CD (I'm posting this from my Ubuntu, not a live CD)


Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36481   293033601    7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3824    30716248+   7  HPFS/NTFS
/dev/hda2   *        3825        9664    46909800   83  Linux
/dev/hda3            9665        9729      522112+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14593   117218241    7  HPFS/NTFS

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        4864    39070048+   b  W95 FAT32

---

### Post by confused57 on 2007-03-04
Since you're booted to Ubuntu, it might help to post the output(s) of:
```
cat /boot/grub/menu.lst
```
menu.lst is short for menu.list

and
```
cat /boot/grub/device.map
```

Also, I'd also recommend that you burn a copy of the Super Grub Disk(500 kb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
I think you'll be glad you did, it's a great tool to have for troubleshooting boot problems.

---

### Post by BriS on 2007-03-04
I have super grub disk on a CD but when i boot it up, it doesn't give me that interface like in the screen shots, it just gives me the same thing as if i loaded grub in the terminal.


cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=fc9950bf-7701-4624-b8c8-f7d044433da1 ro
# kopt_2_6=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1



cat /boot/grub/device.map
(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/hdc
(hd3)   /dev/sda

---

### Post by Herman on 2007-03-04
Hello BriS,
Here is what the error message means,

"DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"
                                 
                                 The BIOS has looked around in the list of devices listed in the BIOS boot sequence you set in the CMOS and has not found a bootable device.
                                 
                                 1)Check your BIOS boot order in CMOS and make sure this computer is set to boot from the device (eg, hard disk, cdrom drive, floppy drive, or the like), that you are trying to boot.

                                 2)If it is a hard disk, if the drive has been newly installed, has it been plugged in and jumpered correctly and set up in the BIOS? 

                                 4)Is the MBR is okay? Does it have the [55aa bootable device signature]("http://users.bigpond.net.au/hermanzone/p6.htm#What_does_an_MBR_really_look_like")?

Maybe you can check the first two items, but you will need help for the third, try the first two if you like.

Regards, Herman :)

---

### Post by confused57 on 2007-03-04
Your menu.lst and device.map look OK...device.map shows hda as your first boot hard drive(hd0)...and you entries in menu.lst are correct and "should" boot your OS.

Did you follow these instructions for burning the SGD in Ubuntu?:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#To_make_your_sgd_file_into_a_disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#To_make_your_sgd_file_into_a_disk)



Do you happen to have an option to boot Windows from the GAG bootloader?

I wish I could you a definite solution, instead of rambling on...you may want to restore your Windows mbr(see my first reply in your thread), to see if Windows will boot?

Added:  Thanks Herman, I was all out of ideas?

---

### Post by BriS on 2007-03-04
My BIOS order has hard disk last with two CD drives before it, the drive works just fine, and yes the 55aa is there.

As for SGD, I burned the iso on this laptop (Windows). I'm not sure if GAG is even installing onto my computer, I have to use a GAG CD in order to actually use it, but I'll reboot and see if i can boot to windows through it.




EDIT: OK i just booted up with GAG on a CD and then booted up windows, it was just fine. I also booted up Ubuntu through the GAG CD which brought me to the grub menu and opened windows from there, worked just fine too.

---

### Post by confused57 on 2007-03-04
> **BriS said:**
> My BIOS order has hard disk last with two CD drives before it, the drive works just fine, and yes the 55aa is there.

As for SGD, I burned the iso on this laptop (Windows). I'm not sure if GAG is even installing onto my computer, I have to use a GAG CD in order to actually use it, but I'll reboot and see if i can boot to windows through it.




EDIT: OK i just booted up with GAG on a CD and then booted up windows, it was just fine. I also booted up Ubuntu through the GAG CD which brought me to the grub menu and opened windows from there, worked just fine too.

Thanks goodness for the GAG bootloader...I don't understand why grub from your root partition boots both OS, but grub doesn't function properly on your mbr?  For now, you don't really need the SGD, since GAG is working off the cd.
Herman's probably typing up a reply as I'm sending this...I'm sure he'll know what you might try next.

---

### Post by BriS on 2007-03-04
I was just about to restore my window's MBR, should I wait?

Hopefully it all works out, it could have something to do with Ultimate Edition, but it's supposed to edgy eft with extra programs.

Thanks for the help you guys

---

### Post by Herman on 2007-03-04
Try restoring the Windows bootloader's code to MBR then and let us know what happens. It shouldn't do any harm and might be a good test to give us some more clues as to the nature of the problem.
Sorry for the delayed response, other things are happening here at the same time.
Regards, Herman :)

---

### Post by BriS on 2007-03-04
I just restored windows MBR and it still doesn't boot up. (Ubuntu or windows) :( 

I used the mbrfix program, but I'll try again with the window's recovery console.

Oh, after I forgot to press a key, windows booted up normally (with the CD in there at least, like it did before)\

I fixed the mbr through window's recovery console and I still can't even boot up windows.

---

### Post by Herman on 2007-03-04
It looks like Ubuntu Ultimate Edition 1.2 is a third party project of some kind, known here in Ubuntu forums, I wasn't aware of it until now. It's related to this one,  [Ho ho ho, Ubuntu Christmas Edition?]("http://www.ubuntuforums.org/showthread.php?t=309704&highlight=Ubuntu+Ultimate+Edition+1.2")

---

### Post by BriS on 2007-03-04
I found it when I was on digg one day
[http://digg.com/linux_unix/Ubuntu_Ultimate_Edition_1_2_DVD_Now_Available_at_LinuxTracker_org](http://digg.com/linux_unix/Ubuntu_Ultimate_Edition_1_2_DVD_Now_Available_at_LinuxTracker_org)
So i decided it was an easy way to switch the Linux without feeling the emptiness of starting completely over. It's supposed to just be Ubuntu 6.1 with a bunch of pre-installed programs.

---

### Post by Herman on 2007-03-04
So you can boot via CDs but not directly through the hard disk's MBR right?

---

### Post by Herman on 2007-03-04
Sorry. I don't know what happened that time, double post.

---

### Post by BriS on 2007-03-04
I think so.

---

### Post by Herman on 2007-03-04
Alright then, can you post a look at your MBR here please?
```
sudo dd if=/dev/hda count=1 | hexdump -C
```Tell me about your hard drive cables too, have they got a blue plug at the motherboard end and a black plug for the master hard drive and a grey one for the slave? 
What jumper settings are you using?


[B] EDIT: Okay, forget that, how about configuring a different hard disk to boot from instead. You have three other MBRs you can use. Install Grub to a different one and just set your BIOS to boot whichever other hard disk you like. Simple! Why didn't I think of that earlier? :)
[/B]

---

### Post by BriS on 2007-03-04
1+0 records in
1+0 records out
00000000  fc 33 c0 8e d8 8e c0 be  00 7c bf 00 06 b9 00 01  |.3.......|......|
00000010  f3 a5 ea 2e 06 00 00 47  41 47 3a 20 90 00 10 00  |.......GAG: ....|
00000020  01 00 00 7c 00 00 00 00  00 00 00 00 00 00 bf 17  |...|............|
00000030  06 b4 0e bb 07 00 8a 05  3c 90 74 07 57 cd 10 5f  |........<.t.W.._|
00000040  47 eb ee bf 1d 06 80 3d  00 75 5f b4 02 cd 16 a9  |G......=.u_.....|
00000050  0f 00 74 56 33 c0 8e d8  8e c0 be be 7d b9 04 00  |..tV3.......}...|
00000060  80 3c 80 74 0a 83 c6 10  e2 f6 b0 32 e9 bb 00 b2  |.<.t.......2....|
00000070  80 b4 41 bb aa 55 cd 13  72 5b 81 fb 55 aa 75 55  |..A..U..r[..U.uU|
00000080  bf 26 06 8b 4c 08 89 0d  8b 4c 0a 89 4d 02 b4 42  |.&..L....L..M..B|
00000090  be 1e 06 bb 03 00 50 56  53 b2 80 cd 13 73 30 5b  |......PVS....s0[|
000000a0  5e 58 4b 75 f1 b0 31 e9  80 00 bb 1b 01 b8 00 10  |^XKu..1.........|
000000b0  8e d8 8e c0 b9 03 00 51  ba 80 00 b9 02 00 b4 02  |.......Q........|
000000c0  b0 3d 90 cd 13 73 46 59  e2 ed b0 31 eb 5c 90 5b  |.=...sFY...1.\.[|
000000d0  5e 58 eb 27 90 b2 80 8a  74 01 8b 4c 02 bb 03 00  |^X.'....t..L....|
000000e0  53 51 52 bb 00 7c b8 01  02 cd 13 73 0b 5a 59 5b  |SQR..|.....s.ZY[|
000000f0  4b 75 ed b0 31 eb 33 90  5a 59 5b 81 3e fe 7d 55  |Ku..1.3.ZY[.>.}U|
00000100  aa 74 05 b0 34 eb 23 90  ea 00 7c 00 00 b8 00 10  |.t..4.#...|.....|
00000110  8e c0 26 81 3e 1c 01 47  41 75 0d 26 83 3e 1e 01  |..&.>..GAu.&.>..|
00000120  47 75 05 ea 20 01 00 10  b0 33 bb 07 00 b4 0e cd  |Gu.. ....3......|
00000130  10 eb fe 56 5f 47 eb f0  eb fe 00 00 00 20 20 20  |...V_G.......   |
00000140  30 30 30 30 20 20 3f 3f  3f 30 00 00 00 30 00 38  |0000  ???0...0.8|
00000150  2c 02 2b 1f 08 32 32 00  00 00 30 20 00 00 00 30  |,.+..22...0 ...0|
00000160  30 30 10 10 0a 09 1c 00  20 00 00 01 02 03 04 05  |00...... .......|
00000170  06 07 08 09 0a 0b 0c 0d  0e 0f 00 00 00 00 20 20  |..............  |
00000180  20 30 30 30 30 00 00 3f  3f 3f 30 00 30 00 30 00  | 0000..???0.0.0.|
00000190  3f 00 00 3f 28 00 30 20  00 15 2f 00 79 01 dd 02  |?..?(.0 ../.y...|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 2c 44 63  d1 cf d1 cf 00 00 00 01  |.....,Dc........|
000001c0  01 00 07 fe ff ff 3f 00  00 00 b1 62 a9 03 80 fe  |......?....b....|
000001d0  ff ff 83 fe ff ff f0 62  a9 03 d0 92 97 05 00 fe  |.......b........|
000001e0  ff ff 82 fe ff ff c0 f5  40 09 01 ef 0f 00 00 00  |........@.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
512 bytes (512 B) copied, 3.2e-05 seconds, 16 MB/s



For my first two drives, the blue on is on the motherboard, the black one is on the main drive and the gray one on the slave. For my CD drive and other hard drive ( the second set) the black one is on the motherboard, the gray one is slave, and the blue one is on the cd drive.



I'm guessing i should install grub into my blank FAT32 drive...?

I rooted (hd0,0) then used setup (hd2), but when i do the find, (hd2) doesn't show up, nor can i boot, so I guess I'm doing something wrong. How do I install grub into a different dive?

---

### Post by Herman on 2007-03-04
Each hard disk drive has it's own Master Boot Record, but the BIOS only looks at the MBR in the hard disk it's set to look at.
Grub can be installed in any or all hard disk MBRs, and the BIOS in many computers can be set to look at whichever hard disks the user selects and sets in BIOS. If not, a different hard disk can be set as Primary Master by the way it is plugged in and jumpered.

[Re-install Grub with a GRUB shell eg; with Live CD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

To install grub to MBR, we normally do sudo grub (from a CD or hard disk installed system or any device that has grub) ```
sudo grub

``````
find /boot/grub/menu.lst
``````
root (hdx,y)
```where x is the drive number in grub's numbering and y is the partition number in grub's numbering where ther is a grub installation.
```
setup (hd0)
``` (hd0) would be the first disk's MBR, you would replace that with (hd1) for the second hard disk or (hd2) for the third or (hd3) for a fourth hard disk. (fd0) would be a floppy disk. And so on.
```
quit
```

---

### Post by BriS on 2007-03-04
I did that, but when i rooted the drive, it didn't respond with a  Filesystem type is ext2fs, partition type 0x83. But i continued anyway. I tried to find again, it only gave me (hd0,1). So i loaded up SGD, then when i rooted (hd0,1) it responded with the filesystem type and partition type, so i continued and again, setup (hd2). The computer still didn't boot. Am i supposed to change the groot in the menu.lst?

---

### Post by Herman on 2007-03-04
I presume you set the BIOS to boot the second hard drive?
It is beginning to seem like your problem might be somewhere in your CMOS or BIOS.

If it doesn't boot it could still be useful to know if you get a grub>_ prompt or still the same "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"  message too, so please let me know if things are changing like that. 
A grub>_ prompt would be a good sign, or a grub error code. When we see one of those we'll be getting close.

> The computer still didn't boot. Am i supposed to change the groot in the menu.lstNo, we won't need to change anything in menu.lst yet, not at this stage anyway. :)

---

### Post by BriS on 2007-03-04
I just followed the same steps you posted above through SGD again, It's booting right now, but it's just a small line flashing over and over, I assume I'll get the disk boot failure again (it usually takes a few minutes until it pops up).

Edit: Yeah, I got the disk boot failure.

---

### Post by Herman on 2007-03-04
Well it doesn't seem likely that anyone would have a MBR problem on more than one MBR, and besides, you showed your MBR with the 55aa sig clearly in the bottom corner. 

So it must be a problem in the BIOS (CMOS settings) or jumpers or cables then. I can't think what else it could be. :-k

It's up to you if you want to try another MBR or go back through your CMOS settings again and lastly maybe your jumpers and cables again.

---

### Post by BriS on 2007-03-04
Should my hd2 have the 55aa label too?

Never mind, it does.

What should I try doing with the MBR or CMOS?

Also, I don't think grub is installing correctly:

grub> find /boot/grub/menu.lst 
 (hd0,1)

Shouldn't it list hd2, as well?

---

### Post by Herman on 2007-03-04
> Should my hd2 have the 55aa label too? To be honest with you I'm not really sure, it's a data drive is it? I know for sure that drives with OS's installed have the 55aa, but I'm not sure about data drives, or how exactly the 55aa is written there. I wonder if grub puts it there? Possibly. That's a good question. I'll find out. :)

---

### Post by BriS on 2007-03-04
All of my data drives (hd1,hd2,sda0) have the 55aa label too, assuming I just change the drive in 

sudo dd if=/dev/hda count=1 | hexdump -C

---

### Post by Herman on 2007-03-04
>  Also, I don't think grub is installing correctly:
grub> find /boot/grub/menu.lst (hd0,1)
Shouldn't it list hd2, as well?No, that's okay, because it's finding your menu.lst file. That's really sort of a test to establish locations where grub exists from where we can install it *from*.

---

### Post by Herman on 2007-03-04
> All of my data drives (hd1,hd2,sda0) have the 55aa label too. Okay, good, they should all be seen as bootable devices by the BIOS then. 

By the way, you don't have any kind of MBR write-protect function running in your BIOS do you? Or antivirus? Those should be turned off if you do, because they prevent the MBR from being written to. But normally that would mean you'd still have the Windows bootloader code there, so that doesn;t make sense, but check anyway please.

---

### Post by BriS on 2007-03-04
I started off with a clean drive, so there cant be an antivirus or anything (unless windows set it up). So it could be the BIOS, I'll fiddle around with it.

I couldn't find anything that had to do with the MBR. The only thing that might even be a little related is the "No-Execute Memory Protect" which "when disabled, forces the NX feature flag to always return 0" This option has always been enabled, but I haven't the slightest clue what it does. There's also "Onboard LAN Function" and "Onboard LAN boot ROM." The function is on auto, but the boot rom is disabled, and again, I have no idea what they do.

---

### Post by Herman on 2007-03-04
Some BIOSes have an antivirus feature, It was invented for 'bootsector' viruses, there are not as many of those around nowadays, but I have read that some still exist. I think the BIOS antivirus is just something that 'write-protects' the MBR, so it can't be written to.
Occasionally it causes problems for people trying to install bootloader.

---

### Post by Herman on 2007-03-04
> I couldn't find anything that had to do with the MBR. The only thing that might even be a little related is the "No-Execute Memory Protect" which "when disabled, forces the NX feature flag to always return 0" This option has always been enabled, but I haven't the slightest clue what it does. There's also "Onboard LAN Function" and "Onboard LAN boot ROM." The function is on auto, but the boot rom is disabled, and again, I have no idea what they do.What BIOS do you have anyway? 
Here are a couple of links on CMOS settings, I'm not sure if they'll help, but maybe,

 [BIOS (Basic Input / Output System)]("http://webpages.charter.net/netw_1/bios.htm")

 
[The Definitive BIOS Optimisation Guide]("http://www.adriansrojakpot.com/Speed_Demonz/BIOS_Guide/BIOS_Guide_Index.htm")

---

### Post by BriS on 2007-03-04
I can't find anything really related to the MBR in the CMOS, so I don't think I have an antivirus or anything in there. But, when I try to save my GAG settings, that doesn't seem to save either.

I have Award Modular BIOS v6.00PG

---

### Post by Herman on 2007-03-04
**[[B]BIOS** - **Award** 6.00PG **BIOS** setup guidelines.doc]("http://www.answersthatwork.com/Download_Area/ATW_Library/Hardware_Maint/HW___6-Award_6.00PG_BIOS_setup_guidelines.pdf")

[/B]I don't see any anitvirus in there either, there's a 'virus warning'. It says that is a useless feature that should be turned off.

---

### Post by BriS on 2007-03-04
I don't even have some of the options that are listed in there, such as "virus  warning." Another thing, it tells me to press delete when I see the name of the BIOS, I press delete when i see "Gigabyte" (my motherboard's manufacturer). There's also a 5 year difference in the copyrights.

I went into the Dual BIOS utility though, "wide range protection" is already disabled, and that might be a virus protection. So i didn't really change anything yet.  :(

---

### Post by Herman on 2007-03-04
I guess that brings us back to your hard drive jumpers, are they set to 'cable select'?

---

### Post by BriS on 2007-03-04
Ummm, I don't know what jumpers are, or even what "cable select" is.

But like i said:


For my first two drives, the blue on is on the motherboard, the black one is on the main drive and the gray one on the slave. For my CD drive and other hard drive ( the second set) the black one is on the motherboard, the gray one is slave, and the blue one is on the cd drive.

Should i be flagging different drives as "boot" in gparted? Right now my Ubuntu partition is on "boot," should something else be, like my FAT32 drive or my window's partition?

---

### Post by Herman on 2007-03-04
I guess you would only need to know that if you installed your hard disks yourself. If you had them installed professionally then I hope whoever did that would probably know.
When we install hard disk drive, the old kind of IDE cables (wide, ribbon cables), have one end that plugs into the motherboard and usually two plugs to plug into a hard drive each or a hard drive and a CD drive maybe. One will be 'Master' and the other 'Slave' on the 'Primary' cable.
The other cable is called the secondary cable and it has a primary and a slave disk.  
The place where the cables are plugged into the MBR determines whether they are primary or secondary.
The jumper settings on the hard disks decide which hard disk on each cable is master and which one is slave.
'Jumpers' are like little plastic rectangular caps that fit over two adjacent pins in a recess in the end of the disk's case somewhere, usually near where the cables plug in. The jumpers have metal inside that makes an electrical contact between the two pins. Depending which two pins the jumper is set on, it sets the hard disk as 'master', 'slave', or in 'cable select' mode.

The other thing to know is that there are cable-select IDE cables, and ordinary IDE cables. Ordinary ones need the jumpers set to 'master' or 'slave'. These have black plugs, or plugs that are all the same color.
'Cable select' IDE cables have a blue plug for the motherboard, a black plug for the master disk, and a grey plug for the slave. The jumpers should be set to 'cable select' if those cables are used.

link:[Guide to Installing **IDE** devices]("http://freepctech.com/pc/001/installing_ide_devices.shtml")

video link:  [isdn21.asf]("http://www.quepublishing.com/content/downloads/upgrading/videos/High/isdn21.asf")

So your jumpers should be set to 'cable select' for your first two drives.
Are you sure your other cable is okay when the blue plug is in the CD drive? Will the blue plug fit in the motherboard? Shouldn't the black one be in one of the drives? :)

---

### Post by BriS on 2007-03-04
> **Herman said:**
> "]isdn21.asf[/URL]

So your jumpers should be set to 'cable select' for your first two drives.
Are you sure your other cable is okay when the blue plug is in the CD drive? Will the blue plug fit in the motherboard? Shouldn't the black one be in one of the drives? :)

I'm not entirely sure it's OK, but the CD drive and the hard drive work just fine. And yes, the blue one should be on the motherboard, but i don't have an expansion bay, so i had to figure out a way to go from the motherboard to the drive then all the way up to the CD drive, and of course, that meant plugging it all in backwards. It works though. Again, I'm not completely sure, but i do think all of the drives are still on the manufacturer's setting, whatever that may be.

---

### Post by Herman on 2007-03-04
On the computer manufacturer's settings, meaning they were already that way since the computer was new? 

Or the hard disk drive manufacturer's settings, (if you installed them yourself), usually meaning they would both be set as 'master'?

I'm not really sure if having the jumpers wrong will cause the problems you're complaining of or not, but we already checked about everything else, so after this I'm out of ideas for a while....

Regards, Herman :)

---

### Post by BriS on 2007-03-04
I don't think the jumper has to do with the problem, all of the drives are on the correct master / slave in the BIOS. I'll play around more with everything in a few hours, it's 5:30am and i think I'll head off to bed now. Thanks for all the help though, I appreciate you doing this for me. I'll fiddle around with it after some sleep, good night.

---

### Post by Herman on 2007-03-04
Okay, it's well past time for me to have a sleep for a while too, I'll be around again later sometime. It certianly does seem like a mystery, I'm interested to find out what the problem turns out to be in the end.

Bye for now, Regards, Herman :)

---

### Post by confused57 on 2007-03-04
> **Herman said:**
> Okay, good, they should all be seen as bootable devices by the BIOS then. 

By the way, you don't have any kind of MBR write-protect function running in your BIOS do you? Or antivirus? Those should be turned off if you do, because they prevent the MBR from being written to. But normally that would mean you'd still have the Windows bootloader code there, so that doesn;t make sense, but check anyway please.
Excellent suggestion...know you guys are sleeping, went to bed at 4:00 am here(several hours ago)...here's someone whose bios actually had a function to repair the mbr:
[http://www.ubuntuforums.org/showthread.php?t=368012](http://www.ubuntuforums.org/showthread.php?t=368012)

---

### Post by BriS on 2007-03-04
Well, I looked through the manual for my motherboard, there was an option called "Halt On" which was enabled, but even after I turned it off and reinstalled normal ubuntu (not ultimate) my computer still doesn't boot up by itself. So far, I think the problem is with the MBR, howcome GAG isn't installing when I "save to harddisk"?

---

### Post by BriS on 2007-03-04
I just completely formatted my drive, and reinstalled windows only. But I can't even boot that by itself now. I think grub or gag made my computer unbootable. I already tried having window's setup repair itself, but I don't know what to do now.

---

### Post by Herman on 2007-03-04
> So far, I think the problem is with the MBR, howcome GAG isn't installing when I "save to harddisk"?
 GAG did install to hard disk, look, this is a copy of the same MBR you posted a few pages back, it has GAG in it. :)

```
 00000000  fc 33 c0 8e d8 8e c0 be  00 7c bf 00 06 b9 00 01  |.3.......|......|
00000010  f3 a5 ea 2e 06 00 00 47  41 47 3a 20 90 00 10 00  |.......GAG: ....|
00000020  01 00 00 7c 00 00 00 00  00 00 00 00 00 00 bf 17  |...|............|
00000030  06 b4 0e bb 07 00 8a 05  3c 90 74 07 57 cd 10 5f  |........<.t.W.._|
00000040  47 eb ee bf 1d 06 80 3d  00 75 5f b4 02 cd 16 a9  |G......=.u_.....|
00000050  0f 00 74 56 33 c0 8e d8  8e c0 be be 7d b9 04 00  |..tV3.......}...|
00000060  80 3c 80 74 0a 83 c6 10  e2 f6 b0 32 e9 bb 00 b2  |.<.t.......2....|
00000070  80 b4 41 bb aa 55 cd 13  72 5b 81 fb 55 aa 75 55  |..A..U..r[..U.uU|
00000080  bf 26 06 8b 4c 08 89 0d  8b 4c 0a 89 4d 02 b4 42  |.&..L....L..M..B|
00000090  be 1e 06 bb 03 00 50 56  53 b2 80 cd 13 73 30 5b  |......PVS....s0[|
000000a0  5e 58 4b 75 f1 b0 31 e9  80 00 bb 1b 01 b8 00 10  |^XKu..1.........|
000000b0  8e d8 8e c0 b9 03 00 51  ba 80 00 b9 02 00 b4 02  |.......Q........|
000000c0  b0 3d 90 cd 13 73 46 59  e2 ed b0 31 eb 5c 90 5b  |.=...sFY...1.\.[|
000000d0  5e 58 eb 27 90 b2 80 8a  74 01 8b 4c 02 bb 03 00  |^X.'....t..L....|
000000e0  53 51 52 bb 00 7c b8 01  02 cd 13 73 0b 5a 59 5b  |SQR..|.....s.ZY[|
000000f0  4b 75 ed b0 31 eb 33 90  5a 59 5b 81 3e fe 7d 55  |Ku..1.3.ZY[.>.}U|
00000100  aa 74 05 b0 34 eb 23 90  ea 00 7c 00 00 b8 00 10  |.t..4.#...|.....|
00000110  8e c0 26 81 3e 1c 01 47  41 75 0d 26 83 3e 1e 01  |..&.>..GAu.&.>..|
00000120  47 75 05 ea 20 01 00 10  b0 33 bb 07 00 b4 0e cd  |Gu.. ....3......|
00000130  10 eb fe 56 5f 47 eb f0  eb fe 00 00 00 20 20 20  |...V_G.......   |
00000140  30 30 30 30 20 20 3f 3f  3f 30 00 00 00 30 00 38  |0000  ???0...0.8|
00000150  2c 02 2b 1f 08 32 32 00  00 00 30 20 00 00 00 30  |,.+..22...0 ...0|
00000160  30 30 10 10 0a 09 1c 00  20 00 00 01 02 03 04 05  |00...... .......|
00000170  06 07 08 09 0a 0b 0c 0d  0e 0f 00 00 00 00 20 20  |..............  |
00000180  20 30 30 30 30 00 00 3f  3f 3f 30 00 30 00 30 00  | 0000..???0.0.0.|
00000190  3f 00 00 3f 28 00 30 20  00 15 2f 00 79 01 dd 02  |?..?(.0 ../.y...|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 2c 44 63  d1 cf d1 cf 00 00 00 01  |.....,Dc........|
000001c0  01 00 07 fe ff ff 3f 00  00 00 b1 62 a9 03 80 fe  |......?....b....|
000001d0  ff ff 83 fe ff ff f0 62  a9 03 d0 92 97 05 00 fe  |.......b........|
000001e0  ff ff 82 fe ff ff c0 f5  40 09 01 ef 0f 00 00 00  |........@.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```
> I just completely formatted my drive, and reinstalled windows only. But I can't even boot that by itself now. I think grub or gag made my computer unbootable. I already tried having window's setup repair itself, but I don't know what to do now.Well I don't think so, I thing there is something wrong in your BIOS and cabling and jumper settings. I think you should do those properly before you go to any more trouble. 
A new (longer) cable so you won't have to plug that other one is backwards would only cost a couple of dollars. Really it's not fair to blame the software if you don't have the hardware set up right to begin with.

An idea I had while I was working this morning is to try to boot from the other two hard disks that we didn't try yet too. We only tried two out of the four disks. Possibly we tried the wrong two. Just a suggestion. 

Keep trying, be patient, don't give up. 
Regards, Herman :)

---

### Post by BriS on 2007-03-04
It's strange though, I had Ubuntu for an entire week with no problems booting up or anything, but when I tried to set up a dual boot system, everything seemed to go crazy. I'll keep trying to get it working, but I have school tomorrow, so things may have to wait until next weekend. In any case, if things don't work out, I'll probably get over gaming by the time I'm in the next few years or so (I'm only in high school). 

I'll take off my CD drive and plug the IDE cables into the right spot on my hard drive and we'll see what happens.

EDIT: i think that just solved everything. Grub still doesn't load up (considering i uninstalled ubuntu) but at least i get a grub error. I'll install ubuntu again, and it'll probably work, so we'll see. Thanks for the help Herman. I'll get on it right now, and see. :)

---

### Post by lsutiger on 2007-03-04
a) Reset your BIOS (look at your manual on how to do that)
b) Select a single drive, make sure it is set to master or cable select, and disconnect all other hard discs. Connect to only one cd drive if you have multiples.
c) Install Linux..after done, can you boot?
d) If so, select the slave drive for that IDE connection. Make sure it is either set to slave or cable select if you choose cable select on the first drive.
If that doesn't work, I don't know what to tell you other than you have a hardware problem that arose while/after you did dual boot ( it happens sometimes..I do tech work/programming for a pretty large firm and run across these problems alot)
Since you wiped your hard drive it should have worked. I think there may be a problem with what drive(s) is being selected for bootup. Also turn of boot from LAN. That is where the lag is coming from, possibly, between turning on the computer and DISK BOOT FAILURE.
IE - my BIOS has a selection for what device to look at for boot up ( Hard drive/cd rom/external device/lan, etc) and then there is a section to define which item in each class to look at to boot from. So if I have multiple hard drives (which I do) I need to tell the computer which hard drive to boot from. But it is a tricky BIOS.
Just some ideas. Wish you luck!
I will be watching this thread to see your progress.

---

### Post by BriS on 2007-03-05
Well, i reinstalled Windows and Ubuntu, but when i booted up, Grub loaded 1.5 then when it tried to load the next stage, i got Error 22. However, I can still get through if i use GAG on a CD.


EDIT: OK no more error 22, but now NTLDR is missing


EDIT again: OK, fixed it, and now grub loads! It works you guys, it actually works! Thanks for all the help everyone, sorry for bothering you guys for so long ^^;

---

### Post by rsambuca on 2007-03-05
Wow!  Good stuff.  Can you let us know what you did to finally get it working?

---

### Post by lsutiger on 2007-03-05
you have some steps ahead of you...keep me updated! I am very new to Linux like you, but am a 20 year vet to Microsoft. Tell me what you did and what worked.

---

### Post by confused57 on 2007-03-05
> **BriS said:**
> Well, i reinstalled Windows and Ubuntu, but when i booted up, Grub loaded 1.5 then when it tried to load the next stage, i got Error 22. However, I can still get through if i use GAG on a CD.


EDIT: OK no more error 22, but now NTLDR is missing


EDIT again: OK, fixed it, and now grub loads! It works you guys, it actually works! Thanks for all the help everyone, sorry for bothering you guys for so long ^^;
Great job, don't know if I could have persevered as you did...did you install GAG to the mbr or grub & how did you correct the Error 22?  

Herman is a "gold mine" of information & he explains things in a way that even I understand...he's like E.F. Hutton, when he speaks, everybody listens...of course, you're probably too young to know about E.F. Hutton.

---

### Post by BriS on 2007-03-05
I have no clue what happened to GAG. As for grub, that's installed on the Ubuntu partition, and i fixed the Error 22 by restoring window's MBR.

Oh, and yes, i have no idea who E.F. Hutton is. But Herman is good... kudos to him

---

### Post by confused57 on 2007-03-05
> **BriS said:**
> I have no clue what happened to GAG. As for grub, that's installed on the Ubuntu partition, and i fixed the Error 22 by restoring window's MBR.

Oh, and yes, i have no idea who E.F. Hutton is. But Herman is good... kudos to him

Thanks for the update...thought you were much too young for E.F. Hutton, it was a stock trading firm and their commercials showed everybody stopping what they were doing and turn an ear to hear what they suggested as a potentially good stock investment.

---

### Post by mahiyar on 2007-03-05
I have been following this post closely, because I plan to add SATA drive to my existing IDE dual boot. Where SATA will have Ubuntu install and IDE will have WIn XP. I'am still not clear as to what steps are correctly done to avoid the same problems of Bris. But correct me if I'am wrong when I cull out the following steps for my install.
 
1) Remove the ide drive currently in use.
2) Attach the SATA drive, install Ubuntu and GRUB to MBR.
3) Remove SATA drive.
4) Attach the old IDE drive.
5) Reinstall windows or use FIXMBR command so that ntldr boot loader is in MBR of ide.
6) Reattach both SATA and IDE drives.
7) Make SATA drive the primary boot device from BIOS.
8) On restarting I expect the computer to boot into Ubuntu.
9) Make changes in menu.lst file and "map" file using fdisk -lh command, so that windows is chain loaded from Grub menu.
 
Now it is all up to you experts to tell me that the procedure I have devised is sufficient enough or not. Thanks.

---

### Post by confused57 on 2007-03-05
> **mahiyar said:**
> I have been following this post closely, because I plan to add SATA drive to my existing IDE dual boot. Where SATA will have Ubuntu install and IDE will have WIn XP. I'am still not clear as to what steps are correctly done to avoid the same problems of Bris. But correct me if I'am wrong when I cull out the following steps for my install.
 
1) Remove the ide drive currently in use.
2) Attach the SATA drive, install Ubuntu and GRUB to MBR.
3) Remove SATA drive.
4) Attach the old IDE drive.
5) Reinstall windows or use FIXMBR command so that ntldr boot loader is in MBR of ide.
6) Reattach both SATA and IDE drives.
7) Make SATA drive the primary boot device from BIOS.
8) On restarting I expect the computer to boot into Ubuntu.
9) Make changes in menu.lst file and "map" file using fdisk -lh command, so that windows is chain loaded from Grub menu.
 
Now it is all up to you experts to tell me that the procedure I have devised is sufficient enough or not. Thanks.

You're on the right path, but a couple of the steps you mentioned are unnecessary.  I slightly modified what you had:

1) Remove the ide drive currently in use.
2) Attach the SATA drive, install Ubuntu and GRUB to MBR.
3) Attach the old IDE drive.
4) Make SATA drive the primary boot device from BIOS.
On restarting I expect the computer to boot into Ubuntu.
5) Make changes in menu.lst file,  so that windows is chain loaded from Grub menu, use fdisk -lu command to determine partitions before modifying menu.lst.

You could actually do step 4(make SATA drive first hard drive in boot order) as step 1(actually, you'd need to install the SATA drive first).

You might want to read over this thread for a possible entry to boot Windows & how to edit your menu.lst:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by mahiyar on 2007-03-05
Thanks confused57. Now I'am confident of doing the project, and as a first step of buying the SATA drive.

---

