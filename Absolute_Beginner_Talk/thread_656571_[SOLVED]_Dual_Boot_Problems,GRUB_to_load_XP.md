---
title: "[SOLVED] Dual Boot Problems,GRUB to load XP"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by mordantae on 2008-01-02
hi,
im trying to set up a dual boot between xp and linux (gutsy)

i have one 40gb ide drive with linux on it and two 250gb sata drives (first one of which has a partition with windows xp on it)
i'm rather confused as to how to go about it

i've made an entry in menu.lst, This comes up on GRUB however pressing the enter key on that option does absolutely nothing...no error message or anything, just sort of blinks the screen at me..

my fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a732bf50-b259-4dde-b763-4cac7a9b3215 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=d772b070-ce1b-4a5e-b5e2-4238cd631655 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


and my menu.lst looks like this



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
hiddenmenu

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
# kopt=root=UUID=a732bf50-b259-4dde-b763-4cac7a9b3215 ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a732bf50-b259-4dde-b763-4cac7a9b3215 ro noapic nolapic nosplash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a732bf50-b259-4dde-b763-4cac7a9b3215 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		WindowsXP
root (hd1,0)
makeactivechainloader +1


### END DEBIAN AUTOMAGIC KERNELS LIST

i went through a few tutorials and i tried 

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactivechainloader +1

but im not really sure what everything i'm typing means and im rather perplexed that the fstab isnt telling me anything about the SATA drives where xp is installed...

this is what i can see in GParted 

/dev/hda1    IDE 40GB - (master ch0) linux residence
/dev/sda1    firstpartition on SATA(master on ch2) containing fresh xp install
/dev/sda2    secondpartition on same SATA
/dev/sdb1    firstpartition on second SATA
/dev/sdb2    secondpartition on second SATA holding a Ghost of winxp

also another perplexing thing is that i also have an entry called

/dev/mapper/jmicron_LEVIATHAN     

this is what i can only presume a residual something from when i had my SATAs RAID0-ed while running xp in a previous life. the size of it is half the size of what the raid was...i elected to disable all raid entirely since i wanted to keep things simple to start with...so now with raid array deleted and raid disabled from the bios im still getting this entry in GParted...any ideas on how to let it know it doesnt exist? or if it somehow does exist how can i go about obliterating it :) heh...
thanks loads for any help anyone might be able to offer

cheers and hope everyone's having a nice start to their new year...

---

### Post by jken146 on 2008-01-02
> title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactivechainloader +1

The last line should be 2 lines, with "chainloader +1" on a separate line.

