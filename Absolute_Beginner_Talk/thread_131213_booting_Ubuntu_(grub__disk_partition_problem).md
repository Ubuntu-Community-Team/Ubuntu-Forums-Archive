---
title: "booting Ubuntu (grub / disk partition problem?)"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by jichikawa on 2006-02-16
Hello,

I am trying to install and boot Ubuntu on a multiboot system which is partitioned something like this:

hda1: Mandrake 9.1 root directory
hda5: swap
hda6 : Mandrake 9.1 /home
hda7 : FAT32 (shared between Linux and Windows)
hda8 : empty (formatted Linux)
hda9 : Ubuntu (newly installed)

hdb:  several FAT32 partitions for Windows

The problem:  Ubuntu fails to boot.  Here's a quick summary:

1. modified LILO to include Ubuntu option.  Reboot, chose Ubuntu, got a message "Loading Ubuntu" and locked up.

2. created a boot floppy during Ubuntu installation, rather than writing GRUB.  Booting from the floppy gave a "GRUB" message and locked up.

3. created a "grub booter floppy" following these instructions [here]("http://www.troubleshooters.com/linux/grub/grub.htm").  Booted from the floppy, got the grub prompt.  But when I tried to specify the Ubuntu partition by typing:  root (hd0,8) - it locks up.

So at this point I'm just trying to understand why #3 doesn't work.  I'm guessing that #1 and #2 are failing for the same reason.

Doing #3 with my Mandrake partitions is ok - (hd0,0) or (hd0,1) or (hd0,5) works no problem.  Typing (hd0,7) also causes lock up.

Any ideas why grub can't seem to use this partition (hda8)?  I've also tried installing Ubuntu on to hda7 with similar non-success.

I checked my partitions and don't see any problems like overlapping sectors, etc.    My only guess at this point is maybe grub doesn't like anything 'past' the FAT32 partition?  

I've been able to mount and view the installed Ubuntu directories after booting into Mandrake.  Just can't seem to boot into Ubuntu.

[FONT="Courier New"][/FONT][SIZE="2"]Partition Table for /dev/hda
                                                                                                               
            First    Last
 # Type     Sector   Sector   Offset  Length   Filesystem Type (ID)   Flags
-- ------- -------- --------- ------ --------- ---------------------- ---------
 1 Primary        0 16384031      63 16384032  Linux (83)             Boot (80)
   Pri/Log 16384032 16384093*      0       62* Free Space             None (00)
 2 Primary 16384094*195090335       0 178706242* Extended (05)          None (00)
 5 Logical 16384094*20480543       1# 4096450* Linux swap (82)        None (00)
 6 Logical 20480544 122881247      63 102400704  Linux (83)             None (00)
 7 Logical 122881248 163840319      63 40959072  Win95 FAT32 (0B)       None (00)
 8 Logical 163840320 179465327      63 15625008  Linux (83)             None (00)
 9 Logical 179465328 195090335      63 15625008  Linux (83)             None (00)
   Pri/Log 195090336 240121727       0 45031392  Free Space             None (00)[/SIZE]

Please let me know if you think of any causes or ideas on working through this.  Thanks!

---

### Post by steve.horsley on 2006-02-16
I can think of two possibilities. One may be that beyond hda6 may be beyond where GRUB can address, if this is a very large disk. I don't know if GRUB has limits let alone what they are, but it's a thought, and may depend on the BIOS settings. I vaguely remember seeing mention if making sure the BIOS is set for LBA mode but again I'm hazy on the details. If this is the problem, I have no solution to offer.

Second possibility is that the Ubuntu install didn't go right, and the hda9 partition is screwed. Try mounting it from Mandy, and checking that it has sensible-looking contents.

---

### Post by jichikawa on 2006-02-16
Thanks.  Regarding the possibilities you mentioned:

1. I considered the 1024 cylinder limit as well, but as far as I can tell, booting from floppy is not supposed to have this problem.  (If I remember correctly, "Running Linux" suggested the floppy option if LILO ran into this limit problem.)   Also, I'm using version 22.4 of LILO, I believe the 1024 cylinder limitation was worked out in version 21.

2. I did mount from Mandrake and looked at the Ubuntu partition.  As far as I could tell, things looked ok - I saw the /boot/image-vmlinuz-xxxxxx sitting there.

Last night I also tried booting with the Ubuntu Live CD which seemed to work ok.

---

### Post by cotcot on 2006-02-16
As you get the grub prompt , can you boot manually ?

grub> kernel /vlminuz root=/dev/hda9

---

### Post by jichikawa on 2006-02-16
I'll give this a try, but suspect it will freeze like before since simply typing > root (hd0,8) caused it to freeze.  But who knows...

---

### Post by jichikawa on 2006-02-16
I do get the grub prompt, but typing in the line you suggested:

grub > kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda9

gives me an "Error 17: Cannot mount selected partition".  (actually I added the /boot prior to vmlinuz since this is how the kernel is located.)

If I've read other sources correctly, I believe I need to specify which partition contains the kernel, either by:

a)  grub > root (hd0,8)

or

b) grub > kernel (hd0,8)/vmlinuz-2.6.12-9-386 root=/dev/hda9

And both a) and b) result in the same lockup.

This is getting very frustrating ... 

Could the problem be with GRUB?  Is there a similar LILO command line entry method that I could try out?

---

