---
title: "[SOLVED] grub error 17.  please help!!!"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Niklas Schröder on 2008-01-04
i ran out of space on my hd earlier today and decided to delete an old backup partition to make more room.  i used my gparted live cd, deleted the partition, resized my /home partition, and expanded my swap.  gparted didn't appear to have any problems although it had 4 warnings it wouldn't show me.  now, when i reboot my machine, i get grub error 17.  done some research but haven't learned much.  please help!!!

---

### Post by PeterJS on 2008-01-04
Can you post your menu.lst? If it's from an older version it will try to locate the root file system by device name, which may have changed now that their are fewer partitions. Error 17 is the code for unable to mount the partition, which might happen if it's trying to mount your swap space.

---

### Post by frup on 2008-01-04
17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.


One thing that can definitely cause this kind mix up in a perviously stable computer is when someone changes their hard disk Boot Priority in their BIOS.

more [http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by Princey on 2008-01-04
Try re-installing grub. Your partitions were thrown out of sync when you removed the old one you used as backup.

---

### Post by Niklas Schröder on 2008-01-04
well what i can't figure out is that the partition i deleted what just a backup from a tutorial i followed on psycocats...  i just deleted it, expanded my /home to fill the space, and doubled the space of my swap (after moving it to the right).  and my menu.lst is fine.  i updated it about a week ago and it's never given me any problems.  none of the partitions had their names changed, just their sizes...

---

### Post by Niklas Schröder on 2008-01-04
how would i re-install grub if i can't get to a gui?  and what would be the dangers of re-installing it?

---

### Post by Princey on 2008-01-04
You can use a live cd to re-install grub. I've messed up grub a few times and I simply re-installed it. Check out [this]("http://ubuntuforums.org/showpost.php?p=4051320&postcount=2") tutorial. Hope this helps.

---

### Post by Niklas Schröder on 2008-01-04
ok.  i'll try that.  looks promising.  :)  now if i can just find a working live cd in my collection.  ^_^;

---

### Post by Niklas Schröder on 2008-01-04
when i type

```

find /boot/grub/stage1

```

into @#$% small linux, it says it can't find the file...

---

### Post by Niklas Schröder on 2008-01-04
ok.  needed a "sudo" before

```

grub

```

fixed grub now, but now the ubuntu option says it can't find the partition.  how do i go about fixing this?

---

### Post by Niklas Schröder on 2008-01-04
here's how my system is laid out.

i have a couple partitions for my old windoze install.  sda 1, 2,  and 3.  

sda 5, and 6 are inside sda4 and they are for my ubuntu linux install.  is grub seeing it right when it tells me that the main partition is sda 4?  it seems to me like it would really be sda 5...

---

### Post by PeterJS on 2008-01-04
Nope should be sda5, this is what I was trying to get at when I was asking if your partitions might have gotten renamed in the shrink and shuffle.

---

### Post by Niklas Schröder on 2008-01-04
but when i go into the command line and type

```

sudo grub
root (hd0,5)
setup(hd0)

```

it says it can't mount the partition.  did gparted mess up the partition so it's not bootable anymore?

---

### Post by Niklas Schröder on 2008-01-04
bump

---

### Post by frup on 2008-01-04
I am probably very wrong, but I was under the impression you need to do grub on your partitions filesystem not the liveCD's so you might want to try chrooting 

mount your partitions in /media or something and then chroot the ubuntu partition.

so say you mount ubuntu's / to /media/ubu you would type chroot /media/ubu

now you are using the liveCD's tools but changes are affecting / from there you run grub and it will make changes to the grub on the ubuntu partition and mbr not the liveCD's.

---

### Post by Niklas Schröder on 2008-01-04
could you give me a step-by-step please?  i see what you're saying, but i don't know the commands off the top of my head (i MUCH prefer gui's to command line even after a year with only linux) plus it's late and i'm a little fed up with this whole problem.  i'd re-install if i didn't have all my irreplaceable data on that partition!

---

### Post by Niklas Schröder on 2008-01-04
what doesn't make sense about your explanation is that i *have* made effective changes to grub.  it's gone from not booting to showing the menu and booting windoze.  the changes yield the same error in the grub command line (hit "c" while in grub menu).  is there any way i can get out of this problem without re-installing?

---

### Post by frup on 2008-01-04
Oh then it's probably best to disregard what I said. If you are able to boot to windows through grub it is likely that you have only a few errors in your grub menu.lst

Is it still giving error 17 when you try to boot in to ubuntu or a different error? What is likely to be happening that grub is pointing to the wrong partition still. 

Another problem could be that you deleted the wrong partition. I'm sure you would have discovered that by now though.

---

### Post by Niklas Schröder on 2008-01-04
yes.  i have had the bad thought that i deleted the wrong partition.  but i don't think i did.  if i had, i think the numbers counting up in my list of partitions would skip one.  i deleted sda7 and i believe sda5 is my important /home.  and yes.  it still gives me error 17 when i click on the ubuntu link in my grub menu.  but if i click on the "windoze" option, it boots happily.  the only problem with that is that i was planning on deleting that one soon...

---

### Post by PeterJS on 2008-01-04
Ah that makes a difference, I (wrongly) assumed that sda5 was root, if it's actually home, then where is root?

---

### Post by Niklas Schröder on 2008-01-04
which one is root?  the partition housing swap and /home is sda4 and the one with home is sda5 (swap is sda6) and the partition i deleted was an old backup of home (sda7) that was just taking up space.

---

### Post by PeterJS on 2008-01-04
If 4 is the physical partition that contains your logical partition and sda5 is /home and sda6 is swap, then it's not in the extended partitions. I assume sda1 is windows, so what's on 2 and 3?

---

### Post by Niklas Schröder on 2008-01-04
actually sda2 is windows.  sda1 and 3 serve as hidden re-installers for windows.  dell is really weird about partitions...

---

### Post by PeterJS on 2008-01-04
Well that accounts for all your partitions, looks like the one you deleted was your root partition.

---

### Post by Niklas Schröder on 2008-01-04
i sure hope it wasn't!  but i just finished burning an ubuntu live cd.  so hopefully i'll be able to mount the partition in a familiar environment and check it out.  i'm guessing there's no way to get the partition back right?

---

### Post by PeterJS on 2008-01-04
*cringe* I don't think so, doubly so give that you grew the other paritions over it.

---

### Post by Niklas Schröder on 2008-01-04
the root partition's still there.  i deleted the obsolete backup.  i'm looking at the newly resized partition in the live cd environment now.  how can i get grub to recognize it?!?

---

### Post by PeterJS on 2008-01-04
That's good. Can you post your menu.lst? and fdisk -l.

---

### Post by Niklas Schröder on 2008-01-04
yeah.  i actually just pulled up menu.lst to have a look (haven't looked at it yet, just copy/paste).

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
# kopt=root=UUID=ceb5fb0c-efaa-41d9-b82f-e1b32fee3b54 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 7.10
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ceb5fb0c-efaa-41d9-b82f-e1b32fee3b54 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu Recovery
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ceb5fb0c-efaa-41d9-b82f-e1b32fee3b54 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

#title		Ubuntu 7.10, kernel 2.6.20-16-generic
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ceb5fb0c-efaa-41d9-b82f-e1b32fee3b54 ro quiet splash
#initrd		/boot/initrd.img-2.6.20-16-generic
#quiet

#title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ceb5fb0c-efaa-41d9-b82f-e1b32fee3b54 ro single
#initrd		/boot/initrd.img-2.6.20-16-generic

#title		Ubuntu 7.10, memtest86+
#root		(hd0,5)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		------------------------

root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windoze
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by Niklas Schröder on 2008-01-04
and here's the other output

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1951    15631245    7  HPFS/NTFS
/dev/sda3            6534        7113     4658850   db  CP/M / CTOS / ...
/dev/sda4            1952        6533    36804915    5  Extended
/dev/sda5   *        1952        6087    33222388+  83  Linux
/dev/sda6            6088        6533     3582463+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by Niklas Schröder on 2008-01-05
impatient bump.  i'd really like my computer back!  i was planning on doing some projects tonight.  :(

---

### Post by PeterJS on 2008-01-05
> **Niklas Schröder said:**
> yeah.  i actually just pulled up menu.lst to have a look (haven't looked at it yet, just copy/paste).
```

## ## End Default Options ##

title        Ubuntu 7.10
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=ceb5fb0c-efaa-41d9-b82f-e1b32fee3b54 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu Recovery
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=ceb5fb0c-efaa-41d9-b82f-e1b32fee3b54 ro single
initrd        /boot/initrd.img-2.6.22-14-generic

``````
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1951    15631245    7  HPFS/NTFS
/dev/sda3            6534        7113     4658850   db  CP/M / CTOS / ...
/dev/sda4            1952        6533    36804915    5  Extended
/dev/sda5   *        1952        6087    33222388+  83  Linux
/dev/sda6            6088        6533     3582463+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

Looking at the output of fidsk we can see that your root partition is on sda5. Grub and everybody else use different numbering schemes, grub starts counting at zero, where as everybody else starts at 1. So we want the sda5, which grub calls (hd0,4), so looking back up at your grub configuration, I clipped it down to just the two important stanza's if you replace the (hd0,5) with (hd0,4) you should be good to go.

---

### Post by Niklas Schröder on 2008-01-05
thank you thank you thank you!!!  you're awesome!!!  it worked and i'm back and better than ever!  :D :D :D :D :D :D :D :D

---

### Post by PeterJS on 2008-01-05
Sorry that took so long, glad you're back up and running. Keeping a spare live cd around is nice because it makes cleaning up a lot easier.

---

### Post by Niklas Schröder on 2008-01-05
yes it certainly does!  i thought i had a few working ones.  guess i was wrong.  :p

---

