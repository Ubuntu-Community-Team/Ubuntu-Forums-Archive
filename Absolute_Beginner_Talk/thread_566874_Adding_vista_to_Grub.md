---
title: "Adding vista to Grub"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by duncan_nz on 2007-10-04
Hi all, as the thread title says, I'm looking to add vista boot option to my grub menu.

I'm currently running Gusty 7.10 beta on my 80gig hd, vista on my 36gig raptor and my 3rd hard disk is a nfts disk that contains all my other files :)

here is sudo fdisk -l

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x701f458e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      484518   244197040+   7  HPFS/NTFS

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd783d783

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4501    36148224    7  HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000de460

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1824    14651248+  83  Linux
/dev/hdc2            1825        2432     4883760   82  Linux swap / Solaris
/dev/hdc3            2433        9733    58645282+  83  Linux

```

and here is my grub menu.lst...

```
title		Ubuntu gutsy (development branch), kernel 2.6.22-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=17508b0e-6d71-4935-92d7-55ecbd47c183 ro quiet splash
initrd		/boot/initrd.img-2.6.22-12-generic
quiet

title		Ubuntu gutsy (development branch), kernel 2.6.22-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=17508b0e-6d71-4935-92d7-55ecbd47c183 ro single
initrd		/boot/initrd.img-2.6.22-12-generic
```

What should I put for my root option on the new entry? (vista is on sdb1 sata and linux is on ide disk hdc)

---

### Post by duncan_nz on 2007-10-04
bump

---

### Post by Sephyth on 2007-11-15
i would like to know the same actually
my situations is a little bit different
2 sataII drives
both 320 gig
one with vista
one with ubuntu

it wont display vista in the grub file

and i would love to know how to change it

so
*bump*

---

### Post by bulldog on 2007-11-15
Google is your friend :)

[http://www.pro-networks.org/forum/about78184.html](http://www.pro-networks.org/forum/about78184.html)

---

### Post by rfurman24 on 2007-11-15
check this out.

[http://ubuntuforums.org/showthread.php?t=550024](http://ubuntuforums.org/showthread.php?t=550024)

---

### Post by Sephyth on 2007-11-15
so i tried adding vista to grub

it didn't go so well

what i think i have done would be along the lines of saving the grub file to my vista partition on my first hard drive
and it still doesn't have the option to boot to vista

so i have succeeded in doing the complete opposite of what i wanted to do :lolflag:

i know im a complete noob
but if anyone can please give me a bit of guidance on how to fix reverse or even to update the grub file to let me boot into vista ill be laughing

---

### Post by Duck2006 on 2007-11-15
This mite be worth a look.

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2)

---

### Post by Sephyth on 2007-11-15
its helpfull
more of a last resort tho reinstalling
i want to fix this myself
and i dont want to lose any of the stuff i have sitting on my windows partition

alltho maybe reinstalling ubuntu might fix this. . . 
still i would like to leave that till last if i can

anyone else happy to walk me through edditing the grubfile?

---

### Post by LaRoza on 2007-11-15
```

title		Ubuntu gutsy (development branch), kernel 2.6.22-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=17508b0e-6d71-4935-92d7-55ecbd47c183 ro quiet splash
initrd		/boot/initrd.img-2.6.22-12-generic
quiet

title		Ubuntu gutsy (development branch), kernel 2.6.22-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=17508b0e-6d71-4935-92d7-55ecbd47c183 ro single
initrd		/boot/initrd.img-2.6.22-12-generic

title		Windows 95/98/NT/2000
root		(hd1,0)
makeactive
chainloader	+1

```

You can make the title anything you want. If that doesn't work (as it might not) change (hd1,0), to (hd2,0). If that doesn't work, try a 3, but I don't think you'll need to.

---

### Post by meierfra on 2007-11-15
You need to edit the file /boot/grub/menu.lst.  Open a terminal (Applications->Accessories->Terminal) and post the output of


```
sudo fdisk -l
```

and

```
cat /boot/grub/menu.lst
```
(both l are lower case L, not ones)

With that information, I will be  able to tell  you exactly what you need do,

---

### Post by Sephyth on 2007-11-15
that looks promising

now what do i do with it?
sorry
linux noob
i only installed it 3 days ago

---

### Post by LaRoza on 2007-11-15
Look at what I posted (I didn't realize the thread was hijacked...) and try adding Vista that way.

Use:

```

gksudo gedit /boot/grub/menu.list

```

If Vista is on the master (first) disk, you'll have to change the numbers a bit. Don't alter the existing Ubuntu entries, as they are correct. Just add the Windows section to the end.

---

### Post by Sephyth on 2007-11-15
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38162   306536233+  83  Linux
/dev/sdb2           38163       38913     6032407+   5  Extended
/dev/sdb5           38163       38913     6032376   82  Linux swap / Solaris
ubuntu@ubuntu:~$


and the cat /boot/grub/menu.lst comes back as no such file or directory

---

### Post by LaRoza on 2007-11-15
> **Sephyth said:**
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38162   306536233+  83  Linux
/dev/sdb2           38163       38913     6032407+   5  Extended
/dev/sdb5           38163       38913     6032376   82  Linux swap / Solaris
ubuntu@ubuntu:~$


and the cat /boot/grub/menu.lst comes back as no such file or directory

Use:

```

