---
title: "First time Linux user, need partition help"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by thedon_1 on 2008-01-15
Just installed Ubuntu on a partition.

So ok, right now i have this

250GB - 3 partitions

200GB = Windows
30 GB = Ubuntu
1.5GB = I think swap file, it was created when Linux was installed

I'm thinking of having the following

20GB = Windows
20GB = Ubuntu
1.5GB = Swap file
200GB = Files (NTFS)

Would the partition program in Ubuntu be the best thing to do this?
How can i achieve this? 

Thanks

---

### Post by wieman01 on 2008-01-15
The partition program can do the job for you, but I find Windows Partition Magic a safer option, although it is not free.

Sharing a partition between Windows and Ubuntu is possible, but I find it easier if you use FAT32 instead of NTFS. NTFS needs some tweaking before you have write-access to it. 

Resizing and moving partitions is a bit of a skill and tricky. You probably need to reinstall GRUB later on and also edit:
> sudo gedit /etc/fstab
Are you sure you want to go through it? If yes, back up all your data first, so nothing gets lost in the process.

---

### Post by Paul820 on 2008-01-15
you can use gparted that is available from within ubuntu or you can use the gparted live cd available from here [http://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/")

---

### Post by Gone fishing on 2008-01-15
Gparted on the live CD should be able to do that - or you could download a standalone version of gparted. 

I use a large ext3 partition for both  Windows and Ubuntu to share files on there is a very good ext3 driver for Windows [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

### Post by wieman01 on 2008-01-15
> **Gone fishing said:**
> Gparted on the live CD should be able to do that - or you could download a standalone version of gparted. 

I use a large ext3 partition for both  Windows and Ubuntu to share files on there is a very good ext3 driver for Windows [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
How well does this work? Looks promising!

---

### Post by thedon_1 on 2008-01-15
Hmm, that fs-driver looks good, but it doesn't have Vista support.

So basically are these the steps i need to go through?

Resize my windows partition so it is smaller.
Resize my Ubuntu partition so it's smaller.
Using the unallocated space, create a new partition, either NTFS or ext3 with the driver possibly running

---

### Post by c0met on 2008-01-15
A note about FAT 32. 

If you decide to use a FAT 32 formatted partition, you may or may not be aware that FAT 32 has a maximum file size of 4 gigs. This would mean that if you were backing up a 4.7 GB DVD, etc, it would not be able to be performed using the FAT 32 partition.

---

### Post by candtalan on 2008-01-15
What you ask for is certainly possible, however it may not be simply a matter of changing a partition size and adding a new partition. Partitions are physically placed on the drives - you can see that by looking at the  start and finish sectors, but they can be named differently. By adding a partition you will need to be careful about what the names are , and be aware of any changes, deliberate or accidental.

Ubuntu installer will probably have created an extended partition, within which ubuntu and the swap partitions exist.

your intention
20GB = Windows
(possible start of extended partiton)
20GB = Ubuntu
1.5GB = Swap file
200GB = Files (NTFS)
(possible end of extended partition)

I think the boundaries of the extended partition may prevent you from moving the proposed 200GB around, not sure.

It may be easily possible to leave a large partition next to windows, as a new primary partition, maybe like:
20GB = Windows
(large spare primary partition)
(possible start of extended partiton)
30GB = Ubuntu
1.5GB = Swap file
(possible end of extended partition)

The (grub) boot manager resides in the ubuntu partiton and is pointed to in the master boot record in the boot sector, so if anything causes a change of name of the ubuntu partition, then you will need to reinstall grub or whatever, before booting will work again. Although I do  not think that the addition of a second primary partition (your new large spare partition) will change the name of your ubuntu partitions which I guess will be in the extended area and their numbering will probably start from hda5.

A word of caution: When I began using linux and doing stuff, I found it easy to completely hose my stuff a couple of times. Changing partition tables can be more risky that it looks!
hth

---

### Post by thedon_1 on 2008-01-15
Thanks for the information.

What would you recommend is the best option for me? Just use the windows partition to house all of my files?
Or leave my Linux partition and try to make my windows one smaller?

---

### Post by c0met on 2008-01-15
I started out thinking that I would need to be able to access files from Ubuntu when I am in Windows. It turns out that that is a rare event and when I need a file for Windows I can just write it to the NTFS  partition from Linux. For me, it's turned out that I'm more likely to access Windows files when I am in Ubuntu, and there is no problem with that.

I recently re-installed Ubuntu with the following set up...
[LIST]
[*]25 GB for / (formatted to ext3)
[*]2 GB for SWAP
[*]around 60 GB for /home (formatted to ext3)
[/LIST]

I had earlier discovered that it's good to have a separate /home partition. The reason for this is that program settings and things like bookmarks, etc, are stored in the /home area. When you re-install Linux, it will always re-format / to prepare the disk for the OS. This means that if /home is on the same partition as /, you lose customised information. Overall, with a separate /home partition, it's quick and easy to reinstall Ubuntu and the programs you had on before.

---

### Post by wieman01 on 2008-01-15
> **thedon_1 said:**
> Thanks for the information.

What would you recommend is the best option for me? Just use the windows partition to house all of my files?
Or leave my Linux partition and try to make my windows one smaller?
1. Resize the Windows partition to something like 20 GB. 
2. Then move Ubuntu to the right side to it and resize it to 20 GB. 
3. Move the SWAP partition to the right side of Ubuntu (1.5 GB).
4. Format all remaining unallocated space to either Ext3 or FAT32.
5. Modify "/etc/fstab" so that it reflect the changes (post here for help).
6. Reinstall GRUB as required (but I don't think it is necessary).

---

### Post by thedon_1 on 2008-01-15
Noob question, why do i need to modify /etc/fstab?

Thanks for the post though, iwill do tat this evening

---

### Post by wieman01 on 2008-01-15
> **thedon_1 said:**
> Noob question, why do i need to modify /etc/fstab?

Thanks for the post though, iwill do tat this evening
"/etc/fstab" contains all information concerning your partitions. If you change the order, size, etc. you need to adjust "fstab" and tell the system where the partitions are, etc. It is fairly simple when you know what you are doing, but you can make things a little more complicated if you don't. 

So posting the contents of 'fstab' up front and telling us what you plan to do, would certainly help. I have gone through the same process many times, so it's on big deal really. But you have to have done it once.

---

### Post by Gone fishing on 2008-01-15
> **wieman01 said:**
> How well does this work? Looks promising!

Very good I've been using for ages with no problems

---

### Post by thedon_1 on 2008-01-17
Ok guys this is my setup.

160GB NTFS | Windows vista(NTFS) 50gb | Ubuntu 15 GB | Swap file (1.5 GB)

I ran fstab and got this

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d2f9534b-47ae-4def-8644-ce796c54f0f8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d682287b-b981-4e06-9331-757e11fc1761 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Could you please advise me on what to do now.

Thanks

---

### Post by wieman01 on 2008-01-17
**@thedon_1:**

Looks fine, but please also post:
> sudo fdisk -l
> sudo cat /boot/grub/menu.lst
Then we can start.

---

### Post by thedon_1 on 2008-01-17
Ok, here's what i got from menu.lst

I don't know what the fdisk is or where to get it.

My Windows no longer boots, i assume this is used to sort that out?



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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=d2f9534b-47ae-4def-8644-ce796c54f0f8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d2f9534b-47ae-4def-8644-ce796c54f0f8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d2f9534b-47ae-4def-8644-ce796c54f0f8 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by wieman01 on 2008-01-17
**@thedon_1:**

> sudo fdisk -l
That's a terminal command. Have you used the terminal before? Just type this, press enter and key in your password. Then post the results (which are essential).

---

### Post by thedon_1 on 2008-01-17
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcff3aaff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       21130   169726693+   7  HPFS/NTFS
/dev/sda2   *       21131       28208    56851200    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           28209       30238    16299360   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4           30238       30401     1315440    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5           30238       30401     1315408+  82  Linux swap / Solaris

---

### Post by BatPenguin on 2008-01-17
Hello there Wieman01,

Just posting a quick side-note to say that I'm watching this thread with great interest: I have a beautifully working Ubuntu HTPC computer in my living room (including Myth, Vmware etc.) that I set up with the idea of using a dualboot with Windows, but haven't been able to boot into Windows without restoring the Windows MBR (which prevents booting to Ubuntu...) first. Don't consider myself a newbie anymore either (been using Linux for some years) but this dualboot setup just didn't seem to work for me even though I've done it with previous computers.  GRUB is just something that I guess I don't "get" that well. Anyway, Windows isn't a big deal to me anymore (just a few games, most of my games I can play under Linux now too), so I haven't done anything to fix the situation in a long time, but this thread caught my eye and I thought that of course it'd be nice to get it going as well. I heard there's a game called Crysis out there that might be worth checking out so maybe there's a point to booting Windows once a week as well...

So: just posted to say that I'm very interested in seeing how menu.lst should be setup to get Windows to boot as well -- so if you wouldn't mind, please give us spectators a few words of explanation of each step that you use to fix menu.lst with the fdisk information so it might be easier to fix slightly different setups as well with the same principles. I'll try to fix my own setup after seeing what you advice here and maybe post a question or two to confirm what I'll be doing before doing it too, if that's OK.  I'll wait until this first question is solved of course, don't wanna hijack the thread.

Thanks :)

---

### Post by wieman01 on 2008-01-17
> **BatPenguin said:**
> Hello there Wieman01,

Just posting a quick side-note to say that I'm watching this thread with great interest: I have a beautifully working Ubuntu HTPC computer in my living room (including Myth, Vmware etc.) that I set up with the idea of using a dualboot with Windows, but haven't been able to boot into Windows without restoring the Windows MBR (which prevents booting to Ubuntu...) first. Don't consider myself a newbie anymore either (been using Linux for some years) but this dualboot setup just didn't seem to work for me even though I've done it with previous computers.  GRUB is just something that I guess I don't "get" that well. Anyway, Windows isn't a big deal to me anymore (just a few games, most of my games I can play under Linux now too), so I haven't done anything to fix the situation in a long time, but this thread caught my eye and I thought that of course it'd be nice to get it going as well. I heard there's a game called Crysis out there that might be worth checking out so maybe there's a point to booting Windows once a week as well...

So: just posted to say that I'm very interested in seeing how menu.lst should be setup to get Windows to boot as well -- so if you wouldn't mind, please give us spectators a few words of explanation of each step that you use to fix menu.lst with the fdisk information so it might be easier to fix slightly different setups as well with the same principles. I'll try to fix my own setup after seeing what you advice here and maybe post a question or two to confirm what I'll be doing before doing it too, if that's OK.  I'll wait until this first question is solved of course, don't wanna hijack the thread.

Thanks :)
No problem. I appreciate your note. :-) I'll try my best then.

---

### Post by wieman01 on 2008-01-17
> **thedon_1 said:**
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcff3aaff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       21130   169726693+   7  HPFS/NTFS
/dev/sda2   *       21131       28208    56851200    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           28209       30238    16299360   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4           30238       30401     1315440    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5           30238       30401     1315408+  82  Linux swap / Solaris
Just to clarify... What operation system can you boot right now? And what partition do you want to have auto-mounted at boot?

---

### Post by thedon_1 on 2008-01-17
Right now i have Ubuntu 7.1 that loads, it's the first thing in the GRUB menu at bootup.

When i select Vista, it just restarts the pc.

I would prefer Ubuntu to load up as default

---

### Post by wieman01 on 2008-01-17
Ok, got it. This is the relevant section that we need to pay attention to:
> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows Vista/Longhorn (loader)
[COLOR="Red"]root (hd0,1)[/COLOR]
savedefault
makeactive
chainloader +1
This assumes that your Vista installation resides on [COLOR="Red"]"/dev/sda2"[/COLOR]. Is that correct? If [COLOR="Blue"]"/dev/sda1"[/COLOR] is the right one, it should read:
> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows Vista/Longhorn (loader)
[COLOR="Blue"]root (hd0,0)[/COLOR]
savedefault
makeactive
chainloader +1
What are the symptoms now?

---

### Post by thedon_1 on 2008-01-17
Thanks for the reply.

I'm at work right now, so i will have to try it out when i get home, but i appreciate you taking the time to help me.

Thanks

Also, the change you made, what does it actually do? Just so i know if was to explain to someone else or do this again.

---

### Post by tad1073 on 2008-01-17
@ wieman01:

Do you think you could give me a hand also. I am not dual booting but I have 3x9.1gb hd's w/ubuntu on sda ext3 on sda1 and swap on sda5, sdb is unformated and sdc is unformated, sdc1 is ext3 and sdc5 is swap. I tried to do a manual partition from the live cd but I didn't know enough about partitioning and didn't have all the info I needed.

---

### Post by wieman01 on 2008-01-17
> **thedon_1 said:**
> Thanks for the reply.

I'm at work right now, so i will have to try it out when i get home, but i appreciate you taking the time to help me.

Thanks

Also, the change you made, what does it actually do? Just so i know if was to explain to someone else or do this again.
[COLOR="Red"]root (hd0,0) [/COLOR]points to the partition on which you have installed your system. 

The first part [COLOR="Red"]"hd0"[/COLOR] stands for [COLOR="Red"]"sda"[/COLOR], if you partition is on an external device and called [COLOR="Red"]"sdb"[/COLOR] it ought to read [COLOR="Red"]"hd1"[/COLOR]. The second bit stands for your partition number. [COLOR="Red"]"0"[/COLOR] means [COLOR="Red"]"sda1"[/COLOR], [COLOR="Red"]"1"[/COLOR] refers to [COLOR="Red"]"sda2"[/COLOR], and so on. 

If you Windows partition is on [COLOR="Blue"]"/dev/sda1"[/COLOR] for instance, the correct reference would be [COLOR="Blue"]"root (hd0,0)"[/COLOR]. You find a good explanation here (section "Recovering GRUB Manually"):

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub)

