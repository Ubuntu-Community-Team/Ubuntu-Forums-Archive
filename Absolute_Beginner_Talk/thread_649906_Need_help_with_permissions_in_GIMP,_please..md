---
title: "Need help with permissions in GIMP, please."
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-12-25
I began having trouble today, trying to save a .jpg that I had altered with Gimp.

The error message was; " .JPEG image plug-in could not save image "

Under 'Properties -Permissions' it says the Flash card is owned by Root, so I tried to change it with 'CHOWN' to being owned by me but couldn't get the code correct.


qwer@qwer-desktop:~$ chown qwer PC251500.JPG
chown: cannot access `PC251500.JPG': No such file or directory
qwer@qwer-desktop:~$ chown disk/DCIM/100OLYMP PC250500.JPEG image
chown: `disk/DCIM/100OLYMP': invalid user
qwer@qwer-desktop:~$ sduo chown disk/DCIM/100OLYMP PC250500.JPEG image
bash: sduo: command not found
qwer@qwer-desktop:~$ chown qwer PC251500.JPEG disk/DCIM/100OLYMP
chown: cannot access `PC251500.JPEG': No such file or directory
chown: cannot access `disk/DCIM/100OLYMP': No such file or directory
qwer@qwer-desktop:~$

I would appreciate any help or suggestions here. 

TIA

---

### Post by LinuxIsInnovation on 2007-12-25
Try: 
chmod +w PC251500.JPG

---

### Post by fatality_uk on 2007-12-25
> **sayakb said:**
> Try: 
chmod +r PC251500.JPG

What he said :lolflag:

---

### Post by taurus on 2007-12-25
Is that flash card vfat32/vfat?  And how do you mount it?

```
sudo fdisk -l
df -h
```

---

### Post by LinuxIsInnovation on 2007-12-25
> **fatality_uk said:**
> What he said :lolflag:

:-({|=

---

### Post by L Campbell on 2007-12-25
> **taurus said:**
> Is that flash card vfat32/vfat?  And how do you mount it?

```
sudo fdisk -l
df -h
```

The card is a 512MB and I plug it into a  USB card reader.  I'm not sure about the file system on it and won't be able to check that till I get back to my house.

Thanks,

---

### Post by zgornel on 2007-12-25
Try running Gimp as root if you want to leave the permissions alone.

---

### Post by taurus on 2007-12-25
> **zgornel said:**
> Try running Gimp as root if you want to leave the permissions alone.

He can remount that drive with umask=000 option and he can write to it without using sudo if it's a vfat filesystem.

---

### Post by L Campbell on 2007-12-26
> **sayakb said:**
> Try: 
chmod +w PC251500.JPG

Thanks, I tried this but it didn't work.

qwer@qwer-desktop:~$ chmod +w PC251500.JPG
chmod: cannot access `PC251500.JPG': No such file or directory
qwer@qwer-desktop:~$ 


Kind regards.

---

### Post by L Campbell on 2007-12-26
> **taurus said:**
> Is that flash card vfat32/vfat?  And how do you mount it?

```
sudo fdisk -l
df -h
```

Thank you.

Here is what I got:-

qwer@qwer-desktop:~$ sudo fdisk -l
[sudo] password for qwer:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b5496

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 523 MB, 523321344 bytes
16 heads, 63 sectors/track, 1014 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1014      511024+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(1012, 15, 63) logical=(1013, 15, 63)
qwer@qwer-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  4.0G   63G   6% /
varrun                506M   84K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   80K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             499M   38M  462M   8% /media/disk
qwer@qwer-desktop:~$ 

Kind regards.

---

### Post by taurus on 2007-12-26
Try

```
sudo umount /media/disk
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
ls -la /media/sdb1
```
You now should be able to write to /media/sdb1.

---

### Post by L Campbell on 2007-12-26
> **taurus said:**
> Try

```
sudo umount /media/disk
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
ls -la /media/sdb1
```
You now should be able to write to /media/sdb1.

Thanks again.  Here is what I got:-

qwer@qwer-desktop:~$ sudo umount /media/disk
[sudo] password for qwer:
qwer@qwer-desktop:~$ sudo mkdir /media/sdb1
qwer@qwer-desktop:~$ sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
qwer@qwer-desktop:~$ ls -la /media/sdb1
total 36
drwxrwxrwx 4 root root 16384 1969-12-31 18:00 .
drwxr-xr-x 6 root root  4096 2007-12-26 14:39 ..
drwxrwxrwx 3 root root  8192 2004-03-04 20:01 dcim
drwxrwxrwx 2 root root  8192 2004-04-23 08:07 misc
qwer@qwer-desktop:~$ 

I have tried checking the permissions on the disk and on individual photos and they are still all ROOT.

Would re-booting the 'puter be what I need to do now?

Kind Regards.

---

### Post by L Campbell on 2007-12-26
> **L Campbell said:**
> Thanks again.  Here is what I got:-

qwer@qwer-desktop:~$ sudo umount /media/disk
[sudo] password for qwer:
qwer@qwer-desktop:~$ sudo mkdir /media/sdb1
qwer@qwer-desktop:~$ sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
qwer@qwer-desktop:~$ ls -la /media/sdb1
total 36
drwxrwxrwx 4 root root 16384 1969-12-31 18:00 .
drwxr-xr-x 6 root root  4096 2007-12-26 14:39 ..
drwxrwxrwx 3 root root  8192 2004-03-04 20:01 dcim
drwxrwxrwx 2 root root  8192 2004-04-23 08:07 misc
qwer@qwer-desktop:~$ 

I have tried checking the permissions on the disk and on individual photos and they are still all ROOT.

Would re-booting the 'puter be what I need to do now?

Kind Regards.

OK, I re-booted again but nothing seems to have changed.

Just to reiterate, it is a 512MD Compact Flash Card, in a USB mount card reader.

Under 'Permissions' I have:-

Owner - qwer

Group - root

When I try to 'Save as', a photo that I have altered with GIMP, I get the error:-

".JPEG image plug - in could not save image."

---

### Post by taurus on 2007-12-26
If you reboot, you have to repeat the steps that I showed you over again.  Even though root is the owner, you should be able to write to it and by the way, fat32/vfat won't let you change ownership so it's up to you if you keep trying to change from root to your username with chown.

---

### Post by L Campbell on 2007-12-26
> **taurus said:**
> If you reboot, you have to repeat the steps that I showed you over again.  Even though root is the owner, you should be able to write to it and by the way, fat32/vfat won't let you change ownership so it's up to you if you keep trying to change from root to your username with chown.

Oops!  I'm confused here.

Let me try to explain where my confusion is coming from.  Up until 2 days ago, I could take a photo, put the flash card in the reader and, when I opened the disk, I could digitally manipulate the photo with GIMP and ' Save As '.

I could drag a photo from the disk onto my Desktop, digitally manipulate it and ' Save As '.

Now when I try to ' SAVE AS ' a photo I get the error, ".JPEG image plug-in could not save image.

I made the assumption that, if the file said 'root' in the 'Permissions', that 'could' be where my problem was coming from.

As you see from the 'screenshots', the photo that I dragged from the disk, to Desktop, has got different 'Permissions'.  If you could suggest to me what I might be able to do to fix this, I would really appreciate it.

---

