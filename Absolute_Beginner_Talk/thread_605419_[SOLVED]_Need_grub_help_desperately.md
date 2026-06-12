---
title: "[SOLVED] Need grub help desperately"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by bumanie on 2007-11-07
I need help to restore grub. I have tried 
find /boot/grub/stage1 - output (hd0,4)
root (hd0,4)
setup (hd0)
quit
This has not fixed anything.
The only way I can boot the computer is via super grub disk, however it doesn't seem to be able to fix grub (I have tried the various things such as fix grub, fix mbr etc).
I have dual boot xp and feisty. Everything was fine until I installed a slave drive and tried to install gutsy gibbon onto it. (As far as I can ascertain,  the slave drive is installed correctly ie jumper sttings etc and is recognised in BIOS with correct boot sequence etc). Ever since trying the gutsy gibbon install, booting has not worked, however once booted via super grub disc, the OS's work fine. I have uninstalled gutsy and deleted all partitions on the slave drive with g-parted live cd.
If someone can help, I will post any command line output you need. I did a search in terminal for vmlinuz and it returned an error 15. Can someone please help.
Running an amd 2600+ athlon box with 1 gig of ram and a nvidia geforce 4 mx 4000 8x agp card.

---

### Post by dcstar on 2007-11-07
> **bumanie said:**
> I need help to restore grub. I have tried 
find /boot/grub/stage1 - output (hd0,4)
root (hd0,4)
setup (hd0)
quit
This has not fixed anything.
The only way I can boot the computer is via super grub disk, however it doesn't seem to be able to fix grub (I have tried the various things such as fix grub, fix mbr etc).
I have dual boot xp and feisty. Everything was fine until I installed a slave drive and tried to install gutsy gibbon onto it. (As far as I can ascertain,  the slave drive is installed correctly ie jumper sttings etc and is recognised in BIOS with correct boot sequence etc). Ever since trying the gutsy gibbon install, booting has not worked, however once booted via super grub disc, the OS's work fine. I have uninstalled gutsy and deleted all partitions on the slave drive with g-parted live cd.
If someone can help, I will post any command line output you need. I did a search in terminal for vmlinuz and it returned an error 15. Can someone please help.
Running an amd 2600+ athlon box with 1 gig of ram and a nvidia geforce 4 mx 4000 8x agp card.

Tell people what "booting has not worked" actually means, tell us exactly what actually happens.

---

### Post by ecionci on 2007-11-07
Pardon, but we can't tell how much linux experience you have. Anyhow, do you do this:
type grub
grub> find /boot/grub/stage1
grub> root (hd0,4)
Filesystem type is ext3, etc. (does it say this?) if so then type:
grub> root (hd0,4)
grub> setup (hd0,4) next it should check if boot, grub and stage 1 exist
and tell you if it has indeed succeded. It will put grub boot loader on MBR.

More help can be found at [http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

By the way, don't we have rules about spamming? See post above.

---

### Post by TeaSwigger on 2007-11-07
Pardon a possibly silly question, but just to be clear, you are attempting to fix the GRUB which the attempted Gutsy installed on the Slave drive? Did you have it install to the MBR of the Master? Wouldn't it then supposed to point to the GRUB on hd1,x? Can you boot from a slave drive? Thought it had to be master, but admittedly I'm no expert at the best of times and am sleepy right now :p.

---

### Post by bumanie on 2007-11-07
Sorry, I should have mentioned it was a grub error 22.
It didn't boot from either drive, just came up with the grub error at grub stage 1.5. The instructions ecionci sent still get the grub 22 error and there is no file type mentioned after the grub> root (hd0,4) he mentions in his post.

---

### Post by bumanie on 2007-11-07
I unfortunately have to go to work very soon.
Here is the result of my fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11090    89080393+   7  HPFS/NTFS
/dev/hda2           11091       11214      996030   82  Linux swap / Solaris
/dev/hda4           11215       15299    32812762+   5  Extended
/dev/hda5   *       11215       15299    32812731   83  Linux

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

The grub gedit /boot/menu.lst is blank!!!
Device map says (hd0)
If anyone has any suggestions after reading this output, please make suggestions. I will check while at work, but won't be able to do anything until I return tomorrow morning.
I however think I will have to bite the bullet and do a complete reinstall of both OS's.

---

### Post by bumanie on 2007-11-08
I will restate my major problems and how they came about.  This has been a drawn out issue that I hope some knowledgeable person can help me with.
Facts:
1) I have an amd 2600+ athlon, !gig ram, nvidia geforce 4 mx 4000 8x agp
2) I have a dual boot xp and feisty on master drive 
3) Everything was fine until I added a slave drive and attempted to install gutsy gibbon onto it
4) As soon as I installed gutsy, I immediately got grub error 17 and later grub error 22 at stage 1.5 of grub booting
5) I deleted the partitions on slave drive, thus removing gutsy
6) Grub is now mucked up. I continue to get grub error 22 at stage 1.5
7) Can only boot into an OS via super grub disk
8) Super grub disk says it has been successful at restoring both xp and feisty, but grub error 22 continues, so I have to continue booting via super grub disk. Once booted both xp and feisty work perfectly. I am reasonably sure the problem is with the bootloader.
9) My last post states that I have a blank grub menu.lst - I did a system recovery and now I have a grub menu.lst 
If anyone thinks they may be able to help, please reply with instructions of things you would me to post. Thanking anyone in advance.

