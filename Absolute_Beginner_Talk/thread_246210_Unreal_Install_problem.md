---
title: "Unreal Install problem"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Nico0020 on 2006-08-28
im new to linux but have a friend helping me.  I am trying to install Unreal Tournament 2004 which is linux supported.  i get the first disk installed and then it needs to switch disk, but the drive will not eject on its own nor my by command as i guess its being used.  
I am running on ubuntu 6.06 LTS - the Dapper Drake - released in June 2006 ona laptop if that helps any. thanks for your help, im enjoying linux very much so far.

---

### Post by fr0stbyte2 on 2006-09-02
I'm having this same issue. *bump*

---

### Post by RadixLecti on 2006-09-02
First: have you copied the linux installer to your computer? I think you have to do that when installing UT. That's probably your problem; Ubuntu wants to use the linux installer, while at the same time it wants the second CD.

Then, there's always the tough approach to ejecting the CD:

First, have a look at /etc/fstab with a text editor. Your cd is most often hdc.

Then, type sudo umount -l /dev/hdc
and after that, sudo eject /dev/hdc

---

### Post by steve.horsley on 2006-09-02
> First: have you copied the linux installer to your computer? I think you have to do that when installing UT. That's probably your problem; Ubuntu wants to use the linux installer, while at the same time it wants the second CD.

That's almost sertainly the issue. I vaguely remember that when I was installing UT2004 that I was ejecting the CDs by right-click and eject the CD icon on the desktop, without problems.

Make sure the next CD's icon appears on the desktop before pressing enter to continue the installer. If you OK before the disk has finished mounting, I seem to remember the installer gets upset.

---

