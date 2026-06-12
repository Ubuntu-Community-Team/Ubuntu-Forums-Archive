---
title: "External hard disk problem"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by RogerD on 2006-10-22
Hi

I have an Western Digital My Book external usb hard drive. It used to give me no problems - I'd plug it in; it appeared on the desktop, and I could read and write to the drive without any difficulties.

But now I'm having problems. I first noticed something was wrong, when I plugged in the drive and it didn't appear on the desktop. I've subsequently found a way to make it appear on the desktop, and although I can open the drive and read files, I can't write to the drive. I'm not very knowledgeable abut the inner workings of Linux/Ubuntu, but my problem has forced me to explore the likes of "mount" and "df". Here's my "df" output when my hard drive isn't plugged in.

roger@roger-desktop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/hda3              49G  5.8G   43G  12% /
varrun                379M   76K  379M   1% /var/run
varlock               379M  4.0K  379M   1% /var/lock
udev                  379M  144K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   19M  361M   5% /lib/modules/2.6.15-27-386/volatile
/dev/hda1              27G  9.8G   17G  37% /media/hda1
roger@roger-desktop:~$

I think I understand this, /devhda3 is my Windows partition (I've got a dual-boot system) mounted at /, and dev/had1 is my linux partition mounted at /media/had1.

The mount command gives me:

roger@roger-desktop:~$ mount
/dev/hda3 on / type reiserfs (rw,notail)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
roger@roger-desktop:~$

So far, OK. Here's where things start to get a bit strange. If I now plug in my hard disk, nothing appears on the desktop, but Places>Computer produces a window showing all my drives including the My Book drive, complete with the Gnome footprint icon. However, if I try to open this drive, with a right mouse click, I get: Unable to mount the selected volume; show more details produces:

error: directory /media/my book is not empty

error: could not execute pmount

What I think the system is trying to tell, is that "My Book" is already mounted at /media/my book. Which is weird, because there's no change in the output of a mount command. Now things get even weirder.

System>Administration>Disks, prompts some activity on my external hard drive, the power light flashes, and I get a window on my desktop detailing all the drives on my system, including a WD 800BB EXternal, with device name /dev/sdb1, and access path /tmp/disks-conf-sdb1. Amazingly, the My Book icon now appears on my desktop, but although I can open and read files, I can't write to the drive. I get the message: "You do not have permissions to write to this folder."

The df command now produces:

roger@roger-desktop:~$ df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/hda3             50881384   5989964  44891420  12% /
varrun                  388000        76    387924   1% /var/run
varlock                 388000         4    387996   1% /var/lock
udev                    388000       144    387856   1% /dev
devshm                  388000         0    388000   0% /dev/shm
lrm                     388000     18856    369144   5% /lib/modules/2.6.15-27-386/volatile
/dev/hda1             27812856  10173192  17639664  37% /media/hda1
/dev/sdb1             78121024  22262432  55858592  29% /tmp/disks-conf-sdb1
roger@roger-desktop:~$

Showing that I now have a new device on my system, and mount produces:

roger@roger-desktop:~$ mount
/dev/hda3 on / type reiserfs (rw,notail)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sdb1 on /tmp/disks-conf-sdb1 type vfat (rw)
roger@roger-desktop:~$

Indicating that my external drive is mounted in /tmp and that it seems to be read-write. Which is all a bit strange. If I insert a usb flash drive into my machine, it will be mounted in /media, not /tmp. Also, if the drive is read-write, why can't I copy files to it?

I don't understand what's going on here, but it seems that, in some way, my system still thinks My Book is mounted in /media, which, presumably, is why the drive is being mounted in /tmp.

Any help in advising how to restore my system to its former state, why My Book appearing directly on my desktop in a read-write state would be much appreciate.

Roger D

---