If that doesn't fix it for you, please post the output of ```
sudo fdisk -l
```

---

### Post by mordantae on 2008-01-03
changing the last line into two at least gave me an error message...and now it reports that NTLDR is missing...



this is the output of fdisk -l


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd40dd40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4462    35840983+   7  HPFS/NTFS
/dev/sda2            4463       30401   208355017+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00028a9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29126   233954563+   7  HPFS/NTFS
/dev/sdb2           29127       30401    10241437+   f  W95 Ext'd (LBA)
/dev/sdb5           29127       30401    10241406    7  HPFS/NTFS

Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe89be89

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4795    38515806   83  Linux
/dev/hda2            4796        5005     1686825    f  W95 Ext'd (LBA)
/dev/hda5            4796        5005     1686793+  82  Linux swap / Solaris

Disk /dev/dm-0: 250.0 GB, 250047627264 bytes
255 heads, 63 sectors/track, 30399 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00028a9b

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1       29126   233954563+   7  HPFS/NTFS
/dev/dm-0p2           29127       30401    10241437+   f  W95 Ext'd (LBA)
/dev/dm-0p5           29127       30401    10241406    7  HPFS/NTFS




the entry in menu.lst now looks like this


title		WindowsXP
map (hd1) (hd0)
map (hd0) (hd1)
rootnoverify (hd1,0)
makeactive
chainloader +1
boot


thanks for the help

---

### Post by mordantae on 2008-01-05
i am really stuck between a rock and a hard place here i dont know what to do .. :( i've been without a system i can play on since about two weeks before christmas and although im very eager to learn how to use ubuntu i do really need a windows installation to boot into to play !!! i certainly don't want to still be in this situation when i receive assassin's creed!!! i think i might keel over and die  otherwise....please any ideas would be greatly appreciated.. 

thanks in advance

---

### Post by mikewhatever on 2008-01-05
Can you also post the output of <sudo cat /boot/grub/device.map>. You seem to have a lot of HDDs which is usually trickier to set up.

---

### Post by mordantae on 2008-01-05
im not sure whether im doing that correctly but im getting :

tea@Gargleblaster:~$ sudo cat device.map
cat: device.map: No such file or directory
tea@Gargleblaster:~$

---

### Post by mordantae on 2008-01-05
ok cheers mikewhatever :)
right..here's the results

tea@Gargleblaster:~$ sudo cat /boot/grub/device.map
(hd0)   /dev/hda
(hd1)   /dev/sda
(hd2)   /dev/sdb

---

### Post by mikewhatever on 2008-01-05
> **mordantae said:**
> im not sure whether im doing that correctly but im getting :

tea@Gargleblaster:~$ sudo cat device.map
cat: device.map: No such file or directory
tea@Gargleblaster:~$

Thanks, it should have been <sudo cat /boot/grub/device.map>. Corrected in the OP.
According to Herman's guide (see the link below) the chainloading part should look like this:
title        Windows
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk)

You seem to be missing the root (hd1,0) part.

---

### Post by mordantae on 2008-01-05
thanks i'll check it out :) cheers for the reply...i was about to lose hope for a moment there. thanks

---

### Post by mordantae on 2008-01-05
oh wow thankyou thankyou thankyou i've got it working! i dont think i've ever been so happy to see a blimmin windows xp startup loading bar~! 

ho ho ho

for anyone else in some random distant future reading this in hopes of getting out of dual boot doom...do consult the above links...they are full of essential wholesome information on everything to do with using grub..

and for info my entry in menu.lst now stands thusly...

title		WindowsXP
rootnoverify    (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

and i have ubuntu installed on the first hard drive...an IDE
and windows on the first partition of the second drive, a SATA 

oh happy me :)

*fondles ubuntu*

---

### Post by D2Hitman on 2008-01-05
I have a similar problem, I have a multiple hard drive setup, the Master IDE is Ubuntu and the Slave IDE Drive is Windows XP and I can dual boot happily using the menu.lst as detailed previously in this thread. 

I have added an extra PCI Card with Dual IDE Ports on it, this is to give me access more IDE Drives. This card is seen by the Bios as a pseudo SCSI card, both systems can access the Drives but it stops my dual boot to Windows. If I remove the card the dual boot works correctly again.

The two new IDE Drives are sda1 and sdb1, but the problem occurs even with both the new drives disconnected, it is the pseudo SCSI card that is somehow upsetting the Windows Boot, the Ubuntu us fine. 

As mentioned previously in the forum multiple drives cause problems!!  :)

---

### Post by mikewhatever on 2008-01-06
To see a person that happy is worth an effort and is very gratifying. I am glad I saw your post and was able to help. \\:D/

---

### Post by rkd on 2008-01-07
D2Hitman: I imagine what is happening is that the presence of the additional IDE card, even without any drives connected, changes the way the drive numbers are assigned in some way. The drive numbers are what GRUB uses in its references hd1, hd2, and so on.

I believe I recall reading of a way to get a list of what the drive numbers are, but I don't recall where I read that. (And I'm not sure that "drive number" is the proper term for it.) It might be that you look in /boot/grub/device.map, but I'm not sure.

You might find an explanation on this page:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

There is a lot of information about GRUB there, though it isn't easy to read.

---

### Post by mister_pink on 2008-01-07
This is marked as solved now but I feel I should point out that in the original menu file posted the winXP menu option was inside the comments of the automagic kernel settings. It ought to go outside of this or you might find that the xp option disappears one day when that section gets automagically updated!

---

