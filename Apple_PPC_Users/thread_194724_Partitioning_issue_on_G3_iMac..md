---
title: "Partitioning issue on G3 iMac."
date: 2006-06-11
forum: Apple PPC Users
---

### Post by ebeyer on 2006-06-11
I have a G3 iMac/233 MHz which I upgraded with an 80 Gb HD.  My goal is to be able to boot OS X and 3 or 4 linux distributions.  Constraints I know about are (1) OS X needs to be installed into the first 8 Gb of the HD; (2) There needs to be a partition exactly 100.0 Mb in size which is before the Linux partition and which has '/boot' set as its mount point; (3) I need a partition of about ~200 megs as a swap file partition.

What I did was I installed OS X, partitoning (more or less) as follows:

1. 7 Gb - OS X partiton 1
2. ~23 Gb - OS X partition 2
3. 100.0 Mb - Ubuntu boot partition (newworld, bootable).
4. 100.0 Mb - Ubuntu eta3 partition #1 with /boot mountpoint; set to be bootable.
5. ~10 Gigs - Ubuntu eta3 partiton
6. ~10 Gigs - Future linux partition space
7. ~10 Gigs - Future linux partition space
8. ~10 Gigs - Future linux partition space

These figures are not exact - I used up the 80 with these partitions.

OS X installed just fine and I installed all of the updates before continuing.

I installed Ubuntu and, using manual partitioning, set up partitions 3-5 as above.  Phase 1 of installation went OK.  The CD was automatically ejected and the system rebooted, at which point I was presented with ...

.. a blank, grey screen.

So ... did I mess up my partitioning or is there something else I need to do differently?

---

### Post by nkbj on 2006-06-11
Seems that you were bitten by the same bug as a bunch of other people: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508)

Regards,
Niels Kristian

---

### Post by tidris on 2006-06-12
I think you have some bad information regarding the partitions that Ubuntu needs.

I am assuming your machine is NewWorld. Do you know if it is?

There needs to be a bootable partition, but its size is only 1 MB, not 100 MB. That partition needs to have the bootable flag set and Apple_Bootstrap is its type. The yaboot bootloader is installed there. Contrary to what you might have read in other threads, the Ubuntu installer is perfectly capable of creating it for you if you use the automatic partitioning option in the installer.

Ubunutu doesn't need a bootable partition with /boot mount point. I don't have one on my G5 or my PowerBook G3 and Ubuntu is as happy as it can be on both machines.

I didn't see a swap partition in your list of partitions, and that might be part of your problem.

It would be useful if you can post the /etc/yaboot.conf file that was installed in the Ubuntu root partition (I believe that would be partition 5 in your list). You can access that file by booting from the live desktop CD and then mouting that partition.

From my experience the easiest and most foolproof way of installing Ubuntu is to create free  space in the disk and then allowing Ubuntu to automatically create all the partitions it needs in the free space.

---

### Post by ebeyer on 2006-06-12
[QUOTE=nkbj]Seems that you were bitten by the same bug as a bunch of other people: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508)

Regards,
Niels Kristian[/QUOTE]


Well, no.. To be totally honest, I was bitten by this a few install attempts ago.  I'm actually trying to install Breezy and am deferring upgrading until this bug is worked out.  I figured this partitioning issue was broad enough that it wouldn't matter which version we were talking about.

---

### Post by ebeyer on 2006-06-12
[QUOTE=tidris]I think you have some bad information regarding the partitions that Ubuntu needs.

I am assuming your machine is NewWorld. Do you know if it is?

There needs to be a bootable partition, but its size is only 1 MB, not 100 MB. That partition needs to have the bootable flag set and Apple_Bootstrap it its type. The yaboot bootloader is installed there. Contrary to what you might have read in other threads, the Ubuntu installer is perfectly capable of creating it for you if you use the automatic partitioning option in the installer.

Ubunutu doesn't need a bootable partition with /boot mount point. I don't have one on my G5 or my PowerBook G3 and Ubuntu is as happy as it can be on both machines.

I didn't see a swap partition in your list of partitions, and that might be part of your problem.

It would be useful if you can post the /etc/yaboot.conf file that was installed in the Ubuntu root partition (I believe that would be partition 5 in your list). You can access that file by booting from the live desktop CD and then mouting that partition.

From my experience the easiest and most foolproof way of installing Ubuntu is to create free  space in the disk and then allowing Ubuntu to automatically create all the partitions it needs in the free space.[/QUOTE]

1. It is new world.  It's a bondi-blue iMac G3.
2. I may have goofed and said 100 Mb.  I'm pretty sure the newworld boot partition is 1 Mb, but I'll have to go back and look.
3. There is a swap partition, which I created by leaving the space where the main Ubuntu partition was to go and letting the installer automatically partition that space.  I think it came to something like 234 Mb.
4. OK.  This could be my problem.  I have an Apple bootstrap partition at the very beginning of the drive (~23 kB); then the 7.9 Gb Apple boot partition; then the 20+ gig OS X partition; then a new-world boot partition ~ 1 Mb.

So it sounds like you are saying I shouldn't have a "new world boot partition" but rather I should be using the Apple Bootstrap for that purpose?  If so, then I'll need to enlarge that partition to hold one or more kernels.

Thanks.

---

### Post by tidris on 2006-06-12
[QUOTE=ebeyer]1. It is new world.  It's a bondi-blue iMac G3.
2. I may have goofed and said 100 Mb.  I'm pretty sure the newworld boot partition is 1 Mb, but I'll have to go back and look.
3. There is a swap partition, which I created by leaving the space where the main Ubuntu partition was to go and letting the installer automatically partition that space.  I think it came to something like 234 Mb.
4. OK.  This could be my problem.  I have an Apple bootstrap partition at the very beginning of the drive (~23 kB); then the 7.9 Gb Apple boot partition; then the 20+ gig OS X partition; then a new-world boot partition ~ 1 Mb.

