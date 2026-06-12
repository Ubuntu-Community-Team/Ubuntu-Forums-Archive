---
title: "New take on an old thread"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by SteveJ on 2006-12-06
Admittedly, I have asked this question before. The post got so long and convoluted, however, that I don't think anybody would have the patience to get through it to read my last question. So, here goes again....

Due to my own stupidity, after installing Ubuntu, my boot up choices are Ubuntu and an invalid install of Windows (points to the wrong drive). How can I, from Ubuntu, change to boot options to point to the valid install of Windows XP as well as Ubuntu? Currently I have a valid install of XP on my C: drive, and a valid install of Ubuntu on my D: drive. 

Thanks, 

SteveJ


P.S. Please be gentle with your answer - I am brand new to Ubuntu.

---

### Post by Henry Rayker on 2006-12-06
C: and D: drives don't mean anything in terms of Linux. That's a Windows naming convention.

Do you know whether or not they are partitions of the same disk or actual physical hard drives?

---

### Post by taurus on 2006-12-06
You can change the boot order or any other boot option by modifying /boot/grub/menu.lst.

Applications -> Accessories -> Terminal
```
sudo  cp  /boot/grub/menu.lst  /boot/grub/menu.lst.bak
gksudo gedit /boot/grub/menu.lst
```

---

### Post by SteveJ on 2006-12-06
OK, 

Thank you both. Once again, I apologize for my ignorance. I have a book on the way - I just need to get the computer up and running in the mean time. 

So, my drives are two physically independent drives (not a partition). Given that, How might I modify that menu list? What might an entry in ..grub/menu.lst look like to give a boot option to look for windows xp on the primary drive (C: in Windows)?

SteveJ

---

### Post by bulldog on 2006-12-06
Can you give us the outcome of```
sudo fdisk -l [l as in like]
```
And your menu.lst```
gedit /boot/grub/menu.lst
```
So we can have a look at it?

---

### Post by SteveJ on 2006-12-06
I'm a little embarrassed - I'm not at home where the computer is. I didn't expect to get a response so quickly. In Microsoft's support site, I usually leave a post and come back several hours later. I do have the following, which I copied from a previous post.

steve@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 30.6 GB, 30603724800 bytes
255 heads, 63 sectors/track, 3720 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 2 16033+ 12 Compaq diagnostics
/dev/hda2 3 3720 29864835 42 SFS

Disk /dev/hdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 1 2263 18177516 7 HPFS/NTFS
/dev/hdb2 2551 5005 19719787+ 7 HPFS/NTFS
/dev/hdb3 * 2264 2533 2168775 83 Linux
/dev/hdb4 2534 2550 136552+ 5 Extended
/dev/hdb5 2534 2550 136521 82 Linux swap / Solaris

---

### Post by bulldog on 2006-12-06
Can you tell me from which drive you boot?
And which partition is your windows?

---

### Post by SteveJ on 2006-12-06
Windows is in hda, the 30.6GB one. 