_**EDIT:**_

[U]A few more examples:
[/U]
/dev/sda1 -> root (hd0,0)
/dev/sda2 -> root (hd0,1)
/dev/sda3 -> root (hd0,2)
/dev/sda4 -> root (hd0,3)
/dev/sdb1 -> root (hd1,0)
/dev/sdb2 -> root (hd1,1)

---

### Post by wieman01 on 2008-01-17
> **tad1073 said:**
> @ wieman01:

Do you think you could give me a hand also. I am not dual booting but I have 3x9.1gb hd's w/ubuntu on sda ext3 on sda1 and swap on sda5, sdb is unformated and sdc is unformated, sdc1 is ext3 and sdc5 is swap. I tried to do a manual partition from the live cd but I didn't know enough about partitioning and didn't have all the info I needed.
No problem. Just open up a new thread and send me the link by PM.

---

### Post by c0met on 2008-01-17
The link below will take you to an article that will help you with setting up GRUB.

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4139582]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4139582")

 Ignore the article's title, the section you need it about 1/3 of the way through the article and has the heading **[COLOR="DarkRed"]Reinstalling Grub to the MBR[/COLOR]**.

Regarding the below...

> /dev/sda1 1 21130 169726693+ 7 HPFS/NTFS
/dev/sda2 * 21131 28208 56851200 7 HPFS/NTFS