---

### Post by philinux on 2007-11-08
From the live cd can you not use the backup of menu.lst to get something going?

---

### Post by bumanie on 2007-11-08
Nothing I have tried so far has worked. I have not tried the grub menu.lst via the live cd as I only just found it again. Yesterday the gedit box was blank. Do you really think the live cd method will work? I will give it a go and get back to you shortly. Thanks for answering.

---

### Post by philinux on 2007-11-08
Unless you can get access to the backup of menu.lst some other way?

If you've got a backup at least it will have all the boot up commands you need.

---

### Post by bumanie on 2007-11-08
Unfortunately, booting up with the live cd of feisty has not changed anything. I typed sudo gedit /boot/grub/menu.lst-backup and came up blank. Any other suggestions? Do you know anything about editing the menu.lst?

---

### Post by ByteJuggler on 2007-11-08
> **bumanie said:**
> I unfortunately have to go to work very soon.
Here is the result of my fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11090    89080393+   7  HPFS/NTFS
/dev/hda2           11091       11214      996030   82  Linux swap / Solaris
/dev/hda4           11215       15299    32812762+   5  Extended
/dev/hda5   *       11215       15299    32812731   83  Linux

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

The grub gedit /boot/menu.lst is blank!!!
Device map says (hd0)
If anyone has any suggestions after reading this output, please make suggestions. I will check while at work, but won't be able to do anything until I return tomorrow morning.
I however think I will have to bite the bullet and do a complete reinstall of both OS's.

OK I'll have a stab at helping you but I'll have to test some of this at home which will take some time.  But, off the cuff I note you have both hda1 and hda5 marked as bootable, IIRC (and I could be wrong here) Window's boot loader doesn't like it when 2 partitions are marked as bootable, and the Linux boot loaders don't tend to care IIRC, so you might want to take the bootable flag off the Linux partition for now so there's only one bootable partition so Windows should be happy(er) You can use "sudo cfdisk" command to do that easily.

Also, your device map is empty/wrong, which won't help matters, we'll have to get that recreated.  That said, you can try running "sudo update-grub" which theoretically will regenerate your menu.lst etc.  You can in the meantime try these 2 things and see if it makes any difference and post back.  I will try to set up appropriate files for you to use this end tonight and get back to you.  You really should not need to reinstall both OS's!

---

### Post by philinux on 2007-11-08
> **bumanie said:**
> Unfortunately, booting up with the live cd of feisty has not changed anything. I typed sudo gedit /boot/grub/menu.lst-backup and came up blank. Any other suggestions? Do you know anything about editing the menu.lst?


It should be sudo gedit /boot/grub/menu.lst.backup not -backup

---

### Post by bumanie on 2007-11-08
Bytejuggler you are the first one to give me some of getting this sorted out. I agree that I shouldn't have to reinstall either OS, that was a sign of desperation/frustration that I was not able to find any instructions that helped with this particular problem. I will try the 2 things you have suggested and get back to you. Appreciate the help.

---

### Post by gn2 on 2007-11-08
Have you tried to simply re-install Grub?

