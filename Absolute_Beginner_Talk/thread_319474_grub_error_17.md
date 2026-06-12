---
title: "grub error 17"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by trachycarpus on 2006-12-15
I have made a large Boo boo :confused: , I have windows on hda and ubunto on a partition of hdb. I decided to install Mandriva on hdb6 and all went well.At the end of the installation It sugggested I use lilo or skip. I skipped. When I went to reboot I get to the grub loader and it says Grub Loading stage 1.5, Grub error 17. I am using a cd of kubunto at the moment. Have I made a terminal error or can I edit grub in some way to get rid of the oproblem. 
Any help would be really appreciated.
Peter.

---

### Post by jonesyp on 2006-12-15
Are you dual booting with Windows?  If so insert your windows XP disk, select repair, follow the prompts and type 'fixmbr' reboot and start again

---

### Post by Iarwain ben-adar on 2006-12-15
Hiya,
no probs at all!

Just type in these:
```
sudo grub
```

That gives you a terminal with the ```
grub>
``` stuff..

Then type in ```
 find /boot/grub/stage1
```

This will give you a (maybe more) location(s), something similair like this
> (hd0,1)

The output of this command (the (hdx,y) stuff) you will need later on..

```
 root (hdx,y)
```

This will tell grub that grub should be installed there (it's not a big deal if you have multiple (hdx,y), because you only need 1, and it's okay which one you use :cool: )

And as a final, type in this
```
setup (hd0)
```

Note: this will install on the MBR of your first drive.


Iarwain

---

### Post by trachycarpus on 2006-12-15
Thanks jonesp, I did that and I now have a windows box again. However I can't now load Ubunto and of course windows can't see the partition ubunto's on.

Iarwain ben-adar, Will this now work if I put the live cd in or have I now lost grub forever, never to be seen again?
Peter

---

### Post by jbayone on 2006-12-15
Whenever I had this issue before, I just re-installed Ubuntu.  It all started when I used Partition Magic in XP to resize my hard drive.  The next time it booted, everything went to crap.

---

### Post by Iarwain ben-adar on 2006-12-15
As far as i know,
it SHOULD work.


Iarwain

---

### Post by trachycarpus on 2006-12-15
Is that an install over the top or a format and reinstall?
Thanks
Peter

---

### Post by Iarwain ben-adar on 2006-12-15
You don't need to reinstall!

Ubuntu is fixable :D
That's the fun part of linux :cool:

Just do as i have told,
and you should be fine.

Should you encounter more errors, just post them here :wink:


Iarwain

---

### Post by okt on 2006-12-15
I am also getting the error 17 message when booting. I have 3 SATA harddrives in my PC atm,

Disk1 - XP pro
Disk2 - NTFS Storage
Disk3 - Ubuntu

I haven't worked with Ubuntu for almost a year now, and back then I was a real noob. So I need as much info as I can get. I am on a laptop, and have the 6.10 install cd booted up on my desktop. I have tried what you have suggested and I still get the error. 

Any information I can post to help solve this?

---

### Post by Iarwain ben-adar on 2006-12-15
Hi okt,

Well,
what did you get when you typen ```
grub> find /boot/grub/stage1
``` ?


Iarwain

---

### Post by bulldog on 2006-12-15
From which disk are you booting on the desktop and where is GRUB installed?
Can you give us the output of ```
sudo fdisk -l (l as in like ) 
```
And if possible the outcome of your menu.lst as well,but before we can acces it we have to mount your ubuntu.

---

### Post by okt on 2006-12-15
> **Iarwain ben-adar said:**
> Hi okt,

Well,
what did you get when you typen ```
grub> find /boot/grub/stage1
``` ?


Iarwain

```
grub> find /boot/grub/stage1
(hd2,0)
```

---

### Post by Iarwain ben-adar on 2006-12-15
```
grub> root (hd2,0)
grub> setup (hd0)
```

And this then?


Iarwain

---

### Post by bulldog on 2006-12-15
When you get an error with GRUB it doesn't mean you have to reinstall GRUB because it's there already.
It has an error which you have to solve.

17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

---

### Post by okt on 2006-12-15
> **Iarwain ben-adar said:**
> ```
grub> root (hd2,0)
grub> setup (hd0)
```

And this then?


Iarwain
```
grub> root (hd2,0)

grub> setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_Stage1_5 (hd0)"... 15 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd2,0) /boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
```