Wieman has offered you a lot of good advice. Just to help clarify the quote /dev/sda1 is (hd0,0) and  /dev/sda2 is (hd0,1). These are the first two partitions on your hard drive. The NTFS indicates that they are used by Windows. There is an asterisk against /dev/sda2. I interpret this as meaning the /dev/sda2 is the boot partition (I might be wrong, though). If /dev/sda2 is boot, then root (hd0,1) should be correct. Otherwise, you need to make the change that Wieman has suggested.
[B][U][COLOR="Navy"]
ADDITIONAL THOUGHT[/COLOR][/U][/B]

It might also be worthwhile burning a bootup CD of SuperGRUB and boot your system from that. There are options within the program that will create boot settings. I have found this little program really useful when it comes to helping fix boot problems. Sometimes it doesn't solve the problem but often it does.

You can get the Live CD of SuperGRUB from

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by thedon_1 on 2008-01-17
> **wieman01 said:**
> Ok, got it. This is the relevant section that we need to pay attention to:

This assumes that your Vista installation resides on [COLOR="Red"]"/dev/sda2"[/COLOR]. Is that correct? If [COLOR="Blue"]"/dev/sda1"[/COLOR] is the right one, it should read:

What are the symptoms now?

Ok just had a look. Vista is on /sda2.

