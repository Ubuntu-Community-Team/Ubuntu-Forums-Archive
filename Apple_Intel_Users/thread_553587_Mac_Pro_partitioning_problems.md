---
title: "Mac Pro partitioning problems"
date: 2007-09-17
forum: Apple Intel Users
---

### Post by spy1325 on 2007-09-17
I've got a Mac Pro with 2 500GB hd's installed in bays 1, and 2

I partitioned the second HD with 32GB of space for Ubuntu 7.04 using bootcamp
I booted the live disk fine and am having trouble getting the partitioning right, it seems bootcamp caters to the windows partitioning, as it pre defines the new partitions as FAT32 etc.

i am getting this error 
-------
Two file systems are assigned the same mount point (/media/EFI): SCSI3 (0,0,0), partition #1 (sda) and SCSI4 (0,0,0), partition #1 (sdb).

Please correct this by changing mount points.
-----------------------

my hard drives are
/dev/sda
   /dev/sda1 - fat32 /media/EFI system partition - 209 mb
   /dev/sda2              488763mb 498300mb used
   /free space             134mbs
/dev/sdb
   /dev/sbd1 fat32 /media/EFI system partition - 209mb
   /dev/sdb2           432712mb 107800 mb used
  free space 134MB
   /dev/sdb3     fat32 /media/DOS_Fat_32_untited_2 67045mb 33 mb used


i think i need to make a SWAP partition and use the rest of the free spce on SDB3 to make an EXT3 partition for ubuntu but i keep getting that error from before..

i've installed Ubuntu on my Macbook and many desktops and dont usually have partitioning problems


any help is appreciated

---

### Post by mert on 2007-09-18
I will be interested to see how your install works.  I have a Mac Pro and I am thinking of installing Ubuntu on an empty hard disk.  It is not clear to me if I need bootcamp or not.  I think I'll give it a try without bootcamp and see if the installer runs.  Not sure if I can use the default bootloader setup though.

---

### Post by spy1325 on 2007-09-18
I just wiped my second harddrive - (migrated the data to my first HD)
and made a mac partition with 400GB space and left the rest to be formatted by ubuntu.
i ran the install disk and formatted the partition as ext3 with a 512 swap partition and went on with the installation but it had a fatal error when it tried to install GRUB. so i assume its having problems with the bootloader. theres a program clled rEFI that supports linux and handles the mac OSX bootloading fine. so im gonna try that and will post the results here

---

### Post by pxwpxw on 2007-09-18
> **spy1325 said:**
> I just wiped my second harddrive - (migrated the data to my first HD)
and made a mac partition with 400GB space and left the rest to be formatted by ubuntu.
i ran the install disk and formatted the partition as ext3 with a 512 swap partition and went on with the installation but it had a fatal error when it tried to install GRUB. so i assume its having problems with the bootloader. theres a program clled rEFI that supports linux and handles the mac OSX bootloading fine. so im gonna try that and will post the results here

Also very interested in your dual drive system solution. 
Install EFIt in Macosx as you suggest and check out the MBR/GPT synchronization with its Partition Tool, a probable cause for grubs difficulty. 

Refit is a very useful tool and boot manager. Refit on a usb stick is also handy backup. Has good documentation on the sourceforge web site.

edit:
related issue:
[Boot my Mac to Ubuntu on External USB 2.0 - post by garethrv]("http://ubuntuforums.org/showpost.php?p=3388223&postcount=16")

---

### Post by CaptSaltyJack on 2007-11-02
I'm having the same error as the original poster.  "Two file systems are assigned the same mount point"  Anyone know how to resolve this?

---

### Post by cyberdork33 on 2007-11-03
you should not be trying to mount any EFI filesystems.

look in /etc/fstab.

Take off any of the lines that are for the EFI partitions.
sda1, sdb1, etc. depending on the number of disks you have.

---

### Post by CaptSaltyJack on 2007-11-03
Cool, thanks.  Also, do I absolutely need rEFIt to dual boot Leopard and Ubuntu?  And, when Ubuntu asks me if I want Grub to install the bootloader, do I say yes? (and I should install it to which drive, exactly?  Will it mess up me booting into Leopard?)

---

### Post by cyberdork33 on 2007-11-03
> **CaptSaltyJack said:**
> Cool, thanks.  Also, do I absolutely need rEFIt to dual boot Leopard and Ubuntu?  And, when Ubuntu asks me if I want Grub to install the bootloader, do I say yes? (and I should install it to which drive, exactly?  Will it mess up me booting into Leopard?)
You do not need rEFIt, you can hold alt on each bootup instead.

install grub to the ubuntu partition or to the default location

it will not mess up leopard (Or tiger for that matter).

---

### Post by CaptSaltyJack on 2007-11-03
Awesome, thanks a ton!!

---

### Post by CaptSaltyJack on 2007-11-03
cyberdork: Ok, a bit of a problem.  fstab doesn't have anything about EFI.  Here's my /etc/fstab file:

```

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

```

But in the install window, when it shows the disks and partitions, I see four 209MB partitions (sda1, sdb1, sdc1, sdd1) that have a mount point of "/media/EFI system partition," even though listing the contents of /media shows nothing.

