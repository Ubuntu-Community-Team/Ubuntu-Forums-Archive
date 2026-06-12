---
title: "[SOLVED] (Ya) GRUB harf disk error!"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by kkarad on 2007-11-05
Hello all,

As you apparently understood from the post's title my dual boot fails! :(

I 've got winXP with Ubuntu 7.10 and I use GRUB which was installed during the ubuntu installation proccess. 

When the Ubuntu installation completes (successfully) and after the reboot of the system, I get a "GRUB.10 hard disk error" message. 

One of the many ways to recover the system (which might give you a hinnt) is that I boot from Ubuntu Livce CD and I choose the boot from first hard disk (last) option. Then the GRUB boot option menu appears and I can choose the OS I want to use. It seems that grub is properly installed but it is not invoked!

Do you know what causes the problem and how I can fix it?

Just to give you some more information: 

1) I use a toshiba laptop - qosmio F10 with its latest bios version.
2) my partitions are the following: /dev/hda1 (windows, ntfs, 45 GB), /dev/hda2 (ubuntu 7 .10, ext3,9 GB) and swap (1.5 GB)
3) The '/boot' is located in the linux partition (under '/' root folder)

I tried to use the root (hd0,1), setup(hd0) and reboot. The action was executed successfully but the problem has not been dissappeared.

Best Regards,

Konstantinos

---

### Post by kyphi on 2007-11-05
You could try this in a terminal:

```
sudo grub
``` press 'Enter' - that will get you into grub.

```
find /boot/grub/stage1
``` press 'Enter' - that will tell you where grub is.  It will show a value like (hdX,Y).  Take note of X and Y.

```
root (hdX,Y)
``` insert the values for X and Y and press 'Enter'.

```
setup (hd0)
``` 0=zero and press 'Enter'.

```
quit
``` and press 'Enter'.

Press Ctrl + d to exit the terminal.

Reboot

---

### Post by kkarad on 2007-11-05
As explained in my initial post i have already tried this procedure but with no results! I forgot to mentioned that my /boot/grub/stage1 file is located at hda2 which is my linux partition

Regards,

Konstantinos

---

### Post by meierfra on 2007-11-05
Does the grub menu appear at boot-up?

Post the output of 

sudo fdisk -l

---

### Post by vivichrist on 2007-11-05
boot up the live cd and in a terminal mount the root partition on /media:

sudo mount /dev/bla /media (note: no number, bla might be hda, sdc, sda, etc.)

then:

sudo gedit /media/boot/grub/menu.list

to ensure all is ok

then:

grub-install --root-directory=/media /dev/bla

 or something ... you get the idea?

I've not had much luck installing grub or any other bootloader onto a partition if that is what you did?
need more info on this

---

### Post by kyphi on 2007-11-06
You seem to have made a mistake during your installation of Ubuntu and either placed GRUB onto the wrong partition or else the small portion of GRUB on your Windows partition is corrupted.

There is no need to reinstall, although you can do that, if you wish.

Boot from your Ubuntu disc and choose install.  When you get to Partitioning, choose Manual Partition.  Create the partitions for " / , /boot , swap but do not format them.  Complete the formatting process and click 'Yes' when you are asked to save the changes.  You will get an error message advising that the system could not install.  Keep selecting 'Continue' until you return to the installation menu.  Select 'Install Grub'.

After that, reboot.

---

### Post by kkarad on 2007-11-06
hello meierfra,

GRUB menu does not appear in my screen. I get immediately "GRUB hard disk error" message.

As you requested here are the results of the fdisk report:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf10af10a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5957    47849571    7  HPFS/NTFS
/dev/sda2            5958        7058     8843782+  83  Linux
/dev/sda4            7059        7296     1911735   82  Linux swap / Solaris

Hope this help you to help me! :D

---

### Post by kkarad on 2007-11-07
> **kyphi said:**
> You seem to have made a mistake during your installation of Ubuntu and either placed GRUB onto the wrong partition or else the small portion of GRUB on your Windows partition is corrupted.

There is no need to reinstall, although you can do that, if you wish.

Boot from your Ubuntu disc and choose install.  When you get to Partitioning, choose Manual Partition.  Create the partitions for " / , /boot , swap but do not format them.  Complete the formatting process and click 'Yes' when you are asked to save the changes.  You will get an error message advising that the system could not install.  Keep selecting 'Continue' until you return to the installation menu.  Select 'Install Grub'.

After that, reboot.


Is it necessary to create a partition for /boot ? the /boot in my machine is under the root folder "/". Do you think this is the cause of the problem?

---

### Post by kyphi on 2007-11-07
Follow the  installation instructions on your Ubuntu disc except for formatting.  Some distros use different configurations.

If you are not confident in restoring or installing GRUB via the live CD, you might prefer to get the Super Grub Boot Disk.

There is a lot of information at this URL

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by kkarad on 2007-11-11
Hello,

I finally managed to install succesfully the lilo boot loader!

I tried all the possible options with grub (SGD, etc) but it couldn't work. I was always getting the "GRUB Hard Disk Error" message.

Thanks for the help guys!

Regards,

Konstantinos

---

