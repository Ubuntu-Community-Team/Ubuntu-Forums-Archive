---
title: "Windows will not boot!!!"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Zip247 on 2007-12-27
After using gparted to resize my windows partition and create one for ubuntu I can no longer boot my windows.  I will post /boot/grub/menu.lst.  If anything else is needed just ask and I will get it on the forum as quick as possible.  My wife if very unhappy that I cant boot to windows(I want to get rid of it, she wont let me!!!).  

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=9a68b8be-ebd5-4432-9712-0029b5bc79df ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9a68b8be-ebd5-4432-9712-0029b5bc79df ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9a68b8be-ebd5-4432-9712-0029b5bc79df ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


any help would be appreciated

---

### Post by jas0 on 2007-12-27
Please also post the contents of:

```
less /boot/grub/device.map

and

sudo fdisk -l
```

---

### Post by Zip247 on 2007-12-27
here they are

> Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00071aa9

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1            8990       18159    73658025   83  Linux
/dev/hda2               1        8989    72204111    7  HPFS/NTFS
/dev/hda3   *       18160       19457    10426185   82  Linux swap / Solaris

Partition table entries are not in disk order

> (hd0)	/dev/hda

---

### Post by jas0 on 2007-12-27
LOL! Crap! Everything looks fine to me. :\

So what happens when you try to boot into Windows?

---

### Post by Zip247 on 2007-12-27
When selecting XP from the grub menu I just get a black screen with the words

Starting up...


and it just stays like that until i ctr-alt-del

---

### Post by jas0 on 2007-12-27
Hmm... try to boot into Ubuntu and go to

```
cd /media/hda2
```

Do you see the usual windows directories like Windows and Program Files?

---

### Post by Tyke91 on 2007-12-27
i've had this problem before, you need to boot with your windows install CD (or A windows install CD) , select repair installation, get to a windows command line and type the command
```
CHKDSK
```

hope this helps

---

### Post by Zip247 on 2007-12-27
I can access all of the data on the windows partition just fine, I just cant boot to it.  


tyke91,

I will try and find my windows cd and let you know what happens when and if I do.

---

### Post by jas0 on 2007-12-27
> **wdecker said:**
> I can access all of the data on the windows partition just fine, I just cant boot to it.  


tyke91,

I will try and find my windows cd and let you know what happens when and if I do.

This is good news! Try what Tyke91 suggested:

```
chkdsk /f
```

---

### Post by Zip247 on 2007-12-27
chkdsk found nothing wrong.  I am in the process of system recovery for XP, and will re-install ubuntu after that.  Luckily ubuntu installs quick and easy

---

### Post by Zip247 on 2007-12-27
Bad news and good news

Bad

after XP system recovery, I could not boot the pc to anything.  

I then booted with the gparted boot disk and my HD looked exactly like it did prior to the sys recov.

Good

I burned a SuperGrub Disk and booted to it and recovered my grub loader so I can boot to Ubuntu again.  All of my data from my windows partition is still there and I am back to square one.

Taking the family to dinner now, will check on responses when i get back

---

### Post by meierfra on 2007-12-27
Did you try booting windows with SuperGrub?
Try the various options in SuperGrub. In particular, SuperGrub lets you fix the Windows Boot sector. and the MBR.

Actually I think the problems is that you installed Ubuntu on the first partition. That's where Windows  used to be. And that's where boot.ini is still looking for it. So if SuperGrub  and fixing the boot sector did not help, you might try to edit "boot.ini" from Ubuntu.

---

### Post by digital_exhaust on 2007-12-27
Boot form your XP cd, repair, and choose to save the partition that XP is on.. and try rebooting. Don't know if that will work or not, but I have saved several Vista partitions that way after a resize... 

Good luck..

---

### Post by Zip247 on 2007-12-27
I looked at the boot.ini from windows and from what I saw it is good.

here it is

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect



It looks like it knows that XP is on partition 2 of the HD.

---

### Post by meierfra on 2007-12-28
> default=multi(0)disk(0)rdisk(0)partition(2)\WINDOW S

Did you run"fixboot" before you looked at "boot.ini"?  

What was one your hard drive look before you resized windows? Did it  just have one partition?
Did you try the suggestion from digital_exhaust?
Did you try Supergrub?

---

### Post by Zip247 on 2007-12-28
> Did you run"fixboot" before you looked at "boot.ini"?  


no but i did run fdsk /mbr from a win98 boot disk


