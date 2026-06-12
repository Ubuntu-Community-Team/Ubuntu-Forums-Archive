---
title: "How to access my windows partition?"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-10-13
Hi,
Im trying to access my windows partition from ubuntu (7.10) and normally there's a very handy icon on the desktop but recentley it's disapeared :confused: does anyone know how i can access the partition so i can play or open files from it? or even get the icon back. :KS

Thanx in advance,

So far a very happy linux user :P

---

### Post by Dr Small on 2007-10-13
I generally open Nautilus, and on the left hand side bar, I see the drive listed under "File System" and "Floppy 1", and it usually right there.

Dr Small

---

### Post by Pumalite on 2007-10-13
It's probably mounted in /media. At this point you have read only access. For read/write, install ntfs-3g
sudo apt-get install ntfs-3g

---

### Post by kamitsukai on 2007-10-13
> **Pumalite said:**
> It's probably mounted in /media. At this point you have read only access. For read/write, install ntfs-3g
sudo apt-get install ntfs-3g

well i "googled it" and alot of posts said that it was under media but i only have an empty folder? 

ps: i love the way i posted this like 3miniutes ago an i already have 2 replys!

---

### Post by Pumalite on 2007-10-13
Post:
sudo fdisk -lu

---

### Post by kamitsukai on 2007-10-13
```
carl@carl-laptop:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf6bca237

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   109563299    54780626    7  HPFS/NTFS
/dev/sda2       109563300   151187714    20812207+  83  Linux
/dev/sda3       151187715   156296384     2554335   82  Linux swap / Solaris
```

thanx for helping:KS

---

### Post by Pumalite on 2007-10-13
At the Terminal:
sudo mkdir /media/sda1
sudo mount -t ntfs /dev/sda1 /media/sda1

---

### Post by kamitsukai on 2007-10-13
```
carl@carl-laptop:~$ sudo mkdir /media/sda1
mkdir: cannot create directory `/media/sda1': File exists
carl@carl-laptop:~$ sudo mount -t ntfs /dev/sda1 /media/sda1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0
carl@carl-laptop:~$ 

```

hmmmm... ill try the options it gives and see if they work

---

### Post by duckblind123 on 2007-10-13
I am running Ubuntu 6.06 LTS and I also ran the sudo fdisk -lu command:

mjdesktop@mjdesktop:~$ sudo fdisk -lu

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    39712679    19856308+   7  HPFS/NTFS
/dev/hda2        39712680    76662179    18474750   83  Linux
/dev/hda3        76662180    78156224      747022+   5  Extended
/dev/hda5        76662243    78156224      746991   82  Linux swap / Solaris

Is it possible to access any of my Windows partition files from the Ubuntu side?
FYI:  I am really new to Ubuntu, but am very anxious to learn more about it.
Thanks, duckblind123

---

### Post by Pumalite on 2007-10-13
The first error says that you already have directory sda1. Look for it. You can also try at the Terminal:
mount

To find out what is really mounted at the moment.

---

### Post by kamitsukai on 2007-10-13
i discovered the problem! its vista...grrr if i choose restart instead of shutdown it doesent shutdown properly an courses problems with ubuntu.

thank you pumalite):P

---

### Post by duckblind123 on 2007-10-13
Okay, I do see the hda1 as listed in the sudo fdisk -lu, but when I ran the mount, Iget:
mjdesktop@mjdesktop:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-29-386/volatile type tmpfs (rw)

I only see the hda2 mounted.  What would be the correct method for mounting
the hda1?
Thanks, duckblind123

---

### Post by Pumalite on 2007-10-13
> **duckblind123 said:**
> I am running Ubuntu 6.06 LTS and I also ran the sudo fdisk -lu command:

mjdesktop@mjdesktop:~$ sudo fdisk -lu

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    39712679    19856308+   7  HPFS/NTFS
/dev/hda2        39712680    76662179    18474750   83  Linux
/dev/hda3        76662180    78156224      747022+   5  Extended
/dev/hda5        76662243    78156224      746991   82  Linux swap / Solaris

Is it possible to access any of my Windows partition files from the Ubuntu side?
FYI:  I am really new to Ubuntu, but am very anxious to learn more about it.
Thanks, duckblind123

At the Terminal:
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda1 /media/windows

---