What do i then need to do?

---

### Post by c0met on 2008-01-17
If /dev/sda2 is your first or only hard disk, then root (hd0,1) in your menu.lst is correct. My next step would be to burn a live CD of SuperGrub and see if I could restore Windows boot using that. The URL for it is above. 

Failing that, I'd edit the menu.lst and make the changes that Wieman suggests. That is, 

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows Vista/Longhorn (loader)[COLOR="Blue"]
root (hd0,0)[/COLOR]
savedefault
makeactive
chainloader +1

I'd save this and reboot. That will also check that /sda2 is 100% correct. 

To edit the menu.lst do the following
[LIST]
[*]boot into Ubuntu
[*]open a terminal
[*]enter the command [COLOR="Blue"]sudo gedit /boot/grub/menu.lst[/COLOR]
[*]you'll be asked for you password
[*]scroll down the file that is opened until you get the Windows Vista entry (it seems to be right at the bottom of the text)
[*]change to[COLOR="Blue"] root (hd0,0)[/COLOR] (these are zeros)
[*]save and exit
[*]reboot
[/LIST]

See what happens if you try to go to Vista this time.

If that didn't work, I'd reboot Ubuntu and re-edit the menu.lst and restore root to (hd0,1). I'd then then remove the [COLOR="Blue"]savedefault[/COLOR] entry. Save menu.lst and reboot and try Windows. I mention about removing savedefault because I do not have that entry in my menu.lst.

If that doesn't work, I'd go to the URL below, scroll down about 1/3 of the page and follow the instructions for re-installing GRUB into the MBR. (My apologies, I have just realised that I posted the wrong link in my previous post.)

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")

---

### Post by wieman01 on 2008-01-18
c0met has given valuable advice, I would suggest that you follow it.

If your Vista installation continuously reboots after you have selected it from Grub, then it is very likely that it has been corrupted. So you might have to reinstall it. The current settings are OK as far as I can tell, so that is the only other explanation I can come up with.

---