So it sounds like you are saying I shouldn't have a "new world boot partition" but rather I should be using the Apple Bootstrap for that purpose?  If so, then I'll need to enlarge that partition to hold one or more kernels.

Thanks.[/QUOTE]

Here is the partition map for my G3 Powerbook.

        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2          Apple_Driver43 Macintosh                56 @ 64       ( 28.0k)  Driver 4.3
/dev/hda3          Apple_Driver43 Macintosh                56 @ 120      ( 28.0k)  Driver 4.3
/dev/hda4        Apple_Driver_ATA Macintosh                56 @ 176      ( 28.0k)  Unknown
/dev/hda5        Apple_Driver_ATA Macintosh                56 @ 232      ( 28.0k)  Unknown
/dev/hda6          Apple_FWDriver Macintosh               512 @ 288      (256.0k)  Unknown
/dev/hda7      Apple_Driver_IOKit Macintosh               512 @ 800      (256.0k)  Unknown
/dev/hda8           Apple_Patches Patch Partition         512 @ 1312     (256.0k)  Unknown
/dev/hda9         Apple_Bootstrap untitled               1954 @ 1824     (977.0k)  NewWorld bootblock
/dev/hda10        Apple_UNIX_SVR2 untitled           11316407 @ 3778     (  5.4G)  Linux native
/dev/hda11              Apple_HFS Apple_HFS_Untitled_5 23551664 @ 11881536 ( 11.2G)  HFS
/dev/hda12        Apple_UNIX_SVR2 swap                 561351 @ 11320185 (274.1M)  Linux swap
/dev/hda13             Apple_Free Extra                    16 @ 35433200 (  8.0k)  Free space

The disk was originally 100% OSX. I created around 6GB free space in it by reducing the size of the main OSX partition, then had the Ubuntu installer automatically partition the 6GB free space. The installer created these partitions:
- Apple_Bootstrap 977KB (NewWorld bootblock), 
- Appple_UNIX_SVR2 5.4GB which is the Ubuntu root,
- Apple_UNIX_SVR2 274MB which is the Ubuntu swap. 

The yaboot bootloader is installed in the Apple_Bootstrap partition. The LINUX kernel is not in that partition, but in the Ubuntu root partition. That is why the Apple_Bootstrap partition only has to be 1 MB in size.

If you are able to boot from the Ubuntu live CD, open a terminal window and type man bootstrap. That will give you a lot of useful info regarding the boot process and partitions needed. 

In particular, it says in there that the bootable Apple_Boostrap partition that contains yaboot needs  to be before any MacOS partition, otherwise OpenFirware will boot from MacOS instead of yaboot. However, your problem seems to be that the machine doesn't boot at all, right? That is why I asked to see the /etc/yaboot.conf file that should have been installed in the Ubuntu root partition.

---

### Post by EuroCity on 2006-06-12
The original iMac, as the beige G3 tower, must have the OS kernel within the first 8 GB of the hard disk, in order to be able to successfully boot the system: so, you must set up a partition scheme that not only has OS X within the first 8 GB (otherwise, you can't even install it from the CDs), but also, similarly, the Linux (Ubuntu) kernel. 

So, if you also have OS X (which takes up quite some gigabytes), the best option is to create a Linux /boot partition (where the kernels will be stored) immediately before or after the OS main partition, and anyway always before the end of the first 8 GB of the hard disk: the size of 100 MB (recommended on the Terrasoft/Yellow Dog site) isn't at all mandatory, but could be a good compromise (maybe it could even be smaller, say 32 MB+, similarly to the SUSE Linux "suseboot" HFS partition).

The Apple_Bootstrap partition is an entirely different matter: it should, ideally, be the first partition after the partition map itself, and only needs to be 1 MB (or even 800 KB, according to Debian) in size.

The bootstrap partition holds the yaboot bootloader; the /boot partition holds the kernel, but really only for those machines that have the (in)famous 8 GB limit.

It's obvious that those computers that don't have this 8 GB limitation don't need a /boot partition...

---

### Post by tidris on 2006-06-12
[QUOTE=EuroCity]
So, if you also have OS X (which takes up quite some gigabytes), the best option is to create a Linux /boot partition (where the kernels will be stored) immediately before or after the OS main partition, and anyway always before the end of the first 8 GB of the hard disk: the size of 100 MB (recommended on the Terrasoft/Yellow Dog site) isn't at all mandatory, but could be a good compromise (maybe it could even be smaller, say 32 MB+, similarly to the SUSE Linux "suseboot" HFS partition).
[/QUOTE]

Well, that makes sense to me. Does the yaboot.conf file created by the Ubuntu installer need to be hand tweaked to work with that partition scheme? Does the /boot partition need to be bootable? Does the Ubuntu installer copy the kernel images to the /boot partition or is that something that has to be done by hand?

---

### Post by EuroCity on 2006-06-13
I have never tried all this with an old iMac (even if I actually have one as my second computer), but it should all be automatic, once the bootstrap partition (with no mount point!) is marked as bootable and the /boot partition, formatted as ext3, has its mount point set as /boot: if the mount point is correct, then all subsequent kernel updates, etc. should automatically go into that partition (exactly as if it were an ordinary folder on the root partition, as it usually happens with newer computers, without the 8 GB limit).

---