> What was one your hard drive look before you resized windows? Did it  just have one partition?

no it had many partitions.  a recovery one that i did not need, a xp one, a ubuntu one and a swap partition.

> Did you try the suggestion from digital_exhaust?

I do not have the xp disk i only have the recovery disks that HP sent with the machine and they do not let you do what digital_exhaust mentioned.  I plan on getting a XP install disk from a friend and trying this

> Did you try Supergrub?

Yes, I tried to fix the mbr for windows with supergrub, when i rebooted the machine could not find any HD.  Re-booted with supergrub again and fixed the grub to get back to where i started.

Thanks to all who are trying to help, I am not giving up yet, so if you have any more suggestions just keep them coming.  All help is greatly appreciated.

---

### Post by meierfra on 2007-12-28
Supergrub also has a fixboot option. It's in the Windows(Advanced)  menu under

re-install Windows NTLDR's IPL to a boot sector

See [Hermanzone]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") for more information.

---

### Post by Zip247 on 2007-12-28
> **meierfra said:**
> Supergrub also has a fixboot option. It's in the Windows(Advanced)  menu under

re-install Windows NTLDR's IPL to a boot sector

See [Hermanzone]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") for more information.

Today has been a busy day for me.  Have not had time to attempt anything.  I will try and re-install the windows NTLDR  later tonight when I get home from work.  

A quick question...Has anyone ever used a program called savepart?  Now that XP is not on partition 1, the registry may still think thats where it is.  According to the savepart documentation, it has the ability to change the registry to let it know what drive letter(partition) XP resides on.

If there are any more suggestions, just keep them coming.

---

### Post by meierfra on 2007-12-28
Don't know anything about "savepart"

Here  is a different  idea:  (but  try fixboot on supergrub first)

Your Ubuntu partition actually comes after the Windows Partition on the hard drive:

> dev/hda1 8990 18159 73658025 83 Linux
/dev/hda2 1 8989 72204111 7 HPFS/NTFS

So you can use  testdisk to fix your partition table.  Windows   will be hda1 after that.
To install testdisk:

```
sudo apt-get  install testdisk
```
(you need the universe repositories enabled for that)
For info on testdisk click on testdisk in my signature.

One problem: Once you rewrote the partion table, grub won't work any more. So you need to fix  grub before you reboot:

```
sudo grub 
root (hd0,1)
setup (hd0)
quit
```

(This might fail since grub might not know the new partition table yet. Then use SuperGrub to get back into Ubuntu. Also you still need to continue with the rest of the instructions)


```
gksudo gedit /boot/grub/menu.lst
```

Change "#groot (hd0,0)" to "#groot (hd1,0)"

Change 

 title Microsoft Windows XP Home Edition
root (hd0,1)

to 

 title Microsoft Windows XP Home Edition
root (hd0,0)

Save the file.

```
sudo  update-grub
```
Since you changed groot, this will change all the  "root (hd0,0)" to "root  (hd0,1)"

Now reboot and hope for the best. 

If that didn't work, try the fixboot again

---

### Post by meierfra on 2007-12-28
Actually I'm not sure about my last suggestion. And neither  your "savepart"

Windows was  the second partition before  you resized windows. The Dell recovery partition was first.  That's why boot.ini  points to second partition. That is also the reason why windows is /dev/sda2  despite the fact that it physically the first partition  on the hard drive.

 Using testdisk to fix the partition table  seems like a good idea, but then boot.ini will point to the wrong partition. May fixboot can fix that. Maybe you have to edit boot.ini manually. Maybe you have use "savepart" to fix the registry.  

And MAYBE windows will boot at the end of all this. Personally I would actually go trough all of this. Just because I like to understand how things work and actually enjoy trying out all kinds of different methods. 

But  erasing all the partitions and starting from scratch probably  would be  faster.  Although reinstalling  Windows can be a pain in the neck, too.

If you are lucky, somebody else in the forum actually understands what is going on  and   comes up with better suggestions.

---

### Post by eternicode on 2007-12-28
Best I can tell, this was your fdisk -l output (always good to put it in "code" tags instead of "quote" tags ;) )...

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00071aa9

Device     Boot  Start   End     Blocks    Id  System
/dev/hda1        8990    18159   73658025  83  Linux
/dev/hda2        1       8989    72204111  7   HPFS/NTFS
/dev/hda3  *     18160   19457   10426185  82  Linux swap / Solaris

