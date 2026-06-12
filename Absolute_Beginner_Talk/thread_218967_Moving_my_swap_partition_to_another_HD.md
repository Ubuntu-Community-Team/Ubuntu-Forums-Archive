---
title: "Moving my swap partition to another HD ?"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by Browser_ice on 2006-07-19
When I had created the partitions on both my HD, I was thinking about puting Ubuntu and its swap on the same HD. But now that I think of it, I think it would better from a performance point of view, if the swap partition was on the second HD.

How can I move it ?

---

### Post by thoolihan on 2006-07-19
assuming your first disk is hda and second disk is hdc ( you can verify this with   #dmesg | grep hd

create a partition of the size you want on /dev/hdc using fdisk
or whatever partition tool you like.
```

mkswap /dev/hdc1
swapon /dev/hdc1

```

Then edit /etc/fstab and change the line that says somthing like:
/dev/hda2 none swp  defaults 0 0
to use the new device:
/dev/hd**c1** none swp  defaults 0 0

Reboot and enjoy...

---

### Post by Browser_ice on 2006-07-27
If I use the Disks Manager, it shows I have 2 Linux Swap partitions : hdba5 and hdb10.  I had manualy formated hdb10 as memory swap but I guess the system isn't using it at all.  I want hdb10 to be my swap.

I need the answer as soon as possible. I am waiting for this to start doing an image for my whole PC while all installations are cleaned and fresh.


Do I simply update the /etc/fstab  and boot ???

browserice@browserice-desktop:~$ sudo mkswap /dev/hdb10
Password:
Setting up swapspace version 1, size = 10733953 kB
no label, UUID=fd8d4715-970f-43d6-953d-5889888d035c
browserice@browserice-desktop:~$ sudo swapon /dev/hdb10
browserice@browserice-desktop:~$ sudo edit /etc/fstab
Warning: unknown mime-type for "/etc/fstab" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
browserice@browserice-desktop:~$ edit /etc/fstab
Warning: unknown mime-type for "/etc/fstab" -- using "application/*"
Error: no write permission for file "/etc/fstab"

I guess I have to be a root user to edit that file ?  

[update1]
never minde for the permission. I did a sugo gedit /etc/fstab

I found a link talking about what I should do. Should I go ahead ?

0. If you haven't booted yet, use Grub's handy features to edit the boot command (press 'e', and read the instructions on the bottom. You should add "resume=/dev/hdxx" in the end of the line that begins with "kernel".
1. Edit "/etc/mkinitramfs/conf.d/resume" (needs sudo) to contain the right device address.
2. Run "sudo dpkg-reconfigure initramfs-tools" and wait a moment (it took about a minute for me, with one kernel installed).
3. Reboot, rejoice and start breathing again. (If it doesn't work, check the spelling everywhere, most of the stuff is case sensitive.)
[/update1]

browserice@browserice-desktop:~$ dmesg | grep hd
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179574.744000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb :DMA
[17179574.744000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd :DMA
[17179575.172000] hda: Maxtor 6Y080L0, ATA DISK drive
[17179575.456000] hdb: Maxtor 6L250R0, ATA DISK drive
[17179576.424000] hdc: HL-DT-ST DVDRAM GSA-4163B, ATAPI CD/DVD-ROM drive
[17179577.208000] hdd: LG CD-ROM CRD-8522B, ATAPI CD/DVD-ROM drive
[17179577.284000] hda: max request size: 128KiB
[17179577.296000] hda: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/1 6/63, UDMA(33)
[17179577.296000] hda: cache flushes supported
[17179577.296000]  hda: hda1 hda2 hda3 < hda5 >
[17179577.320000] hdb: max request size: 1024KiB
[17179577.324000] hdb: 490234752 sectors (251000 MB) w/16384KiB Cache, CHS=30515 /255/63, UDMA(33)
[17179577.324000] hdb: cache flushes supported
[17179577.324000]  hdb: hdb1 hdb2 < hdb5 hdb6 hdb7 hdb8 hdb9 hdb10 >
[17179577.424000] hdc: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.432000] hdd: ATAPI 52X CD-ROM drive, 128kB Cache, DMA
[17179591.132000] Adding 1582360k swap on /dev/hda5.  Priority:-1 extents:1 acro ss:1582360k
[17179591.252000] EXT3 FS on hda2, internal journal


browserice@browserice-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Browser_ice on 2006-07-27
Ok, I proceeded with the followings :

sudo mkswap /dev/hdb10
sudo swapon /dev/hdb10

sugo gedit /etc/fstab
[INDENT][FONT="Courier New"][SIZE="2"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb10      none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0[/SIZE][/FONT][/INDENT]

added "resume=/dev/hdb10" on the first kernel of my menu.lst

edited "/etc/mkinitramfs/conf.d/resume" to point to my hdb10

ran "sudo dpkg-reconfigure initramfs-tools" which took like 30 sec

rebooted. It seams a bit faster now.

Now my disks are :
[INDENT][FONT="Courier New"][SIZE="2"]browserice@browserice-desktop:~$ dmesg | grep hd
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash resume=/dev/hdb10
[17179575.816000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[17179575.816000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[17179576.244000] hda: Maxtor 6Y080L0, ATA DISK drive
[17179576.528000] hdb: Maxtor 6L250R0, ATA DISK drive
[17179577.496000] hdc: HL-DT-ST DVDRAM GSA-4163B, ATAPI CD/DVD-ROM drive
[17179578.280000] hdd: LG CD-ROM CRD-8522B, ATAPI CD/DVD-ROM drive
[17179578.356000] hda: max request size: 128KiB
[17179578.368000] hda: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
[17179578.368000] hda: cache flushes supported
[17179578.368000]  hda: hda1 hda2 hda3 < hda5 >
[17179578.392000] hdb: max request size: 1024KiB
[17179578.396000] hdb: 490234752 sectors (251000 MB) w/16384KiB Cache, CHS=30515/255/63, UDMA(33)
[17179578.396000] hdb: cache flushes supported
[17179578.396000]  hdb: hdb1 hdb2 < hdb5 hdb6 hdb7 hdb8 hdb9 hdb10 >
[17179578.496000] hdc: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179578.504000] hdd: ATAPI 52X CD-ROM drive, 128kB Cache, DMA
[17179592.236000] Adding 10482372k swap on /dev/hdb10.  Priority:-1 extents:1 across:10482372k
[17179592.356000] EXT3 FS on hda2, internal journal[/SIZE][/FONT][/INDENT]

Can I safely delete my /dev/hda5 ????
Everything is done and safe ???
What about that resume thing in my menu.lst ? DO I leave it there ?

---

### Post by BlueStreak on 2006-07-27
I'm curious, how would this improve performance?!?

---

### Post by -deadcats on 2006-07-27
> **BlueStreak said:**
> I'm curious, how would this improve performance?!?

Because (or so the theory goes) you're reading from one HDD while writing to another; instead of first reading then writing to the same HDD.

It's a fairly old practice. I first read about it in the early '90's in a book by Peter Norton.

regards,
-dc

---

### Post by BlueStreak on 2006-07-27
ok, I suppose that makes sense "theoretically". I don't mean to be a pain but would there be a tangible performance gain here?

---

### Post by -deadcats on 2006-07-27
> **BlueStreak said:**
> ok, I suppose that makes sense "theoretically". I don't mean to be a pain but would there be a tangible performance gain here?

I dunno. I suppose it all depends on file-size, HDD physical speed differences, blah, blah. But you know, every little bit helps when you're fine-tuning for performance (this from someone who used to spend hours reconfiguring autoexec.bat and config.sys files). The book title, or something like it, was the Hard Disc Companion by Peter Norton. And Peter Norton knows his stuff. Or "stuff" the way it was back then. ;) 
I suppose if the topic is of interest, there's probably a ton of it on the intarweb. There's also Gentoo, if your bent is to get all possible hell-bent-for-leather speed out of your rig. ;)

regards,
-dc

---