This can be done from a live CD: [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

Lots more booting an installing info on the excellent Hernanzone website, link in my sig.
Well worth bookmarking.

---

### Post by ByteJuggler on 2007-11-08
> **bumanie said:**
> I will try the 2 things you have suggested and get back to you. Appreciate the help.

Just to note, I actually corrected the one command I posted as I had made a typo, and also that I'm not guaranteeing anything yet - those suggestions are just off the top of my head, as I say I'll have to spend a little more time when I'm home tonight to craft and test the commands/files I think you'll need (so please be patient.) :-)

---

### Post by bumanie on 2007-11-08
To gn2 - yes I have read herman's site and followed those commands. For some reason the file system does not appear after typing in the (hd0,4) command, thus it has not worked. That is the first thing I tried because I had saved grub once before via that method.
Philinux, I will try the live cd again if bytejuggler's two suggestions don't work. Thanks again to everyone. This has been an ongoing issue for two weeks (had a previous post related to this) and this is the first time I have received any hope of solving the problem. Thanks again.

---

### Post by philinux on 2007-11-08
Hope it goes well, if the backup is there at least you'll see what it looked like before it got blanked.

---

### Post by meierfra on 2007-11-08
Never mind.

---

### Post by bumanie on 2007-11-08
meierfra I think you were the one who suggested I disconnect the slave drive. I did that and that is why I was gone for so long. Upon trying to reboot, the system check took about 5 minutes and I had to do this 3- or 4 times before super grub disk would boot the system. I don't know why the system is now booting so slowly now that the slave drive is unplugged. I am now not sure whether it was the right thing to do or not. Any way it seems that you got sick of waiting. Sorry.
Any way, I tried bytejuggler's suggestions and neither have worked. I will await further suggestions. In the meantime I may see if I can get the slave drive reconnected and see whether that increases the system check speed.

---

### Post by bumanie on 2007-11-08
What I have done recently. 
1) Followed philinux's instructions, unfortunately I drew a blank there
2) Followed bytejuggler's 2 suggestions, continue to get grub error 22
3) Unplugged slave drive as meierfra (I think) suggested, system startup very slow. I therefore repowered slave drive and everything re startup back to normal.
Awaiting further suggestions.
I am getting tired though it nearly 3 am here!

---

### Post by bumanie on 2007-11-08
"I will try to set up appropriate files for you to use this end tonight and get back to you."
To bytjuggler thanks for  your help. I look forward to hearing from you, however your night is my day. I'm in Australia you're in th UK. I need to sleep now. I will check when I wake up. just for interest here is the grub menu.lst I found earlier after not having one at all yesterday (or at least it had stored itself somewhere invisible to me).

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=d8ed1617-8917-471b-b114-f158568e08c3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d8ed1617-8917-471b-b114-f158568e08c3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d8ed1617-8917-471b-b114-f158568e08c3 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d8ed1617-8917-471b-b114-f158568e08c3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d8ed1617-8917-471b-b114-f158568e08c3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Thanks again. Any idea why the system check would take 5 minutes when the slave was unplugged?
Don't know where those smiley faces came from.

---

### Post by meierfra on 2007-11-08
> Any way it seems that you got sick of waiting.

No, After reading the thread more carefully  I realized that I didn't really understand what was going on and that my suggestion probably wouldn't lead to anything.  I checked your profile, and concluded  from the  "last activity" time that you hadn't looked at my post yet (Seems I got that wrong) So I removed my post, but I have to admit,  replacing it by "never mind"  was a poor choice of words.

---

### Post by ByteJuggler on 2007-11-08
OK, I was actually intending to set up a virtual machine to exactly match your setup, but hadn't looked closely enough at your setup before having installed the machine with both XP and Feisty.  So only then I noticed the partitioning order is subtly different from yours, so hence the transcript for (re)installing grub will not directly apply.  So, with that warning/apology up front, here is the unmodified transcript from my VM for installing grub.  Below my unmodified transcript I will give my hand modified guess what it should be for you:

```
walterp@VM1:~$ sudo -s
root@VM1:~# fdisk -lu

Disk /dev/hda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63     6811559     3405748+   7  HPFS/NTFS
/dev/hda2   *     6811560    16225649     4707045   83  Linux
/dev/hda3        16225650    16771859      273105    5  Extended
/dev/hda5        16225713    16771859      273073+  82  Linux swap / Solaris
root@VM1:~# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.20-15-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,1)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

grub> quit

root@VM1:~# exit

```

