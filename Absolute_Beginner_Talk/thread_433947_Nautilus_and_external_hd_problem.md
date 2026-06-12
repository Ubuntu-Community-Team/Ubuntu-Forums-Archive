---
title: "Nautilus and external h/d problem"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by davesmith on 2007-05-05
Hi
Can anyone help with an external drive issue?

Nautilus does´nt start up when i plug in my external h/d. The terminal can see the drive, but neither nautilus or konqueror do.

Here is the output of Sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 4688 37656328+ 83 Linux
/dev/hda2 4689 4864 1413720 5 Extended
/dev/hda5 4689 4864 1413688+ 82 Linux swap / Solaris

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 9964 80035798+ 7 HPFS/NTFS

So, the system can see the external drive, but why cant Nautilus?
Please help!

I´m running 6.10 Edgy

Dave Smith

---

### Post by taurus on 2007-05-05
Does it automount?  What happens if you run this command from a terminal?

```
df -h
```

---

### Post by davesmith on 2007-05-05
Taurus, thanks

here is the output of the command df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G   23G   11G  69% /
varrun                998M   68K  998M   1% /var/run
varlock               998M     0  998M   0% /var/lock
procbususb             10M  144K  9.9M   2% /proc/bus/usb
udev                   10M  144K  9.9M   2% /dev
devshm                998M     0  998M   0% /dev/shm
lrm                   998M   18M  981M   2% /lib/modules/2.6.17-10-generic/volatile

what does that tell you?

---

### Post by taurus on 2007-05-05
Well, it means that you need to mount /dev/sda1 before you can access it.

```
sudo mkdir /media/sda1
sudo mount -t ntfs /dev/sda1 /media/sda1 -o nls=utf8,umask=0222
df -h
```

---

### Post by davesmith on 2007-05-05
Ah, that did the trick!

laptop:~$ sudo mkdir /media/sda1
mkdir: cannot create directory `/media/sda1': File exists
laptop:~$ sudo mount -t ntfs /dev/sda1 /media/sda1 -o nls=utf8,umask=0222
mount: /dev/sda1 already mounted or /media/sda1 busy
mount: according to mtab, /dev/sda1 is already mounted on /media/sda1

and an icon called ¨backup¨ has appeared on my desktop:) 

now i thank you most kindly, it just needed mounting

Dave Smith

---

### Post by sparks40 on 2007-05-05
Nice going Taurus. Are you up for another try?
I am having a similar problem but can't quite figure out how to translate Dave's solution with my problem.
I just installed a new Maxtor 100gig HD in an external USB enclosure. However, I can't get my system to recognize the drive or contents. My terminal shows the following to the command:

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              14G  5.0G  8.2G  38% /
varrun                443M  108K  443M   1% /var/run
varlock               443M     0  443M   0% /var/lock
procbususb            443M   96K  443M   1% /proc/bus/usb
udev                  443M   96K  443M   1% /dev
devshm                443M     0  443M   0% /dev/shm
lrm                   443M   33M  410M   8% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1             9.8G  8.7G  1.1G  90% /media/sda1
frank@frank-desktop:~$ 

sda1 and sda2 are both located on a single internal sata HD which is working properly dualbooting XP and Ubuntu.

Could you please give me a hand in getting this going? 
TNX

---

### Post by taurus on 2007-05-05
Can you also include the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by sparks40 on 2007-05-05
this is it.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    c  W95 FAT32 (LBA)
/dev/sda2            1276        3099    14651280   83  Linux
/dev/sda3            3100        3342     1951897+  82  Linux swap / Solaris
/dev/sda4            3343       19457   129443737+   5  Extended
/dev/sda5            3343        4617    10241406   83  Linux
frank@frank-desktop:~$

---

### Post by taurus on 2007-05-05
Well, I see that you are not using /dev/sda5 at all.  

On the other hand, does the BIOS even detect your 100GB Maxtor harddrive at all?  Also, see if XP sees that harddrive.

---

### Post by sparks40 on 2007-05-05
Sorry I didn't mention it earlier but sda5 is a partition on the internal sata drive holding a test version of Fedora. sda1 is an XP partition, sda2 is my ubuntu partition and sda3 is my swap partition. sda4 is an extended partition.

I have not gone into the bios because I was of the opinion that it is only necessary if adding a new drive to the sata disk controller. 

lsusb produces the following:

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 152d:2338  
Bus 001 Device 001: ID 0000:0000  

df -h indicates the following:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              14G  5.0G  8.2G  38% /
varrun                443M  112K  443M   1% /var/run
varlock               443M     0  443M   0% /var/lock
procbususb            443M   96K  443M   1% /proc/bus/usb
udev                  443M   96K  443M   1% /dev
devshm                443M     0  443M   0% /dev/shm
lrm                   443M   33M  410M   8% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1             9.8G  8.7G  1.1G  90% /media/sda1

This seems to indicate to me that the usb drive is /proc/bus/usb and is recognized????

Xp recognizes the drive but I cannot list the directory or access any of the data on it.

---

### Post by taurus on 2007-05-05
So, XP can't access that 100GB Maxtor harddrive then!  Have you created a filesystem on that harddrive at all?

---

### Post by sparks40 on 2007-05-05
Yes, there is a fat32 with data on it.

---

### Post by sparks40 on 2007-05-05
Actually I have tried  four seperate drives with fat32 and ext3 filesystems on them... none of them seem to show up. doesn't the df -h indicate that the drive is in fact being seen by the system???

---

### Post by taurus on 2007-05-09
Actually, df -h only shows you the mounted partitions so if you want to have a look at your harddrives, you need to run

```
sudo fdisk -l
```
Again, should boot into Windows and defrag that fat32 harddrive first to make sure everything is alright on that harddrive.

---

### Post by sparks40 on 2007-05-09
I have already defraged one of the drives. Moreover, the original drive I tried it on was a brand new, out of the box, Maxtor. 

I initialized and formatted the Maxtor with the installation CD provided in the box without a problem. Under XP the drive is seen in "manange drives" but not in "My Computer." The drive is not seen at all under Ubuntu. Needless to say neither of the two drives previously mentioned worked. 

I borrowed a new "My Book - USB external hard drive"  and it works in both Windows and Ubuntu perfectly. So I can rule out a bug in the USB system on my box. 

It was my understanding that the drivers for external USB drives are part of the OS and not imbeded in the external case/drive box.

I have tried strapping the drive as a master, slave and cable select. NG.

I am not ready to give up, but I do need some direction. Please help.

TNX

---