I had to hand write that so something might not be 100% but hopefully its all there. ;)

---

### Post by Iarwain ben-adar on 2006-12-15
no probs :D

And you still get the error now?

If you do,
please post the output of this command
```
sudo cat /boot/grub/menu.lst
```
and of this one
[/code]sudo fdisk -l (a L, but lowercase)[/code]


Iarwain

---

### Post by okt on 2006-12-15
> **Iarwain ben-adar said:**
> no probs :D

And you still get the error now?

If you do,
please post the output of this command
```
sudo cat /boot/grub/menu.lst
```
and of this one
[/code]sudo fdisk -l (a L, but lowercase)[/code]


Iarwain

I get no such file or directory.

How would I mount and view it properly?

```
sudo fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9038    72597703+   7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          26      204819+  ee  EFI GPT
/dev/sdb2              26        9965    79838424    7  HPFS/NTFS

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14338   115169953+  83  Linux
/dev/sdc2           14339       14946     4883760    5  Extended
/dev/sdc5           14339       14946     4883728+  82  Linux swap / Solaris

```

---

### Post by Iarwain ben-adar on 2006-12-15
:oops: forgot you were using the live disc :D

So,
first make a dir for your Linux partition to be mounted on:
```
sudo mkdir /test
```
(you can make it where you like, and name it how you like, but it's just for keeping things simple)

```
sudo mount /dev/sdc1 /test
```
(this mounts it to /test)

And then do ```
sudo cat /test/boot/grub/menu.lst
```

That should work :D


Iarwain

---

### Post by jbayone on 2006-12-15
I did a re-install from the live CD to get up and running again.  I couldn't mount any drive I had installed so I couldn't edit the grub config.

---

### Post by Iarwain ben-adar on 2006-12-15
> **jbayone said:**
> I did a re-install from the live CD to get up and running again.  I couldn't mount any drive I had installed so I couldn't edit the grub config.

Strange that you couldn't mount the hard drive :?


Iarwain

---

### Post by okt on 2006-12-15
Sorry it took so long, slow bloated windoze...

I left the commented stuff in, hope you don't mind. :P

```
sudo cat /media/ubuntu/boot/grub/menu.lst
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
# kopt=root=UUID=1f9c60d1-ba87-4f44-9511-8eb129b88a00 ro
# kopt_2_6=root=/dev/sdc1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sdc1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sdc1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by Iarwain ben-adar on 2006-12-15
Strange,
can't see anything weird about it :?

And the error you get is a Error 17?


Iarwain

---

### Post by okt on 2006-12-15
> **Iarwain ben-adar said:**
> Strange,
can't see anything weird about it :?

And the error you get is a Error 17?


Iarwain

Yes, 

GRUB Loading stage 1.5.


GRUB loading, please wait...
Error 17

---

### Post by Iarwain ben-adar on 2006-12-15
Don't know what could be the error,
but maybe try [this](http://forums.gentoo.org/viewtopic.php?t=120802), see the 4th post :wink:


Iarwain

---

### Post by okt on 2006-12-15
Well I haven't had any luck, even tried to reinstall it.
When I tried what that guy had, using (hd2,1) instead of (hd2,0) it gave me a error 17...


Is there a way I can put another boot loader on there?

---

### Post by Iarwain ben-adar on 2006-12-16
I see that you already started another thread :D

All i can suggest is LiLo, but i don't know sqaut about it :oops:


Iarwain

---

### Post by trachycarpus on 2006-12-16
Right, back to me again. Thanks to all that have helped( notice its not tried) The Fixmbr worked and so did the grub fix of Iarwain ben-adar. However when I get into grub menu the couple of Ubunto options, when selected, both turn up the message  "Cannot mount selected partition" At least the error messages mean something to normal people, unlike Windows.
Peter

---

### Post by Iarwain ben-adar on 2006-12-16
Welcome back! :D

So,
how 'bout a little ```
sudo fdisk -l (lowercase L)
```
and this one
```
sudo cat /boot/grub/menu.lst
``` (see my above post of how to mount your drive in the Live-cd)


Iarwain

---

### Post by John E on 2006-12-16
Grub error 17 means that the partition you've selected as / (root) cannot be mounted. Either it doesn't exist or it's not a Linux partition or you've indicated the wrong partition in menu.lst

Do you still need help with this or have you solved the problem now?

---

### Post by bulldog on 2006-12-16
If it's not solved yet,keep an eye on your fstab too,and see if the partition GRUB points to,is listed in fstab the same way.
In example,if GRUB points to (hd0,3) look in fstab if (hda4) is set there as well.

Be aware fstab uses a different naming as GRUB.

---

### Post by trachycarpus on 2006-12-16
Sorry I didn't answer sooner as I'm at work trying to sell xmas trees, harder than you think. However I have not yet solved the problem, when I sudo fdisk -l I get 
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4997    40138371    7  HPFS/NTFS

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/hdb2            2551        2933     3076447+  1c  Hidden W95 FAT32 (LBA)
/dev/hdb3            2934        3962     8265442+  1c  Hidden W95 FAT32 (LBA)
/dev/hdb4            3963       10011    48588592+   f  W95 Ext'd (LBA)
/dev/hdb5            3963        4090     1028128+  83  Linux
/dev/hdb6            4209        5803    12811806   83  Linux
/dev/hdb7            7397       10011    21004956    b  W95 FAT32
/dev/hdb8   *        5804        7326    12233466   83  Linux
/dev/hdb9            7327        7396      562243+  82  Linux swap / Solaris
/dev/hdb10           4091        4116      208813+  82  Linux swap / Solaris
/dev/hdb11           4117        4208      738958+  83  Linux

Partition table entries are not in disk order

sudo cat /boot/grub/menu.lst returns an error message.

Sorry, being a newbie I don't know what a Fstab is. or where it is.
Thanks
 Peter

---

### Post by trachycarpus on 2006-12-16
in the grub edit selection I get
root (hd1,6) this is where ubunto is
kernal/boot/vmlinuz-2.6.17-generic root=dev/hdb7 ro quiet splas
should hdb7 read hdb6???
Hope this might help.
Peter

---

### Post by ReiKn on 2006-12-16
> **trachycarpus said:**
> in the grub edit selection I get
root (hd1,6) this is where ubunto is
kernal/boot/vmlinuz-2.6.17-generic root=dev/hdb7 ro quiet splas
should hdb7 read hdb6???
Hope this might help.
Peter

hdb7 is ok, it corresponds to hd(1,6), though my line reads:
/boot/vmlinuz-2.6.17-10-generic root=UUID=(something random-looking here)

I had a problem booting windows from a SATA drive that wasn't the hd(0, something). So you could try my fix:

Add (this maps hd1 to be hd0 and vice versa) 
```
map (hd0) (hd1)
map (hd1) (hd0)
```
before the root line in the /boot/grub/menu.lst, then change the root line to 
```
root (hd0,6)
```

---

### Post by John E on 2006-12-16
Do you only have one physical drive? If so, it appears to be configured as a slave instead of the master. Were you aware of this?

Also, is it feasible just to re-install Ubuntu or would you lose weeks' worth of setting up & configuration?

---

### Post by Goweb on 2006-12-16
I have a very similar problem.....tried to istall Ubuntu 6.10 edgy on my PC.

I choose the option to use the whole hard drive....now on re-boot I get the error:

GRUB Loading stage 1.5.

GRUB loading, please wait....

Error 18


There is a cursor flashing below the error...but I cant type anything.

Shuld I just try to re-install? What should I choose for options as far as hard drive?

I dont need a dual-boot pc for now.

The hard drive used to be a MS Windows 2000 Pro set-up.

Thx!!

---

### Post by trachycarpus on 2006-12-16
No I have dual boot with windows on hda, hdb7 I see is a fat32 partition  so ubunto wouldn't be there and be bootable would it???:confused: 
May well try the map fix later this evening, damn I'm babysitting tonight.

---

### Post by trachycarpus on 2006-12-16
Thanks ReiKn

tried the map commands, error messages for both-- bash syntax error near unexpected token hdo and the same for hd1
tried root (hd0,6) message No such file or Directory
pity it didn't work
Thanks for idea
peter

---

### Post by ReiKn on 2006-12-16
> **trachycarpus said:**
> Thanks ReiKn

tried the map commands, error messages for both-- bash syntax error near unexpected token hdo and the same for hd1
tried root (hd0,6) message No such file or Directory
pity it didn't work
Thanks for idea
peter

Ah, I guess I wasn't clear enough..
So you're supposed to edit the file (using gedit for example)
/boot/grub/menu.lst 
of your ubuntu install, and make the changes to that file so that the corresponding part of it looks something like this:

Doing a backup copy of the menu.lst first would be a good idea.

```

title           Ubuntu, kernel 2.6.17-generic
map (hd0) (hd1)
map (hd1) (hd0)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.17-generic root=/dev/hda7
initrd          /boot/initrd.img-2.6.17-generic
savedefault
boot

```

But if this is true:
> 
No I have dual boot with windows on hda, hdb7 I see is a fat32 partition so ubunto wouldn't be there and be bootable would it???
May well try the map fix later this evening, damn I'm babysitting tonight.


you should just find out the real partition ubuntu is on and change the root line and the kernel line to correspond with that partition. As far as I know the mapping thing is needed only if the OS is not on the first drive (hda).

---

### Post by John E on 2006-12-16
> **trachycarpus said:**
> No I have dual boot with windows on hda, hdb7 I see is a fat32 partition  so ubunto wouldn't be there and be bootable would it???:confused: 
Which partition do you think Ubuntu is on?

---

### Post by John E on 2006-12-16
> **Goweb said:**
> I choose the option to use the whole hard drive....now on re-boot I get the error:

GRUB Loading stage 1.5.

GRUB loading, please wait....

Error 18


There is a cursor flashing below the error...but I cant type anything.

Shuld I just try to re-install? What should I choose for options as far as hard drive?

Error 18 means that Grub is trying to boot from a sector which is higher than the highest value allowed by the BIOS. Older PC's had a limit on how high the boot sector could be. Having said that, this is a very strange error to be getting if you chose to use the whole drive for Ubuntu. What size is your hard drive?

---

### Post by Goweb on 2006-12-16
Its a 160GB hard drive.....Is there any options for starting fresh?

Reformat the drive? 

Must be some options - Thx!

---

### Post by trachycarpus on 2006-12-17
Quote
"you should just find out the real partition ubuntu is on and change the root line and the kernel line to correspond with that partition. As far as I know the mapping thing is needed only if the OS is not on the first drive (hda)."
Well I've found out that Ubunto is on hdb 7, I found this out by changing the grub entry for root 
 from hdb6 to hdb7. I now get past the "unable to mount" problem and Ubunto starts to load. It gets to about 10% of the orange bar and stops and goes into the flashing curser. There it stops. 
Any thoughts about the next step?
Thanks to all who've tried to help e struggling newbie.
Peter.

---

### Post by John E on 2006-12-17
**Goweb** - My advice would be this:-

1) Obtain a partition manager such as Gparted or Partition Magic that can be booted from a CD ROM or floppy.
2) Using the partition mnaager, check how many partitions are currently on the drive. From what you said earlier, it sounds as if there should only be one (or maybe two, if you allocated a swap partition).
3) If you find some partitions that you didn't expect to be there, come back here for further advice - otherwise....
4) Delete all the partitions.
5) If you want to be able to dual-boot at a later date, create a primary partition (unformatted) of about 30GB.
6) Create an extended partition taking up the rest of the disk (leave it unformatted).
7) Resize the extended partition, leaving about 1GB of space at the beginning. Format this as a Linux swap partition.
8) Delete the unformatted logical partition, leaving only a swap partition in the extended space.
9) Create a new logical partition (immediately above the swap partition) and make it about 10GB. Format it as ext2 or ext3.
10) Delete the primary partition (if you created one).
11) Now you should be left with just 2 Linux partitions. Re-install Ubuntu, making sure that you select each partition appropriately (swap partition = /swap and ext2 or ext3 partition = /).
12) Now you should be able to boot into Ubuntu. Resize the main Linux partition later - or create extra Linux partitions in the extended space, if you prefer.

---

### Post by John E on 2006-12-17
**trachycarpus** - What does the orange writing say, just before you get the flashing cursor? Also, can you boot up okay using the live CD?

---

### Post by trachycarpus on 2006-12-17
> **John E said:**
> **trachycarpus** - What does the orange writing say, just before you get the flashing cursor? Also, can you boot up okay using the live CD?

As far as I remember there is no writing and I'm using the live cd now. Heck its slow compared to the real thing.
John E
Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/hdb2            2551        2933     3076447+  1c  Hidden W95 FAT32 (LBA)
/dev/hdb3            2934        3962     8265442+  1c  Hidden W95 FAT32 (LBA)
/dev/hdb4            3963       10011    48588592+   f  W95 Ext'd (LBA)
/dev/hdb5            3963        4090     1028128+  83  Linux
/dev/hdb6            4209        5803    12811806   83  Linux
/dev/hdb7            7397       10011    21004956    b  W95 FAT32
/dev/hdb8   *        5804        7326    12233466   83  Linux
/dev/hdb9            7327        7396      562243+  82  Linux swap / Solaris
/dev/hdb10           4091        4116      208813+  82  Linux swap / Solaris
/dev/hdb11           4117        4208      738958+  83  Linux
As you can see there is a win partition which I don't want to lose, the rest would be a nuisance but not a problem.Could I delete all the partitions except Hdb1?

---

### Post by John E on 2006-12-17
1) It looks as though all the Windows parttiions are primary and all the Linux ones are logical. Is that correct?
If so, you can use Fdisk to delete the extended partition - but you'll lose **_all_** your Linux partitions

2) Do you have access to a partition manager such as GParted or Partition Magic?

3) What version of Windows is it - and do you still have the install CD?

---

### Post by trachycarpus on 2006-12-17
now I'm showing my ignorance, insert groan here, I don't know the difference and not sure how to find out. I have burned the iso of gparted and will run this later to see if this will enlighten me. Can't do it now as I'm about to start work. 
Thanks
Peter.

---

### Post by John E on 2006-12-17
Okay - here's a crash course for when you get back....

1) No matter how big it is, a physical hard drive can only hold up to 4 x primary partitions.
2) Once a partition is formatted it becomes known as a volume. A volume is simply a partition that can be recognised by an operating system. However, not all operating systems recognise all types of volume. Furthermore, partitions can be deliberately hidden to make them invisible to the OS.
3) Under Windows, volumes are assigned letters (such as C:, D: and E: etc). Under Linux, they're assigned names (such as /dev/hda1 and /dev/hdb6).
4) Any **_one_** of the primary partitions can be designated as an extended partition. By convention, the 4th primary partition is normally extended but it needn't be the 4th one. An extended parttiion can be subdivided into further partitions. These are known as logical partitions because they're subdivisions of a physical parttiion. Once again, after formatting, they become known as logical volumes.
5) **Fdisk** knows nothing about logical partitions. It only recognises the 4 types of physical partition. Therefore, if you use Fdisk to delete an extended partition, you'll lose all the logical partitions and volumes that it contained.
6) To create and manipulate logical partitions you need a partition manager such as Gparted or Partition Magic.

I don't think you should go too much further utnil you get Gparted up & running!

---

### Post by bulldog on 2006-12-17
Don't use Partition Magic to create new Linux partitions,you're heading for trouble if you do,use Gparted instead.

@John E,
Fdisk is surely capable in creating and deleting logical volumes,but it's rather confusing to use it.
Gparted is the best bet in this.

---

### Post by CAN-CAN on 2006-12-17
I have the same error 17! I am a very newbie in Linux and I don't know what to do even if I read all threads about this error..

Well, my story is this..
I have 2 IDE Hard drives:
i. Master  320 GB, 3 partitions: 1st ext3 for Ubuntu, 2nd NTFS for WinXP(not yet installed) and 3rd swap
ii. Slave 60 GB, NTFS with media.

I installed Ubuntu first and I installed grub on hd0. I believed that it was right for my system.

What is the answer to my probem?
If you need more information about my system, let me know..

---

### Post by bulldog on 2006-12-17
If you plan to install windows,I would suggest to make a primary partition at the beginning of the disk,otherwise you're heading for more trouble as you have already :D 

I presume you did see the GRUB menu and it fails to boot.
Fire up the live cd and if you come to the desktop,open a terminal and copy the content of
```
sudo fdisk -l (l as in like)
``` to this forum.
So we can have a look at your problems.

---

### Post by CAN-CAN on 2006-12-17
```
Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19269   154778211   83  Linux
/dev/hda2           38539       38913     3012187+   5  Extended
/dev/hda3           19270       38538   154778242+   7  HPFS/NTFS
/dev/hda5           38539       38913     3012156   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7475    60042906    7  HPFS/NTFS
```


That's my results..

I forgot to say that if I boot from the CD and I choose "Boot from the Hard Disk" and choose the kernel of Ubuntu I boot with no problem..

---

### Post by bulldog on 2006-12-17
Well if you can boot into ubuntu do so.
And give us the content of ```
gksudo gedit /boot/grub/menu.lst
```

Seeing your partitions I suggest to install windows on hdb and keep hda3 as a storage partition for your windows files.
Doing so needs some altering to the menu.lst because windows likes to think to be on the first disk.
A minor thing to do,don't you worry about that.

---

### Post by CAN-CAN on 2006-12-17
Here you go..

```
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
# kopt=root=UUID=ff626d34-dd69-4eb0-93e3-471669389e1c ro
# kopt_2_6=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```


It's really big!!! I don't understand anything!

---

### Post by bulldog on 2006-12-17
Presuming grub is on hda there's nothing wrong with your menu.lst
You can try ```
sudo update-grub
``` in your terminal.

Which kind of file system did you use?You best should use ext3 but don't think this is what's wrong.

Can you give me the outcome of ```
gksudo gedit /etc/fstab
```

---

### Post by CAN-CAN on 2006-12-17
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ff626d34-dd69-4eb0-93e3-471669389e1c /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /media/hda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=F890D4AD90D4741A /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=3721688e-4602-463b-bb96-7874eafaf19e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

I use ext3.

---

### Post by bulldog on 2006-12-17
Nothing wrong with this as well.
You stated it boot fine from using the live cd and boot from hard disk,so there shouldn't be anything wrong with it.
Only thing I can think of is reinstalling GRUB from the live cd and see if there's an error within GRUB.
Otherwise I don't know what the error caused.
To install GRUB from the live cd.

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

---

### Post by John E on 2006-12-17
Can Can -  take note of Bulldog's advice and make Windows your first primary partition. Also, try to install Ubuntu in the first logical partition. That way, you can add & remove other partitions without upsetting either Windows or Ubuntu.

To get Ubuntu back again, boot up with the live CD and open up a terminal. Type **sudo grub** (you'll probably be asked for your maintenance password).

After entering the password, type **root (hd0, 0)**. You should see something about it being Type 83. If so, type **setup (hd0)**. Then type **quit**. This will bring you back to the command terminal. Type **exit** and re-boot (remembering to remove the live CD). With a bit of luck, you'll have your Grub menu back again.

---

### Post by CAN-CAN on 2006-12-17
I did what you've tell but nothing..
The same problem!

I'm getting crazy!!!](*,)

---

### Post by John E on 2006-12-17
So you typed root (hd0,0) and you saw a message saying it was Type 83?

---

### Post by bulldog on 2006-12-17
Everything is set as it should be,the reason it won't boot is beyond me,you can with the live cd without errors,so the only thing I can think of is that you boot from hdb so take a look in your BIOS to see if you do.

But with all the info you've provided,I don't think it's the case,but to be absolutely sure....just take a quick look.

---

### Post by trachycarpus on 2006-12-17
> **John E said:**
> Okay - here's a crash course for when you get back....

6) To create and manipulate logical partitions you need a partition manager such as Gparted or Partition Magic.

I don't think you should go too much further utnil you get Gparted up & running!

Downloaded Gparted and burned iso
ran and got past the splash screen up to the script and there it stalled.
Part of the message 
Disabling irq14, hd9 lost interrupt, irq14 nobody cared( wrong I do care;)  )ide0 on irq 14. There is a lot more script but it just seems to recycle over and iver.
This is getting very frustrating.
What am I doing wrong, assuming I am 
Peter.

---

### Post by CAN-CAN on 2006-12-17
[QUOTE="John E"]So you typed root (hd0,0) and you saw a message saying it was Type 83?
[/QUOTE]

No, I didn't see that message. It didn't message me anything..

---

### Post by John E on 2006-12-18
At the moment, can you boot up from the live CD?

---

### Post by trachycarpus on 2006-12-18
yes
on it now

---

### Post by John E on 2006-12-18
Okay - open up a terminal window and type **sudo grub**. Then enter your maintenance password. After that, type **root (hd0,0)** and let me know what output you see.

---

### Post by trachycarpus on 2006-12-18
As this thread is confusing about who is replying to who, i've started a new thread, Error on grub 17. If I've made an error here please delete/lock the inappropriate post.
Peter

---

