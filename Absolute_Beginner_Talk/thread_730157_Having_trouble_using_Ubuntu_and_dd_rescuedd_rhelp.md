---
title: "Having trouble using Ubuntu and dd_rescue/dd_rhelp"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by shammihundal on 2008-03-20
Hey everybody, this is my first post here so please go easy and I have done extensive research on this matter and can not find anything to help my problem. :)

For the short version my drive that is broken needs to be saved. I tried so many things with no luck. Installed Ubuntu and dd_rescue/dd_rhelp and cant figure out how to run it. I plug in my external drive with broken drive in it to laptop and put in

sudo dd_rhelp /dev/sda1 /dev/sda2/backup.img

I know this is wrong but how do I make it tell to read from external and write to laptop partion? Also how do I create a clean partition inside of the Ububtu partition?

Ok now the long version for the more patient ones.

The problem that I have is that I have been trying to recover pictures from a broken hard drive. When I say broken I mean that the head is clinking and rattling a bit. So of course the hard drive can not mount. I’ve tried multiple things in Windows with no luck. So I researched online and found out about dd_rescue and dd_rhelp. So I downloaded Ubuntu without knowing anything about linux and gave it a shot. I consider myself pretty knowledgeable about computer but have little skills in DOS related thins like the terminal. Using the program has proved to be a challenge. Ive been to many sites like 

[http://www.debianadmin.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html](http://www.debianadmin.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html)

and they are very helpful, however I just cant seem to get started.

I have installed dd_rescue and have the dd_rhelp that does not need to be installed. I put my broken 40GB hard drive into the USB 2.0 generic external case that I have and hooked it up to my laptop that has an 80GB Ubuntu partition. 

The next step would be go to the dd_rhelp folder in the terminal and type

sudo dd_rhelp /dev/sda1 /dev/sda2/backup.img

Here is where I have my problem. I understand that sda1 is the broken drive and sda2 is the good drive. How do you set this to be though? Is it right when you plug in the drive that it sets it to that? Also what is the “/dev” stand for? How do I make it tell to read from external drive that does not mount (but I guess Im not supposed to do that) and write to laptop Ubuntu partion? Do I need to create another partition on the Ubuntu partition so that it is clear of files and folders? How do I do that if I need to?

I know Ive been knocking myself on my head as well. It seems so easy but I just cant do it and I am submitting to the higher power to be. Please help this problem out and give any other advice or suggestions that might help in my journey. Those picture are my girlfriends whole history and she would be devastated if she lost them as would I.

---

### Post by aysiu on 2008-03-20
First of all, you have to see what your partition table looks like. Can you post the output of these commands (just copy and paste the output back here)? ```
df -h
sudo fdisk -l
``` Also, I don't know what *dd_rhelp* is, but if you have the *ddrescue* package installed, the command is ```
dd_rescue /dev/*brokendevicelocation* /dev/*workingdevicelocation*/backup.img
``` The two commands I gave you before will help us determine what *brokendevicelocation* and *workingdevicelocation* are.

---

### Post by shammihundal on 2008-03-26
Sorry for the long wait. I have been very busy with a cousins wedding.

This is what I get with a healthy drive in the external case

```
shammihundal@shammihundal-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             120G  8.8G  105G   8% /
varrun                506M   96K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   88K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             299G  113G  186G  38% /media/Backup
shammihundal@shammihundal-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce1ee1d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3259    26177886    7  HPFS/NTFS
/dev/sda2            3260       19080   127082182+  83  Linux
/dev/sda3           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2263960f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    6  FAT16

```

and I get this with the broken drive in there

```
shammihundal@shammihundal-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             120G  8.8G  105G   8% /
varrun                506M  100K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   96K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
shammihundal@shammihundal-laptop:~$ sudo fdisk -l
[sudo] password for shammihundal:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce1ee1d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3259    26177886    7  HPFS/NTFS
/dev/sda2            3260       19080   127082182+  83  Linux
/dev/sda3           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
240 heads, 63 sectors/track, 5170 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x0000675f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4790    36212368+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2            4791        5169     2865240    f  W95 Ext'd (LBA)
/dev/sdb5            4791        5169     2865208+   7  HPFS/NTFS
shammihundal@shammihundal-laptop:~$ 

```

Should I just use two external hard drive or can i just put the image on the linux partition?

---

### Post by aysiu on 2008-03-26
So it'd be ```
dd_rescue /dev/sdb1 ~/Desktop/backup1.img
``` and ```
dd_rescue /dev/sdb5 ~/Desktop/backup2.img
```

---

