---
title: "How to know when &amp; whether GRUB/MBR needs work"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-09-13
I read at:

phbc50/howtos/how-to reinstall grub

[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)

How to Reinstall GRUB. 

But I don't really know what went wrong and don't want to make matters worse.

I had a 40 gig disk, as pri. master.  I had a 10 gig as pri. slave. Both where Ubuntu. Feisty on the big one Dapper on the little one.

I read here at the forums about adding a windows drive. Most of what I thought I understood was about adding a section to the Grub (/boot/grub/menu.lst) about the windows drive. I did this.

I removed the former slave (Dapper) and put in a Win98 disk, with jumpers set properly. Rebooted. Nothing. the former menu of various kernels was not the same. Selecting something did nothing. 

I have removed the 40 gig pri. master, put the former 10 gig pri. slave in as pri. master. Next I reinstalled Feisty. Brought all on this disk "up to date" via Synpatic.

Now I want to work on the 40 gig. 

How do I know whether the MBR or GRUB need modifying? How do I fix this?

If I reattach the 40 gig as pri. slave, how can I "inspect" or check it's MBR / GRUB?

---

### Post by dwhitney67 on 2007-09-13
I believe that the MBR GRUB will reference the menu.lst file in the /boot/grub directory of your primary drive.  This is an ASCII file that you can edit, however do be careful!

Within the menu.lst file are entry points for the one or more kernels, distros, Windows, etc that are available on your system.  If you were unable to boot into Windows when you swapped drives, this is probably because the menu.lst did not have an entry for such, or an entry within the file conflicts with how the Windows HDD is setup.

---

### Post by Mark_in_Hollywood on 2007-09-13
Thanks for your input, that's all very factual and nothing you talk about could cause me to harm my system further, but, there is no help with solving the problems. 

How do I "fix" the mbr for the particular set of disks, optical drives, or what have you that both MBR and GRUB need?

Is it possible to inspect the MBR for faults?

Is there a Grub template or something to work from?

Has anybody reading this tried SuperGrub or SystemRescueCD?

---

### Post by mlentink on 2007-09-13
Would [this]("http://en.wikipedia.org/wiki/Master_Boot_Record") help at all?

---

### Post by dwhitney67 on 2007-09-13
> **Mark_in_Hollywood said:**
> Thanks for your input, that's all very factual and nothing you talk about could cause me to harm my system further, but, there is no help with solving the problems. 

How do I "fix" the mbr for the particular set of disks, optical drives, or what have you that both MBR and GRUB need?

Is it possible to inspect the MBR for faults?

Is there a Grub template or something to work from?

Has anybody reading this tried SuperGrub or SystemRescueCD?

Here's a script the my employer uses to write grub to the MBR.  I do not know if it helps:

[PHP]#!/bin/sh

ROOT_DIR=/mnt
DEVICE_MAP=$ROOT_DIR/boot/grub/device.map
GRUB_RAW=/boot/grub
GRUB_DIR=$ROOT_DIR/$GRUB_RAW

# Prepare...
mkdir -p $GRUB_DIR
rm -f $DEVICE_MAP

# Create device map
/sbin/grub --device-map=$DEVICE_MAP --batch <<EOF #> /dev/null 2> /dev/null
quit
EOF

# Copy files
for a in stage1 e2fs_stage1_5 stage2
do
  cp $ROOT_DIR/usr/share/grub/i386-pc/$a $GRUB_DIR
done

# Install
/sbin/grub --batch --device-map=$DEVICE_MAP <<EOF #> /dev/null 2> /dev/null
root (hd0,0)
setup --stage2=$GRUB_DIR/stage2 --prefix=$GRUB_RAW (hd0)
quit
EOF[/PHP]

---

### Post by Mark_in_Hollywood on 2007-09-13
I believe I have not put the question as to how to solve this problem correctly to the community. That is my fault. I will try to reform the question and post again another time.

---

### Post by logos34 on 2007-09-13
Hopefully these links will answer your questions:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