gksudo gedit /boot/grub/menu.lst

```

And add

```

title		Windows 95/98/NT/2000
root		(hd0,0)
makeactive
chainloader	+1

```
To the end.

---

### Post by Sephyth on 2007-11-15
when it opens up the menu.list there is nothing there
ive tried adding the above code but it comes back file not found

and i apreciate the help by the way

---

### Post by LaRoza on 2007-11-15
It is not "menu.list" just "menu.lst".

(I do that by accident all the time...)

---

### Post by meierfra on 2007-11-15
Came to late.

---

### Post by LaRoza on 2007-11-15
> **meierfra said:**
> Came to late.

Welcome anyway. [noparse]:-)[/noparse]

---

### Post by Sephyth on 2007-11-15
haha nice
yeah tried it with .lst
the file came up blank
added the code

and got this back

ubuntu@ubuntu:~$ gksudo gedit /boot/grub/menu.lst

** (gedit:15400): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

---

### Post by meierfra on 2007-11-15
I just noticed the "ubuntu@ubuntu". Are you working on the Live CD? That would explain why /boot/grub/menu.lst comes up blank.

---

### Post by Sephyth on 2007-11-15
yeah i am working on the live cd becouse i cant boot into ubuntu
well spotted
i was wondering a little if my name should be there

ta mate

---

### Post by LaRoza on 2007-11-15
Use Nautilus, or whatever file manager you use, to look for it. I don't understand why you are getting those errors.

I guess it could be elsewhere, but I don't see how.

-EDIT

Thanks for letting us know of the live cd...

Use:

```

gksudo nautilus

```

Browse for it, it will be on the hard drive (obviously) double click on it, add the entry and try it out.

---

### Post by meierfra on 2007-11-15
You should have  told  us that you can't boot into ubuntu.  If you  press Esc during boot up, to you get the grub menu?  Do you get any error messages?

---

### Post by Sephyth on 2007-11-15
yeah sorry for the live cd debacle

i just located and edited my menu.lst file
ill restart and boot in now and see if it works

if not ill write down any error messages i get

ill be back soon lads

---

### Post by Sephyth on 2007-11-15
sorted

thank you to the both of you
i can now happily boot into widows or Ubuntu from the grub menu

```

gksudo gedit/boot/grub/menu.lst
```

added those extra lines in

booted into grub
played around with the partitions

all good

again
thanks lads
much appreciated

---

### Post by LaRoza on 2007-11-15
> **Sephyth said:**
> sorted

thank you to the both of you
i can now happily boot into widows or Ubuntu from the grub menu

added those extra lines in

booted into grub
played around with the partitions

all good

again
thanks lads
much appreciated

No problem! (Even from those that might not be lads...)

---

### Post by Sephyth on 2007-11-15
haha bloody hell i should have noticed that

my apologies

a special thanks to LaRosa
for your patience and guidance

without you i would probably be formating right now

---

### Post by LaRoza on 2007-11-15
> **Sephyth said:**
> 
a special thanks to LaRosa
for your patience and guidance

without you i would probably be formating right now

If it weren't for the poster you realized you were on a Live CD, I'd be banging my head against my desk trying to figure this out.

LaRoza is different from LaRosa. LaRoza is word from euskara (Basque) and LaRosa is a very popular Italian surname. So similar, yet so different.

---

### Post by Sephyth on 2007-11-15
*smacks forhead*
haha my apologies

again thankyou
and i hope you have a wonderfull day / night

---

### Post by NatroXz on 2008-02-02
So sorry to bring this tread back to live, but I really need some help.
I think the one I have highlighted is the one Vista is on.
But Im clueless :confused:

Here is the output on "sudo fdisk -l"
```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1502b896

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4111    33021576    7  HPFS/NTFS
/dev/hda2            4112       19457   123266745    f  W95 Ext'd (LBA)
**[COLOR="Red"]/dev/hda5            4112        8002    31254426    7  HPFS/NTFS[/COLOR]**
/dev/hda6            8003       15877    63255906    7  HPFS/NTFS
/dev/hda7           15878       19457    28755968    7  HPFS/NTFS

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9630f814

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       24321   195350400    f  W95 Ext'd (LBA)
/dev/sda5               2        9516    76429206    7  HPFS/NTFS
/dev/sda6           15393       24321    71722161    7  HPFS/NTFS
/dev/sda7   *        9517       15146    45222943+  83  Linux
/dev/sda8           15147       15392     1975963+  82  Linux swap / Solaris

Partition table entries are not in disk order

```


And here is the output on "cat /boot/grub/menu.lst"
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=UUID=8cdd64b7-21eb-416e-97cc-55e917cf9660 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,6)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8cdd64b7-21eb-416e-97cc-55e917cf9660 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8cdd64b7-21eb-416e-97cc-55e917cf9660 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,6)
kernel          /boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by NatroXz on 2008-02-05
Sorry , BUMP:?

---

### Post by NatroXz on 2008-02-07
[ S O L V E D ]

[Here]("http://ubuntuforums.org/showthread.php?t=685018")

And

[Here]("http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html")

---