Any ideas?  In the install window that shows all the partitions, should I just choose one of the EFI partitions, click "Edit Partition" and change the mount point from /media/EFI System Partition to something else?

---

### Post by CaptSaltyJack on 2007-11-03
I figured it out, you just set the mount option to blank for the EFI partitions.. ignore the FAT errors, it installs fine.  The problem is, Grub installed the bootloader on hd0.. I think that was the wrong spot.  I installed Ubuntu on a partition on sdc, so I suppose I needed to change (hd0) to (hd2).  I noticed when I booted up the main (first) drive, Tiger, it said I needed to reboot my machine.. probably had to fix the MBR.  If I boot into Ubuntu, I just get a blinking cursor, so Grub didn't take.  Does this sound right?

---

### Post by cyberdork33 on 2007-11-03
> **CaptSaltyJack said:**
> cyberdork: Ok, a bit of a problem.  fstab doesn't have anything about EFI.  Here's my /etc/fstab file:

```

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

```But in the install window, when it shows the disks and partitions, I see four 209MB partitions (sda1, sdb1, sdc1, sdd1) that have a mount point of "/media/EFI system partition," even though listing the contents of /media shows nothing.

Any ideas?  In the install window that shows all the partitions, should I just choose one of the EFI partitions, click "Edit Partition" and change the mount point from /media/EFI System Partition to something else?

That is the cd's /etc/fstab

but you changed the mount points correctly.

It really shouldn't matter which you install grub too, but if it isn't working then I would try to change it. Tiger / Leopard doesn't use the MBR so it would have no reason to change it. OSX completely ignores it.

You can easily install grub wherever you want. in a terminal (from the live cd)
```
 grub
``````
grub> find /boot/grub/stage1
```Use the result of that in the next command:
```
grub> root (hd2,x)
``` Note this should be the partition on which the grub config files are located. Likely your Ubuntu root partition (or your /boot partition if  you made that separate).

Now install the bootloader to the MBR of sdc.
```
grub> setup (hd2)
```fini!
```
grub> quit
```
You might get an extra icon in rEFIt after this, but we can fix it, i just have to figure out how to clear the MBR.

---

### Post by CaptSaltyJack on 2007-11-03
Ahh man, I give up.  So, I followed your steps, and now an extra 'Windows' partition shows up in the Mac boot screen, great.. I choose it, and finally I see grub!  But it says "Error 22: No such partition" when I choose any of the entries.

I checked /boot/grub/menu.lst on the Ubuntu partition.  They all point to (hd2,3).  That seems right.  The third hard drive in the system has four partitions:

0: EFI
1: Leopard
2: Linux swap
3: ext3 Ubuntu partition

I don't understand why this isn't working.

---

### Post by CaptSaltyJack on 2007-11-03
Got it.  I edited the menu.lst and changed (hd2,3) to (hd0,3).  For some reason, it sees the third hard drive (sdc) as hd0.  I guess it's a relativity thing.

---

### Post by cyberdork33 on 2007-11-04
> **CaptSaltyJack said:**
> Got it.  I edited the menu.lst and changed (hd2,3) to (hd0,3).  For some reason, it sees the third hard drive (sdc) as hd0.  I guess it's a relativity thing. that is strange. hey if it works! So you still have an extra icon?

---

### Post by dasistwas on 2008-03-31
Hi,

I have a similar problem:

I have a Mac Pro, with two hard-disks.
First Harddisk: MAC OS X
Second: Ubuntu Hardy Heron.

I installed rEFIT, when I boot and choose to start Linux, it does only show a black screen. When I insert the Ubuntu install CD, and boot from the CD, then choose "Boot from first Hard Disk", Ubuntu starts normally from Hard Disk.

I want to use my Ubuntu without the install CD, how could I do this?
The following is the /boot/grub/menu.lst text:

```
title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=d7dec805-e7e9-41d2-9855-cf3e1b1b3dc2 ro quiet splash locale=de_DE
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=d7dec805-e7e9-41d2-9855-cf3e1b1b3dc2 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), kernel 2.6.24-11-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-11-generic root=UUID=d7dec805-e7e9-41d2-9855-cf3e1b1b3dc2 ro quiet splash locale=de_DE
initrd		/boot/initrd.img-2.6.24-11-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-11-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-11-generic root=UUID=d7dec805-e7e9-41d2-9855-cf3e1b1b3dc2 ro single
initrd		/boot/initrd.img-2.6.24-11-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
```

Should I change (hd1,0) to (hd2,0)?

Can I change the settings somewhere when I already started Ubuntu like in the Bootloader-Config section of Ubuntu?

Thanks for your help,
David

---

### Post by cyberdork33 on 2008-04-01
> **dasistwas said:**
> Should I change (hd1,0) to (hd2,0)?

Can I change the settings somewhere when I already started Ubuntu like in the Bootloader-Config section of Ubuntu?

Thanks for your help,
David
well hd2 would be hard drive 3, which you do not have...

I *think* that you should make it hd0,0. I know that seems weird. Just make a backup of the file first and you can copy it back if it doesn't work right.

---