Originally, from Windows, I partitioned hdb into two 20GB drives (roughly), one for ubuntu and one for a future Linux or Unix OS (I'm in college for SW Eng, and have to study both)

After doing so, I installed Ubuntu into the first partition of hdb.

SteveJ

---

### Post by bulldog on 2006-12-06
If I understand all of this :D 
you boot from the windows disk and GRUB is installed in this disk as well.

So your windows should point at (hd0,0)
Your ubuntu should point at (hd1,2)

But if you can post your menu.lst later it should be much clearer to tell.
I bookmark this thread and await your menu.lst if you don't get it on track.

---

### Post by SteveJ on 2006-12-06
Thanks, 

I'll post the menu.lst this evening.

SteveJ

---

### Post by SteveJ on 2006-12-06
Here is my menu.lst
--------------------

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
# kopt=root=UUID=1113b417-51d3-4621-b6f7-80ca365625be ro
# kopt_2_6=root=/dev/hdb3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by bulldog on 2006-12-07
Hmmm,just like I said,windows (hd0,0) and ubuntu (hd1,2).
If your windows is on this partition it should boot,do you get an error message or something?

To be clear can you give me the output of ```
sudo fdisk -l (l as in like)
```

Not an old one but a fresh one,there should be something else going wrong here.

---

### Post by SteveJ on 2006-12-07
Basically, what I get are three dots when I try to boot windows.

'...', They grow from one to three dots then start over again - indefinately. 

I'll send the fdisk when I get home. Perhaps a little history might help, though - so you know how I got here.

Initially:
Got computer, with Windows2k on primary, second drive was storage. Decided to install xp on second drive. Later decided wrather to install xp on primary and format secondary. I ended up with 2 pointers to xp - one for the primary drive, one for the second. I edited the boot.ini (incorrectly), and got rid of the wrong entry. I then had two options at boot-up (xp and default). The default option worked OK – the xp option did not (did the same thing that I see now). 

Installed ubuntu:
I installed ubuntu on my second drive. It worked fine but it got rid the 'default' option, so I could no longer load windows.

Reinstalled windows:
This got windows back, but removed the ubuntu option on startup. I once again had two entries for Windows XP – on worked and one didn’t.

Repaired ubuntu:
I put in the ‘boot from cd’ version of ubuntu, and from the terminal ran some command (I don’t have the syntax available, but can get it) that repaired the ubuntu boot for me, but took away windows again – that is where I am currently. 



At this point, I would be open to starting from scratch again, getting everthing off of my computer (clean) and reinstalling windows and Ubuntu. I’m just not sure, at this point, that I won’t end up in the same place though.

Thanks, 


SteveJ

---

### Post by bulldog on 2006-12-07
Well something points to a wrong entry.
And it's not GRUB,at least I think so.

You reinstalled windows and ended up with two entry's in your boot.ini.
So I think there are some things remaining from your win2k install what is messing up things.

If a reinstall of windows is possible I should do so,but reformat the drive before you install,so everything is gone.

Have some questions though.
What are the ```
Device Boot Start End Blocks Id System
/dev/hda1 * 1 2 16033+ 12 Compaq diagnostics
/dev/hda2 3 3720 29864835 42 SFS
```
I don't understand why it points to Compaq diagnostics and what on earth is SFS?

---

### Post by SteveJ on 2006-12-07
I couldn't tell you what SFS is, to be honest. 

Last time I installed Windows I did a format. I see your point though - one would think that I wouldn't end up with 2 boots if I did a format. Perhaps the install grabs the boot.ini before formatting it so that it can allow for other operating systems?

I will go ahead and install Windows again. It is going to get rid of Ubuntu though.

Thanks

SteveJ

---

### Post by bulldog on 2006-12-07
You can let ubuntu where it is :D 
reinstalling GRUB with the live cd is 5 minutes work.

SFS ?? you don't know what it is?
What are you doing with that partition and can you access it?
What's on it.

You make me curious :D

And the Compaq thing? is that something you have to install for some reason?

---

### Post by scc4fun on 2006-12-07
> **bulldog said:**
> You can let ubuntu where it is :D 
reinstalling GRUB with the live cd is 5 minutes work.

SFS ?? you don't know what it is?
What are you doing with that partition and can you access it?
What's on it.

You make me curious :D

And the Compaq thing? is that something you have to install for some reason?
Either Secure FileSystem or Windows 2000?

See [http://www.google.com/search?q=cache:qTS-SVIipqYJ:www.osdever.net/documents/pdf/partitiontypes.pdf+fdisk+id+42+SFS&hl=en&gl=us&ct=clnk&cd=5&client=firefox-a](http://www.google.com/search?q=cache:qTS-SVIipqYJ:www.osdever.net/documents/pdf/partitiontypes.pdf+fdisk+id+42+SFS&hl=en&gl=us&ct=clnk&cd=5&client=firefox-a)

---

### Post by eXisor on 2006-12-07
It could be the boot.ini on the windows drive is pointing to the incorrect partition. (The partition numbering sometimes gets borked when you add a new partition). 
If this is the case, you need to modify boot.ini to point to the correct partition. I had to do the same thing recently.

---

### Post by igknighted on 2006-12-07
(hd0,0) refers to the compaq diagnostics partition.  This is not what you want.  Try replacing (hd0,0) with (hd0,1).  It appears that Compaq put some silly diagnostic tool on the first partition.  hda1 (or (hd0,0)) is too small for the windows install, it must be one hda2 (or (hd0,1).

---

### Post by bulldog on 2006-12-07
> **igknighted said:**
> (hd0,0) refers to the compaq diagnostics partition.  This is not what you want.  Try replacing (hd0,0) with (hd0,1)

Well (hd0,1) would point to the SFS drive.
And I've just learned that it could be a windows2000 install of some sort [thank you scc4fun].
If that is a win2k install,I understand why there are two entry's in your boot.ini.

If there's nothing on the SFS drive you're interested in,just try to format it to NTFS as well,so we get rid of it.:D 

Don't install windows again if you can format the SFS partition.
Altering the boot.ini file should be enough to get it working.

But before doing anything give us a recent sudo fdisk -l please,so we can have a look at all options.

---

### Post by gn2 on 2006-12-07
The "SFS" possibly relates to a hidden recovery partition.

Have you had a look at it with a partitioning utility like Partition Magic, Paragon Partition Editor or gparted live CD?

If you have a Windows Install Cd and all the other software you need on CD's you could re-install everything from scratch and delete all existing partitions, then create new ones with the Windows installer.

Also, have you read this: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by SteveJ on 2006-12-07
Thanks all;

I should probably say that, before this event, my sum experience with boot.ini is zero. 

I will do as you (Bulldog) asked, and get a current report of partitions. With respect to modifying the boot.ini - I wouldn't know how to do that from Ubuntu. 

Also, I should mention that I did one other step that I didn't list in my previous post. After installing Windows (before installing Ubuntu), I partitioned my second drive into two drives, each about 20GB. I installed Ubuntu on the first partition.

Thanks;

SteveJ

---

### Post by bulldog on 2006-12-07
AAARRRGGGHHH now all is lost :D :D 

No the problem is in the Compaq thingy and the SFS partition.
We should be able to solve that.

---

### Post by Duck2006 on 2006-12-07
The first partition on the hd0,1 (windows c:) is a recovery partition for windows 2000,from posts thats that it sound like. I run a compaq and had the same type of partition on mine. I deleted, so there was only one partition on that drive. So you can use the partition tool on the XP disk or from the drives manufacture to take the partition off the hard drive, leaving just one witch will make thing a lot easyer

---

### Post by SteveJ on 2006-12-07
Hmmm.

I don't remember seeing a partition option on my XP CD. Basically, my only options are install and recover. Under install I have the option to format (quick format) before installing. I certainly don't see any options for partitioning the drives. 

I wonder if one of the partitioning programs mentioned above (I have also seen a couple of open source once) will allow me to reformat both drives, delete all partitions, and start from scratch?)

In the mean time, my plan is still to get home and  do the 'fdisk l' and post here. I haven't given up hope of resolving it nicely. If playing nice doesn't work, the next step is to blow it up and start again. 

Thanks, 

SteveJ

---

### Post by gn2 on 2006-12-07
When you install Windows, it will give you the option to delete the existing partitions on the drive. Do this, then create a new partition to install to. 

Remember to back-up any data you want to keep to removable media beforehand.

---

### Post by Duck2006 on 2006-12-07
Yes thats the way. There is a video on the web some wher that shows this (the dual boot install of windows and ubuntu) but i forget as to the address of the site that it is on, as it was a wile back that i saw it

---

### Post by SteveJ on 2006-12-07
OK, here is the result of fdisk;

Disk /dev/hda: 30.6 GB, 30603724800 bytes
255 heads, 63 sectors/track, 3720 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1           2       16033+  12  Compaq diagnostics
/dev/hda2               3        3720    29864835   42  SFS

Disk /dev/hdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2263    18177516    7  HPFS/NTFS
/dev/hdb2            2551        5005    19719787+   7  HPFS/NTFS
/dev/hdb3   *        2264        2533     2168775   83  Linux
/dev/hdb4            2534        2550      136552+   5  Extended
/dev/hdb5            2534        2550      136521   82  Linux swap / Solaris


Think that their is hope for me, or do I need to start anew?

---

### Post by seshomaru samma on 2006-12-08
Sounds like a Windows's problem. Can you post your boot.ini here?
Mount the Windows partition with Ubuntu and look for it at the C:/ partition. 
I'm not sure if Ubuntu can write to NTFS but I'm pretty sure [Knoppix ]("http://www.knoppix.org/")can. So if we figure out the boot.ini you can just alter it with Knoppix and you don't need to alter anything....

---