Partition table entries are not in disk order
```

Am I the only one who's noticed that the swap partition is marked as bootable?  Is this an issue, or am I confused about the purpose of that flag?

---

### Post by Zip247 on 2007-12-28
I will try your suggestions of testdisk later when i get home from work.  If I have to edit the boot.ini manually that should be no prob.  I will just use supergrub to boot to ubuntu and then edit the boot.ini from there.  Also like you I do not mind playing around trying to fix this.  I have burned all of my pictures and files that I need from my windows partition so if I mess it up I will just remove everything from the HD, re-partition with gparted and then start the installs fresh.  I know that XP install is a long time, but at least I can get ubuntu up and running in about 20 minutes.  I will let you know how your suggestions work out.

---

### Post by bturrie on 2007-12-28
As an aside and only marginally related to your question, I dual booted for a while but got tired of it. Eventually I saved off a ghost image of my windows machine, used the free Vmware Converter tool to create a virtual machine from the image, then wiped my system installed kubuntu and vmware server (or player, both are freeware). Now I run a kubuntu system with an an XP virtual machine based on my old system. It's not good for games but everything else works great. Over time I've gotten to where I hardly use xp anymore except occasionally on websites that only work wit IE, but it's there if I need it.


Alternatively it's pretty easy to build an XP or other windows virtual machine from scratch. You can either do that from vmserver directly or go to the website [www.easyvmx.com](www.easyvmx.com) and configure then download a empty virtual machine to install your windows vm on.

---

### Post by meierfra on 2007-12-28
> Am I the only one who's noticed that the swap partition is marked as bootable? Is this an issue, or am I confused about the purpose of that flag?

Good point. I think I a noticed it at the beginning, but ignored it (since it does not matter when booting with grub).. But it does matter after running "fixmbr" 

So yes, the boot flag needs to be changed. From Ubuntu:

```
sudo grub
root (hd0,1)
makeactive
quit
```

Just to summarize the current plan:

1)  Fix the boot flag

Try to boot into windows. If  you didn't succeed

2)  Use SuperGrub to fix the boot sector and mbr

If you still can't boot into Windows:

3) Use testdisk to fix the partition table.

---

### Post by bturrie on 2007-12-28
As an aside and only marginally related to your question, I dual booted for a while but got tired of it. Eventually I saved off a ghost image of my windows machine, used the free Vmware Converter tool to create a virtual machine from the image, then wiped my system installed kubuntu and vmware server (or player, both are freeware). 

Alternatively it's pretty easy to build an XP or other windows virtual machine from scratch. You can either do that from vmserver directly or go to the website [www.easyvmx.com](www.easyvmx.com) and configure then download a empty virtual machine to install your windows vm on. 

Now I run a kubuntu system with an an XP virtual machine based on my old system. It's not good for games but everything else works great. Over time I've gotten to where I hardly use xp anymore except occasionally on websites that only work with IE, but it's there if I need it. Oh and my wife still uses xp.

---

### Post by Zip247 on 2008-01-01
Finally able to do some more troubleshooting.  I will catch you all up to where I am at with my XP booting problems.

I have used testdisk to set my partition table up differently.

output of fdisk -l

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000715a0

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8989    72204111    7  HPFS/NTFS
/dev/hda2            8990       18159    73658025   83  Linux
/dev/hda3           18160       19457    10426185   82  Linux swap / Solaris
```


my current /boot/grub/menu.lst

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
# kopt=root=UUID=9a68b8be-ebd5-4432-9712-0029b5bc79df ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9a68b8be-ebd5-4432-9712-0029b5bc79df ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9a68b8be-ebd5-4432-9712-0029b5bc79df ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```


my current XP boot.ini file

```
[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect
```


Windows will still not boot.  Just a black screen with the words starting up at the top.

Tried to boot directly to windows with supergrub and get the same results.

I am still not ready to format the whole drive and start from scratch.  So keep the suggestions coming.  Hopefully I can respond faster than last time.

---

### Post by Zip247 on 2008-01-01
nevermind on the suggestions.  I booted to a win2000 cd and did a fixboot c:,  after this when I tried to boot I rx'ed a NTLDR is missing message.  I booted to the supergrub cd and it could not help me get the mbr updated or boot directly to any system.  I then booted to a gparted boot disk all it saw was one big unformatted drive, no more partitions.  I am in the process of using my recovery cd's for XP.  When completed I will re-install gusty and go from there.  Thanks to all for trying to help me.

---

