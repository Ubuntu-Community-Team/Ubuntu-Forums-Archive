---
title: "system stops saying grub"
date: 2005-06-09
forum: Absolute Beginner Talk
---

### Post by hellohenk on 2005-06-09
Hi can someone help me please after installing Ubuntu starting for the first time the system say's Grub loading stage2, then Grub nothing else? someone told me that the version that i have is a correct one  see also a line  
**[minimal Bash-like line editing is supported for the first word, TAB list possible command completions. Anywhere else TAB list the possible completions of a device/filename] ** be very greatful with someone help.

---

### Post by Nimefurahi on 2005-06-09
Did you create a GRUB diskette during or after your Ubuntu installation?

How many hard disk drives are you using and what type are they (IDE, SCSI)?

Have you any other operating systems installed on your workstation?

Perhaps we can help you

---

### Post by hellohenk on 2005-06-09
Did you create a GRUB diskette during or after your Ubuntu installation?
No i did not!
How many hard disk drives are you using and what type are they (IDE, SCSI)?
Just one! and the type is IDE
Have you any other operating systems installed on your workstation?
There is no other OS installed just 1 unformatted disk Brand is Maxtor 19680 cylinders 16 heads 255 sectors 41111 MB
I hope you can help me?

---

### Post by poofyhairguy on 2005-06-09
[QUOTE=hellohenk]Hi can someone help me please after installing Ubuntu starting for the first time the system say's Grub loading stage2, then Grub nothing else? someone told me that the version that i have is a correct one  see also a line  
**[minimal Bash-like line editing is supported for the first word, TAB list possible command completions. Anywhere else TAB list the possible completions of a device/filename] ** be very greatful with someone help.[/QUOTE]

So when you try to install it, it won't boot afterwards? I'm a little confused.

---

### Post by Nimefurahi on 2005-06-10
Hellohenk,

So it seems as if the grub loader was installed, perhaps in the MBR or the first active partition of your singular IDE hard drive, but as much (or as little) of the GRUB loader that WAS installed, it seems to be incomplete (with additional stages missing) and without the luxury of a menu. If that would be the case, please don't panic. We'll work on restoring the menu later. First we need to bring up as much as you installed of Ubuntu with as much of the grub loader that is available to you.

Attempt to boot again. Your screen seems to go as far as displaying the GRUB command prompt:

    GNU GRUB  version 0.95  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub>

Immediately after the grub command prompt   (grub>)   type in   root (
and press the Tab key.

Your options will be displayed, perhaps something like:

grub> root (
 Possible disks are:  fd0 hd0

grub> root (

With your singular IDE hard drive, your choice should probably be hd0.

... so continue by typing hd0  immediately after the  (

(please forgive me, but that is hd0 ("zero") and NOT hdO (O as in "Ontario") .... please type in hd0  and press the Tab key again:

Your available formated partitions should be listed, along with an identifier of the file system for each of those partitions.

Here's hoping that you originally formatted your hard drive with two partitions, one to serve as the root partition "/" and another to serve as the swap partition.

The file system identifier for your root partition should be type 83. Your swap partion would be type 82.

Perhaps this will be in your case, (hd0,0) with a file system of type 83.

OK... at this point, let us take a break and please report back to your elder brother as much as you have discovered.

Be patient my friend.

Nimefurahi

---

### Post by Nimefurahi on 2005-06-10
As you described offline:

grub> root
(hd0,0): filesystem type is ext2fs, partition type 0X83

So I hope we can assume that this is your root partition with an ext2 file system. (If when you originally set up your disk, you partitioned additional areas for, let's say. /home or /usr, please let me know). But if this is a singular partition for your Ubuntu system, let's proceed:

Once again at the GRUB prompt, type  root (hd0,0)     (and press Enter)

Now, type in   kernel /boot/vmlinuz   and immediately press the Tab key.

I am hoping that the line automatically completes with something like:

kernel /boot/vmlinuz-2.6.10-5-386

This is assuming your system has the current kernel du jour. I suppose it doesn't really matter. All we need to see is that GRUB sees a kernel in your /boot directory.

So if after typing    kernel /boot/vmlinuz    and pressing the Tab key, you see something similar to  kernel /boot/vmlinuz-2.6.10-5-386, we are ready to proceed.

Type in whatever was reported in the step above  (i.e.  kernel /boot/vmlinuz-2.6.10-5-386) and continue typing   ro root=/dev/hda1  Press the Enter key.

In our example, this would look like:

kernel /boot/vmlinuz-2.6.10-5-386 ro root=/dev/hda1  (press Enter)

Good?

Ok, now carefully type in   initrd /boot/initrd  and press the Tab key.

With any luck, the auto completion will yield something like:

initrd /boot/initrd.img-2.6.10-5-386   (or something very similar)

If GRUB is happy with this, type in   boot   and press the Enter key.

Your Ubuntu should boot up.

If you have success with this, we will later proceed with reestablishing your GRUB menu, but let us take careful and small steps.

Nimefurahi

---

### Post by brickbat on 2005-06-10
Nimefurahi, you are a champion.  This is very educational.

ciao
bb

---

