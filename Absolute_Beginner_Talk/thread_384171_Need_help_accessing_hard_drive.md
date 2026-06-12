---
title: "Need help accessing hard drive"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by morbidAUS on 2007-03-14
Hey, Im awfully sorry if I have posted this in the wrong place, if moderators want to move it , feel free but could i be informed of where it is moved to... thanks in advance...

anyway, quite recently my stupid windows crashed and wont boot when i turn on my computer... So my friend insisted i tried ubuntu, i gave it a shot and it seems to be a good substitute for the windows operating system... Although i do not want to delete my hard drive so I am running this off a disk and have not yet installed it... There are some very important files i need to retreive first before I can wipe the hard drive clear... I only have one hard drive which I cannot seem to access...
When i go to , Places > Computer , it shows the 111 GB volume hard drive, but when i try to access it, it says "The folder contents cannot be displayed, you do not have the persmission necessary to view the contents of "disks-conf-sda1". 
I don't know what to do and half my business is on that hard drive.... :( i would apreciate it if i could have some assistance in retreiving the files and then hopefully ill be able to install ubuntu.. thanks in advance...

---

### Post by scxtt on 2007-03-14
open up a terminal window, then type the following:

sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1

then navigate to /media/sda1 and you should see your files (barring a physical problem w/ the disk) ... let me know if the "mount" command doesn't work, and if your disk is "NTFS" or "FAT32" ...

---

### Post by morbidAUS on 2007-03-14
thank you for your speedy reply, i shall try that now... i pray everything is ok..

---

### Post by morbidAUS on 2007-03-14
ummm ok i then went to computer and opened up the hard drive.. its empty but says it only has 200 MB free which is how much i did have... so where are all the files :| are they retreivable... :(

---

### Post by scxtt on 2007-03-14
what is the output of:

[indent]df -h[/indent]

and

[indent]sudo fdisk -l /dev/sda[/indent]

---

### Post by morbidAUS on 2007-03-14
```
ubuntu@ubuntu:~$ sudo mkdir/media/sda1
sudo: mkdir/media/sda1: command not found
ubuntu@ubuntu:~$ sudo mkdir /media/sda1
ubuntu@ubuntu:~$ sudo mount/dev/sda1 media/sda1
sudo: mount/dev/sda1: command not found
ubuntu@ubuntu:~$ sudo mount /dev/sda1 media/sda1
mount: mount point media/sda1 does not exist
ubuntu@ubuntu:~$ sudo mkdir /media/sda1
mkdir: cannot create directory `/media/sda1': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/sda1
mount: /dev/sda1 already mounted or /media/sda1 busy
mount: according to mtab, /dev/sda1 is mounted on /tmp/disks-conf-sda1
ubuntu@ubuntu:~$

```

thats exactly what i did from start haha i stuff up two times :(

it also when i tried again came up with the i dont have persmission stuff

---

### Post by morbidAUS on 2007-03-14
oh ... i am so sorry.. i feel so stupid.. hahah you here we go... what you actually asked for... 
```
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
unionfs               874M  677M  198M  78% /
varrun                252M   80K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  120K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M  8.8M  244M   4% /lib/modules/2.6.15-23-386/volatile
tmpfs                 252M   20K  252M   1% /tmp
/dev/sda1             112G  112G  195M 100% /tmp/disks-conf-sda1
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14592   117210208+   7  HPFS/NTFS
ubuntu@ubuntu:~$

```

---

### Post by scxtt on 2007-03-15
ok, more commands for output (if your issue is still unresolved): what's the output of **mount**?  i'm wondering if it's mounted correctly for NTFS ...

what do you get if you type **cd /tmp/disks-conf-sda1** in a terminal window?

---

