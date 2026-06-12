---
title: "Feisty Won't Access my CD RW/DVD IDE Drive!"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Aurora@FleetBuzz on 2007-05-14
Just upgraded from Edgy to Feisty.  Everything went well until I tried to play a CD.  Although the CD icon appears on the Desktop, it only serves to open up the file system (nautilus).  I tried to mount it with this command: 
> sudo mount /media/cdrom0/ -o unhide
Here's what I got:
> [mntent]: warning: no final newline at the end of /etc/fstab
mount: block device /dev/cdrom is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/cdrom,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Here's a copy of my directories:
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2              5281348   3484896   1528168  70% /
varrun                  257752       100    257652   1% /var/run
varlock                 257752         0    257752   0% /var/lock
procbususb              257752        92    257660   1% /proc/bus/usb
udev                    257752        92    257660   1% /dev
devshm                  257752         0    257752   0% /dev/shm
lrm                     257752     33788    223964  14% /lib/modules/2.6.20-15-generic/volatile
/dev/sda4             71813692    184480  67981256   1% /documents
/dev/sda1             76870988  20369648  56501340  27% /windows


My computer is a Dell Dimension 8200 PC.  Any suggestions on getting access to the CD drive?

Is there a fix, or should I slick the 7.04 installation and return to Edgy?

---

### Post by Big_Croc7 on 2007-05-16
What exactly are you trying to do?  Are you trying to play an audio CD?  If an icon appears for it on the desktop, it is mounted, so no need to mount it again.  What do you see when you click on the icon?

---

### Post by Aurora@FleetBuzz on 2007-05-16
It opens up the file system.  Unfortunately, when I pop a CD ROM in the drive, nothing happens!

---

### Post by Big_Croc7 on 2007-05-17
Sorry, I don't quite understand what the problem is - that's what it's supposed to do!

It sounds like you might be trying to run a windows autoplay CDROM (one that loads a program automatically in Windows).  That dosen't work in Ubuntu, at least not easily, as linux and windows need different types of programs.

---

### Post by Terl on 2007-05-17
What is on the cd you are using?

---

### Post by Aurora@FleetBuzz on 2007-05-26
I apologize for not acknowledging your responses sooner.  I had to recover from a HD crash!  The problem was that Feisty wouldn't recognize my old IDE drive.  I ripped it out and re-installed Edgy.  I'm much happier.

---

