---
title: "boot problem - error 17"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by rewolf on 2007-03-30
I currently have WinXP installed on my PC as my OS. I have a AMD64 X2 processor (don't know if that influences anything)
My problem is as follows:
I installed ubuntu 6.06 from the play disc, onto another hard-drive.  When i restart after the installation, it appears as though ubuntu tries to boot, but b4 anything happens, a
"error 17" is displayed.
thats all.

What does that mean, and how can i get ubuntu to work?

To get back into windows i had to reinsert my XP disc - go to repair - and say FIXMBR, because the boot record had been changed - argh.  ive tried installing twice.

thanks for the help
--------------
-rewolf

---

### Post by johnnymac on 2007-03-30
So basically you didn't have your grub configuration done correctly.  This happens when you set u your boot partition and grub can't recognize it.  If you can get back in you can modify your grub configuration file to fix it (/boot/grub/menu.lst).

The issue is probably due to you not specifying the correct partition - to - grub entry or you didn't specify your grub to be where the MBR sits.

GL...

---

### Post by rewolf on 2007-03-30
thanx very much...
im so lost with this linux stuff...

so where can i find info on how to configure grub correctly etc?... whatever grub is.
lol - i hate being so dumb!

thanx so soo much

-----------------
-rewolf

---

### Post by Maestro23 on 2007-03-30
Open a terminal and type:

> cat /boot/grub/menu.lst (lower case L)

Copy/Paste the output here.

---

### Post by th3void on 2007-03-30
I am actually having a similar problem.  I was hoping you might be able to help me as well.  XP on one hard drive and tried to install 6.10 on the other.  I was able to boot off of the LiveCD but 

cat /boot/grub/menu.lst (lower case L)

produces

ubuntu@ubuntu:/boot$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:/boot$ 

Any ideas?

---

### Post by Maestro23 on 2007-03-30
> **th3void said:**
> I am actually having a similar problem.  I was hoping you might be able to help me as well.  XP on one hard drive and tried to install 6.10 on the other.  I was able to boot off of the LiveCD but 

cat /boot/grub/menu.lst (lower case L)

produces

ubuntu@ubuntu:/boot$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:/boot$ 

Any ideas?

At your command prompt, you should just type: 

> cat /boot/grub/menu.lst

---

### Post by th3void on 2007-03-30
Yup.

Might this have something to do with it?  No GRUB folder...  at least not that I can tell.

ubuntu@ubuntu:/boot$ ls -l
total 2755
-rw-r--r-- 1 root root  285604 2006-10-13 19:09 abi-2.6.17-10-generic
-rw-r--r-- 1 root root   74645 2006-10-13 16:13 config-2.6.17-10-generic
-rw-r--r-- 1 root root   94600 2006-10-20 11:44 memtest86+.bin
-rw-r--r-- 1 root root  728690 2006-10-13 19:09 System.map-2.6.17-10-generic
-rw-r--r-- 1 root root 1636681 2006-10-13 19:09 vmlinuz-2.6.17-10-generic
ubuntu@ubuntu:/boot$ pwd
/boot
ubuntu@ubuntu:/boot$ 

I know enough about Linux to get around, but not how to fix this :\

---

### Post by th3void on 2007-03-30
And, yes, I was only typing

cat /boot/grub/menu.lst

at the command prompt.

---

### Post by th3void on 2007-03-30
Could the reason I can't find /boot/grub/menu.lst be because I am running off of the LiveCD currently?  Do I need to mount the partition that GRUB was installed onto?

---

### Post by alien21010 on 2007-03-30
> **th3void said:**
> Could the reason I can't find /boot/grub/menu.lst be because I am running off of the LiveCD currently?  Do I need to mount the partition that GRUB was installed onto?


Yep, you need to mount your /boot partition while you are in the LiveCD environment.  

In order to fix this problem we need three things:

1- The output of your /boot/grub/menu.lst file.
2 - How your bios views your hard drives.
3 - The partition scheme for each hard drive.  

Basically what is wrong here is that you have GRUB looking in the wrong area for itself, and therefore cannot find the files that it needs to boot.  This is usually pretty easy to resolve, but may require editing the menu.lst file to point GRUB back to where it should be.  Depending on how you want the boot order for the hard drives, you may need to switch the boot priority for the hard drives in your BIOS.  First though post the information above and we can see what needs to be done.

---

### Post by th3void on 2007-03-30
> Yep, you need to mount your /boot partition while you are in the LiveCD environment.

In order to fix this problem we need three things:

1- The output of your /boot/grub/menu.lst file.
2 - How your bios views your hard drives.
3 - The partition scheme for each hard drive. 


OK, how do I mount the /boot partition from the LiveCD?

Also, how do I get you 2 and 3?

I'm in the absolute beginner forum for a reason ;P

---

### Post by dstew on 2007-03-30
Yes, you need to mount the hard disk partition that contains your linux system. When you have booted from the live CD, you can mount the linux system by

mount /dev/hdb1 /mnt/hdb

or something like that, depending on the name of the partition you want to mount.

EDIT: Then you can find the /boot directory in /mnt/hdb/boot

---

### Post by rewolf on 2007-03-30
thanx very much...
im so lost with this linux stuff...

so where can i find info on how to configure grub correctly etc?... whatever grub is.
lol - i hate being so dumb!

thanx so soo much

-----------------
-rewolf

---

### Post by alien21010 on 2007-03-30
To mount the /boot partition, make a folder (test/ in this case) in the home directory on the live cd and type:

mount /dev/sda1 test/ (where sda1 is the /boot partition or / partition if you did not make a /boot) 

This will mount the partition to that folder.  Once there you can browse through and find /boot/grub/menu.lst.  Please copy and paste the output of that file here.

In order to see how your bios views the hard drives you need to reboot, and enter your bios setup.  In there there should be an option that says something like "Hard Disk Boot Priority" and it will list the two hard drives in order.  I am assuming that the first hard drive probably has Windows on it?  And that Linux is on the second hard drive?

To get the partitioning scheme, all you need to do is type ls /dev/sd* (for SATA hard drives) and ls /dev/hd* (for PATA hard drives).  It will return something like /dev/sda1, /dev/sda2, /dev/sda3 etc (these are the partitions on your hard drives).

---

### Post by rewolf on 2007-03-30
thanx very much...
im so lost with this linux stuff...

so where can i find info on how to configure grub correctly etc?... whatever grub is.
lol - i hate being so dumb!

thanx so soo much

-----------------
-rewolf

---

### Post by Maestro23 on 2007-03-30
> **rewolf said:**
> thanx very much...
im so lost with this linux stuff...

so where can i find info on how to configure grub correctly etc?... whatever grub is.
lol - i hate being so dumb!

thanx so soo much

-----------------
-rewolf

All about GRUB: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by th3void on 2007-03-30
My linux partition is /dev/hdd2
My windows partition is /dev/hda1

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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=feaf02ef-5992-4670-bbfa-639770efbb17 ro
# kopt_2_6=root=/dev/hdd2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd2,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdd2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd2,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdd2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd2,1)
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
title           Windows XP Media Center Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by th3void on 2007-03-30
Also to clarify, I have 3 HDD's.

hda is my Windows XP MCE install, and it's /dev/hda1
hdc is my Windows XP storage drive.
hdd is formatted for both Windows and Linux.
hdd1 is the Windows portion.  hdd2 is where Ubuntu is located.

hda is what my BIOS is booting to, and I thought that's what I told GRUB to install to.  I may be wrong though..

Any ideas?

---

### Post by th3void on 2007-03-30
ubuntu@ubuntu:~/test/boot/grub$ ls -l /dev/hd*
brw-rw---- 1 root disk   3,  0 2007-03-28 17:50 /dev/hda
brw-rw---- 1 root disk   3,  1 2007-03-28 17:50 /dev/hda1
brw-rw---- 1 root cdrom  3, 64 2007-03-28 17:50 /dev/hdb
brw-rw---- 1 root disk  22,  0 2007-03-28 17:50 /dev/hdc
brw-rw---- 1 root disk  22,  1 2007-03-28 17:50 /dev/hdc1
brw-rw---- 1 root disk  22, 64 2007-03-28 17:50 /dev/hdd
brw-rw---- 1 root disk  22, 65 2007-03-28 17:50 /dev/hdd1
brw-rw---- 1 root disk  22, 66 2007-03-28 17:50 /dev/hdd2
brw-rw---- 1 root disk  22, 67 2007-03-28 17:50 /dev/hdd3
brw-rw---- 1 root disk  22, 69 2007-03-28 17:50 /dev/hdd5
ubuntu@ubuntu:~/test/boot/grub$ 

In case that helps...

---

### Post by Duck2006 on 2007-03-30
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by dstew on 2007-03-30
Please post the output of the command **fdisk -l**

This will list your disk partitions. We need to confirm that grub's (hd2,1) is really the same as hdd2.

---

### Post by th3void on 2007-03-30
> **dstew said:**
> Please post the output of the command **fdisk -l**

This will list your disk partitions. We need to confirm that grub's (hd2,1) is really the same as hdd2.

Simply typing fdisk -l yields nothing, ala

ubuntu@ubuntu:~/test/boot/grub$ fdisk -l
ubuntu@ubuntu:~/test/boot/grub$ 

Is there an extra parameter I should be adding here?  I tried 

ubuntu@ubuntu:~/test/boot/grub$ fdisk -l /dev/hdd
Cannot open /dev/hdd

(hdd is the drive my Linux partition is on)

Thanks for all the help, by the way...  This is not much fun for a beginner, but you are certainly easing the transition.

---

### Post by th3void on 2007-03-30
Also, once again, I'm still running off the LiveCD; do I need to change how I run the command to compensate?

---

### Post by alien21010 on 2007-03-30
Yes, fdisk will be very useful.

Type: sudo fdisk -l in the livecd environment (which is what I assume you are in).

---

### Post by th3void on 2007-03-30
Ah, that did it.

ubuntu@ubuntu:~/test/boot/grub$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5004    40194598+   7  HPFS/NTFS

Disk /dev/hdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       38912   312560608+   7  HPFS/NTFS

Disk /dev/hdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       15450   124102093+   7  HPFS/NTFS
/dev/hdd2   *       15451       38725   186956437+  83  Linux
/dev/hdd3           38726       38913     1510110    5  Extended
/dev/hdd5           38726       38913     1510078+  82  Linux swap / Solaris

---

### Post by alien21010 on 2007-03-30
How did you install Ubuntu?  Did you manually make the partitions yourself on /dev/hdd?  Is it possible that you forgot to format the partition using ext3/reiserfs or whatever your choice was?  I only ask because Fdisk -l does not show a file system type for that /dev/hdd2...

---

### Post by th3void on 2007-03-30
I used the automatic tool; I simply told it to autopartition...

---

### Post by th3void on 2007-03-30
> **alien21010 said:**
> How did you install Ubuntu?  Did you manually make the partitions yourself on /dev/hdd?  Is it possible that you forgot to format the partition using ext3/reiserfs or whatever your choice was?  I only ask because Fdisk -l does not show a file system type for that /dev/hdd2...

In Gparted, it states that hdd2 is ext3 formatted,  Is this what I should be using?

---

### Post by alien21010 on 2007-03-30
Yes, ext3 is fine.  Ok, now we are going to use GRUB interactively from the livecd to figure out what the hell it is pointing at.

Open a terminal, type: sudo grub.  The grub command line interface should show up, it will say something like "PROBING BIOS DEVICES THIS MAY TAKE A WHILE", let it do that.  Once it enters into an area where you can enter a prompt, please type the following commands and paste the output if you can.

geometry (hd0)
geometry (hd1)
geometry (hd2)

This will tell you what grub is seeing for the hard drives.  When you do (hd2) you should see the partitions you would expect to see on /dev/hdd.

---

### Post by alien21010 on 2007-03-30
I should have asked this earlier, but can you boot into Windows at all through GRUB?

---

### Post by alien21010 on 2007-03-30
Also try in the grub command interface: find /boot/grub/menu.lst .  That should return (hd2,1).  If that does not, then please say where it does find it... If at all...

We are narrowing down the root of this problem quickly.

---

### Post by th3void on 2007-03-30
> **alien21010 said:**
> I should have asked this earlier, but can you boot into Windows at all through GRUB?

No; the GRUB error occurs at stage 1.5, before I'm able to load up any operating systems at all.  My machine finishes it's POST and then the error occurs.  I'll try your other suggestion in a second and get back to you.

---

### Post by th3void on 2007-03-31
grub> geometry (hd0)
drive 0x80: C/H/S = 5005/255/63, The number of sectors = 80418240, /dev/hda
   Partition num: 0,  Filesystem type unknown, partition type 0x7

grub> geometry (hd1)
drive 0x81: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/hdc
   Partition num: 0,  Filesystem type unknown, partition type 0x7

grub> geometry (hd2)
drive 0x82: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/hdd
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

grub> find /boot/grub/menu.lst
 (hd2,1)

Thanks a ton alien...

---

### Post by alien21010 on 2007-03-31
Well then its not an issue with the GRUB configuration file.  Instead boot into the live cd and enter the GRUB command line interface again (sudo grub).  From there type the following commands:

root (hd2,1)
At this point make sure it says that the filesystem type is ext2fs.

Then type:
setup (hd0)
Make sure that completes with no fatal errors.

Then reboot, and try to reload it.  Basically at this point, I'm thinking that there was a problem with your GRUB install.  Since GRUB is seeing that everything is correct in your menu.lst file hopefully this will work.

---

### Post by th3void on 2007-03-31
> **alien21010 said:**
> 

root (hd2,1)
At this point make sure it says that the filesystem type is ext2fs.


How do I make sure it is ext2fs?

---

### Post by th3void on 2007-03-31
The 

setup (hd0)

command completed successfully.  However, I rebooted, and was presented with the same error...
GRUB Loading stage1.5


GRUB loading, please wait...
Error 17

:\

---

### Post by Duck2006 on 2007-03-31
root hd1,1

---

### Post by th3void on 2007-03-31
> **Duck2006 said:**
> root hd1,1

And that does what exactly?

---

### Post by alien21010 on 2007-03-31
When you type root (hd2,1) it should return something to the effect of:

Filesystem type is ext2fs, partition type 0x83


However, if it does not!, then that is the problem.  Try root (hd1,1) or root (hd0,1) until you find one that returns the above statement.  Then run setup.  See if that works.

---

### Post by Duck2006 on 2007-03-31
windoze is your first boot partition and linux is your second boot partition, you start from 0 and count, your boot partitions and your find that linux is on hd1

---

### Post by th3void on 2007-03-31
It appears that typing

root (hdx,y) 

with x and y being numbers never returns any sort of messages, unless it says "Error 22: No such partition."  Am I doing something wrong?

---

### Post by Duck2006 on 2007-03-31
the other operation for you is to down load super grub and run that it sould solve your problam.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by th3void on 2007-03-31
> **Duck2006 said:**
> windoze is your first boot partition and linux is your second boot partition, you start from 0 and count, your boot partitions and your find that linux is on hd1

Actually, I have 3 HDD's; the first is Windows, the second is a storage drive NTFS formatted, the third is the drive that I installed Linux on.

---

### Post by alien21010 on 2007-03-31
Try running the geometry (hd0), geometry (hd1), geometry (hd2) commands before assigning root.  See if that makes grub return a value.

---

### Post by th3void on 2007-03-31
grub> geometry (hd2)
drive 0x82: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/hdd
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

grub> root (hd2,1)

grub> 


That is the output produced as copied from my terminal.

---

### Post by Duck2006 on 2007-03-31
> Actually, I have 3 HDD's; the first is Windows, the second is a storage drive NTFS formatted, the third is the drive that I installed Linux on.

You only have to boot partitions on your system

---

### Post by th3void on 2007-03-31
> **Duck2006 said:**
> You only have to boot partitions on your system

I do not quite understand what you mean here.

I am downloading SuperGrub right now.

---

### Post by Duck2006 on 2007-03-31
You have 3 hard drives, but only 2 have boot partitions on them, the other is a storage drive.

---

### Post by alien21010 on 2007-03-31
Grub is having major issues with your machine... Is all of your hardware configured correctly (master and slaved?).  Other people on the forums have resolved issues similar to yours because they had two hard drives set to the same jumper.  

Besides that, I think your best bet for resolving this, is either to use Super GRUB, or to go ahead and reinstall Ubuntu using a separate /boot partition, and installing Grub there.  Unfortunately, multiple hard disk installs tend to be much more difficult than single drive installs as you are finding out.  Worst case scenario - physically disable the other two hard drives, install grub to the drive with linux on it.... Get it working, and then set your bios to boot from that hard disk.  If you disable the other drives, GRUB should work.  Afterwords you'll have to edit your menu.lst to add the option for Windows... But it will be much, much easier than continuing to struggle with this.  

Sorry I cannot be of more help than this, but you have me stumped.

---

### Post by th3void on 2007-03-31
I've stumped myself too :D

Thanks for trying.  I'll mess around with it a little bit more, but for every hour I've been struggling with this I've had a glass of wine, so I imagine it will be time for bed pretty soon ;)

I'll let you know if I have any more problems but I'll try a few things different.  Take care.

---

### Post by confused57 on 2007-03-31
> **th3void said:**
> I've stumped myself too :D

Thanks for trying.  I'll mess around with it a little bit more, but for every hour I've been struggling with this I've had a glass of wine, so I imagine it will be time for bed pretty soon ;)

I'll let you know if I have any more problems but I'll try a few things different.  Take care.

I believe one quick thing you might try, is at the grub menu, highlight your Ubuntu entry, press "e", then change root to (hd1,1), then press "b" to boot...worth a try.

You might want to mount your Ubuntu partition using the live cd:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hdd2 /media/ubuntu
```
then
```
cat /media/ubuntu/device.map
```

If the Super Grub Disk is able to boot your Ubuntu partition, you should be able to get grub configured to do so.

---

### Post by Error47 on 2007-03-31
I used to get those, they went away after I formatted my windows drive.

---

### Post by th3void on 2007-03-31
So before, I was only formatting and partioning half my third HDD (hdc), and I was getting Error 17 messages.

So I just reinstalled and this time I totally formatted hdc and reinstalled, and this time I get...  Error 18.

By the way, these are stage1.5 errors.  I have not yet been able to boot linux...

Thoughts?

---

### Post by confused57 on 2007-03-31
> **th3void said:**
> So before, I was only formatting and partioning half my third HDD (hdc), and I was getting Error 17 messages.

So I just reinstalled and this time I totally formatted hdc and reinstalled, and this time I get...  Error 18.

By the way, these are stage1.5 errors.  I have not yet been able to boot linux...

Thoughts?
You'll need to repost the output of:
```
sudo fdisk -l
```
the -l is a small "L"

---

### Post by confused57 on 2007-03-31
> **rewolf said:**
> I currently have WinXP installed on my PC as my OS. I have a AMD64 X2 processor (don't know if that influences anything)
My problem is as follows:
I installed ubuntu 6.06 from the play disc, onto another hard-drive.  When i restart after the installation, it appears as though ubuntu tries to boot, but b4 anything happens, a
"error 17" is displayed.
thats all.

What does that mean, and how can i get ubuntu to work?

To get back into windows i had to reinsert my XP disc - go to repair - and say FIXMBR, because the boot record had been changed - argh.  ive tried installing twice.

thanks for the help
--------------
-rewolf
I'll try to help you, since you started all this...if you want to avoid installing grub to the Window's drive mbr, you might want to read this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

You may be able to accomplish the same thing, without disconnecting your Window's hard drive, by changing the bios hard drive boot order...before installing Ubuntu, go into your bios setup and select your Ubuntu drive as the 1st hard drive in your boot order(after the cd drive), then your Window's drive as  the 2nd hard drive booted.

---

### Post by th3void on 2007-03-31
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5004    40194598+   7  HPFS/NTFS

Disk /dev/hdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       38912   312560608+   7  HPFS/NTFS

Disk /dev/hdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       38725   311058531   83  Linux
/dev/hdd2           38726       38913     1510110    5  Extended
/dev/hdd5           38726       38913     1510078+  82  Linux swap / Solaris

---

### Post by confused57 on 2007-03-31
> **th3void said:**
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5004    40194598+   7  HPFS/NTFS

Disk /dev/hdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       38912   312560608+   7  HPFS/NTFS

Disk /dev/hdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       38725   311058531   83  Linux
/dev/hdd2           38726       38913     1510110    5  Extended
/dev/hdd5           38726       38913     1510078+  82  Linux swap / Solaris

Here's a description & possible solutions for grub error 18:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)
might be related to the size of your hard drive...possible solutions listed in the link are a bios update, reducing the size of your Ubuntu root partition, or having a separate boot partition at the beginning of the hard drive.

If you have another computer you can access, you might want to download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's a useful utility for Windows or Linux booting problems...it can restore your Window's drive mbr or grub and is able to boot Windows or Linux.

You've received some good advice in this thread, but I got a little lost reading through it...so, I may repeat some things that have already been recommended.

If you've read the reply I gave to rewolf, you might consider doing the same thing...restore your Window's IPL code to your Window's drive mbr, using the Super Grub Disk, or following this guide:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Once you're able to boot your Window's drive independently of grub, then follow the advice I gave to rewolf, i.e. set your drive you're installing Ubuntu to as the first hard drive booted in bios and possibly also creating a separate boot partition or making your root partition smaller and maybe setting up a separate /home directory along with the swap partition.

The 2nd link in my signature is an excellent guide for installing with the Desktop cd and the 1st link has some great info for installing with the Alternate cd.

I know this is a lot of "stuff" to digest all at once and feel free to ask any questions you may have.

---

