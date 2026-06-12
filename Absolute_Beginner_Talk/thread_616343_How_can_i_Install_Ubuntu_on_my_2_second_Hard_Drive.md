---
title: "How can i Install Ubuntu on my 2 second Hard Drive"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by pinno7 on 2007-11-18
Hi all 

i am running Win vista ultimate

i have 120gb hard drive for win vista, plus I've added a matching 120gb Maxtor Diamond hard drive

i need really detailed steps on how to do this please. 

Heres what i need.

l would like to  Install Ubuntu on my 2 second Hard Drive (i have a second internal hard drive, and if i can, i would like to use that.)

Have win vista  boot automatically when i turn on my computer, but  how can have the option to boot into ubuntu thorugh the boot menu to second hard drive.

How can i lstall Ubuntu 7.04 to my Dell Dimension 4550
1gb RAM, Intel 2.4ghz P4 processor


l'm very Newbie please guide me  through  step-by-step
that would be very  much appreciated.

---

### Post by Pumalite on 2007-11-18
Just install to 2nd hard drive and install Grub in that drive (at step 8, Advanced Tab, instead of (hd0), type (hd1,0). Use 'Guided>Use Entire Disk'. Later you have to modify your boot.ini in Vista to have access to Ubuntu.

---

### Post by torgrot on 2007-11-18
Or better yet swap the hard drives, install ubuntu to the new drive and it will detect WinVista on the second and create the grub menu.lst with the option to boot it.  Then you don't have to mess with your WinVista drive at all.  It will just work.

torgrot

---

### Post by tyggna1 on 2007-11-18
Vista doesn't have a boot.ini.  It uses a boot database.   Your best bet is to just install it on the drive you want (you'll have to know which is which) and then learn how to edit/change the grub boot order to have windows as default.

---

### Post by mdpalow on 2007-11-18
When you run the Live CD and click the 'install' icon, you will come to a partition windows after answering a few simple questions.

Select the "Manual" option.

Be very careful now...

Look at the currently listed drives; you should now see two hard drives.

You'll recognize your Vista disk by the size displayed and it'll probably be shown as "sda1."

Whichever it is or comes up as - do NOT click on it or do anything to it. Just leave it (Windows) alone.

You'll see another drive listed with some amount of free space depending on size of your drive.

Click that one and create a partition that is between 7000 - 10000 megs (7-10 gigs). Use 'beginning,' and ext3, and be sure to use ' / ' for the mount point.

Then create another partition on that hard drive and create a partition that uses all, but 2000 megs of the remaining space left on that drive. Use 'beginning,' and ext3, and be sure to use ' / home' for the mount point.

Then use the remaining 2000 megs (2 gigs) and create a new partition and instead of selecting ext3, make it swap.

Ubuntu will take care of the rest...

good luck

---

### Post by pinno7 on 2007-11-18
Hi thanks all of you for quit replys..

Have treid to insttal it but l got this messg

Busybox V1.1.3(debian 1:1.1.3-5ubuntu4) Buit-in shell (ash)
Enter "Help' for a list of built-in-comands

/bin/sh: can't access tty; job control turned off
(initramfs)

Can anyone please point me in the right direction? I'm getting frustrated... I can't wait to get linux running on my 2end hard drive ..
Thank you for your help...

---

### Post by Pumalite on 2007-11-18
Post your complete specs.

---

### Post by pinno7 on 2007-11-18
1gb RAM 
Intel 2.4ghz P4 processor 

Disk Drives:
Maxtor 6Y120L0 ATA Device

Dispayer adapters:
Gigabyte Radeon 9660PRO

dvd/cd-rOMS Drives
Philips PBDV1640P ATA Device
TSST copr DVD-ROM TS-H352 ATA DEVICE

Floppy disk drive

Network card
Inte(R) pro/100 VE 

SoundMax Integrated Audio

Microsoft Window Vista ultimate 

But as i said  post 1 
l would like to Install Ubuntu on my 2 second Hard Drive , but infortunalty get this messg above post 6.Thx

---

### Post by Pumalite on 2007-11-18
Try the Alternate CD.

---