So as you can see, /dev/hda2 (which in grub-speak is (hd0,1) ) corresponds to the linux partition, which IS marked as bootable.  And Windows is NOT marked as bootable. (So, I got slightly confused about that earlier in the thread.)  Anyway, the above is theoretically all that should be needed to reinstall grub.  

OK, now I'll redo this again properly tomorrow if need be, exactly matching your Primary disk partition layout, so the files etc. can be just copied from my working system.  For now (as it's 01:54 am and I'm tired) I'll just manually update the transcipt to match what you should see when you run it on your system (modified lines in Bold.)  Please note, to use this, you must be booted into your existing installation, *_not _booted off a liveCD!*

```
walterp@VM1:~$ sudo -s
root@VM1:~# fdisk -lu

Disk /dev/hda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63     6811559     3405748+   7  HPFS/NTFS
/dev/hda2        16225713    16771859      273073+  82  Linux swap / Solaris
/dev/hda3        16225650    16771859      273105    5  Extended
/dev/hda5   *     6811560    16225649     4707045   83  Linux
root@VM1:~# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

**Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y**

Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.20-15-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> **root (hd0,4)**

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p **(hd0,4)**/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.


grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd0)1+17 p **(hd0,4)**/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

grub> quit

root@VM1:~# exit

```

Note: I added in a command to install the boot loader onto (hd1) as well, that's your slave drive.  The idea is that if your BIOS is for some reason using that as your initial boot disk (to get the MBR from), it should then still work.  (Installing the boot loader on the slave disk wont harm anything else.)

BTW, after the "update-grub" above you should already have a "menu.lst", if you don't then something else is going on...  Also make sure you mark the Linux partition (hda4 in your case) as Active/Bootable as shown.  

Once again, apologies for not being more complete/exacting, I'll redo this tomorrow with the proper partition layouts and then post the exact contents of all the files and commands issued.

---

### Post by bumanie on 2007-11-09
Bytejuggler, you seem to have done lots of work. Did you notice that I have found a grub menu.lst and posted it. I assume this may be helpful in tracking down the exact problem. Setting up a virtual system to emulate mine is a great idea - but lots of work for you. Anyway I appreciate it very much. I will await your updated partition layout with commands etc. Also no need to apologise for anything you may not have done perfectly, you are being a great help and I am confident this will be sorted out soon. Thanks again.

---

### Post by adrian15 on 2007-11-15
> **bumanie said:**
> 
8) Super grub disk says it has been successful at restoring both xp and feisty, but grub error 22 continues, so I have to continue booting via super grub disk. Once booted both xp and feisty work perfectly. I am reasonably sure the problem is with the bootloader.

The problem that you have is that the hard disk boot order is not the same when you boot from a cdrom (super grub disk) than when you boot from the hard disk.

Try the latest Super Grub Disk version (currently 0.9670) and its Easy Liveswap option.
Once the Easy Liveswap option has been run go to GNU/LINUX -> Fix Boot of Linux.

This will let you recover your grub boot but maybe when rebooting it leads to an error 15 error.

If you have the error 15 you will have to chroot to your system from a live cd, run ```
mount -a
``` edit menu.lst so that:

```

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

```

reads:

```

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

```

Edit /boot/grub/device.map so that the drive assignation is correct (probably your current setup but reversed although I am not sure) and then run:

```

update-grub.

```

Exit from the chroot. Umount the partitions and reboot and you should not see the error 15.

If it seems not to work, please paste here the /boot/grub/device.map so that I can accurately help you.

In my example you are supposed to have both hard disks connected into your computer.

adrian15

---

### Post by bumanie on 2007-11-15
Thanks Adrian15. I guess I should have marked this as solved. After it was dormant fro 3-4 days I rehashed a new thread, using this as the basis for the new thread. It is now solved, I marked the new  thread as solved and forgot all about this one. Sorry.
Newer thread is here if you would like to look.
[http://ubuntuforums.org/showthread.php?t=610852](http://ubuntuforums.org/showthread.php?t=610852)
Thnaks anyway. And I will mark this as solved right now.

---

