---
title: "New Hard Drive"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Arukas on 2007-09-30
Hello,

I have added a new harddrive to my computer.  The problem is Ubuntu will not write to it only read.  I want both of my OS to write to it.  Anyone know how to fix that so, Ubuntu can read and write, while XP can still read and write too?


Thanks-
Arukas

---

### Post by mivo on 2007-09-30
Three choices:

1) You format it in FAT32.
2) You format it in NTFS and install an NTFS driver in Linux. (Package: ntfs-3g)
3) You format it in ext2 and install an ext2 driver in Windows. ([http://www.fs-driver.org/](http://www.fs-driver.org/))

---

### Post by cotcot on 2007-09-30
What file system do you have on the new drive ?  (if ntfs then install ntfs-3g to be able to write to it)

Otherwise it would be helpfull to post the content your /etc/fstab and tell what the name of the new drive is
Fstab is the file telling ubuntu how to mount partitions (read only, fully accessible ...)

---

### Post by Arukas on 2007-09-30
hello,

I install ntfs drivers, and I still can't right to my hard drive, it can see it, but cannot write to it at all.  

I do not understand what you are asking me to post, I am still a newbie when it comes to what linux does.

-Arukas

---

### Post by Gone fishing on 2007-09-30
NTFS is a problem, it's an MS file system and they don't release the specs source etc – this makes it tricky to write a  Linux driver. The original Linux driver for NTFS could read but not write to NTFS, however, the new ntfs-3g driver allows both read and write (these Linux devs are clever fellows) so thats the driver you need.

Automatix will install this driver and setup the scripts so you can write to the drive, I am, however, loath to recommend Automatix, so it's your call.

---

### Post by Arukas on 2007-09-30
Why do i need automatix?  I used synatpic to install the drivers, how come that don't work?

-Arukas

---

### Post by cotcot on 2007-09-30
Take your time to read [[COLOR="Red"]this[/COLOR]]("http://www.psychocats.net/ubuntu/mountwindows") and tell us if this is helping you.

---

### Post by Arukas on 2007-09-30
that seems more complicated, i went the other way around, and made windows read the linux partition.  It seems more simpliar.   

However, I need to figure out how to keep windows from making unwanted changes in LInux.

-Arukas

---

### Post by Gone fishing on 2007-10-01
You don't need Automatix but once you've added the ntfs-3g drivers it modifies the fstab file so you can use the windows partition without you needing to know how to do this, although you would find help on this forum etc.

I have created an extra ext3 which both Windows and Ubuntu can read I also had to add this to the fstab  file and mounted it in Windows as Drive X (the Windows ext3 driver seems to work perfectly)  I didn't mount the root Ubuntu partition in Windows so no danger of Windows changing anything.

---

### Post by ronald.higgins on 2007-10-01
Did you run ntfs-config to configure write access ?

---

