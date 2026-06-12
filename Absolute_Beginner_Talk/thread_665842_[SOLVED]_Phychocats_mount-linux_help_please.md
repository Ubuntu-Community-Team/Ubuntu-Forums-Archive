---
title: "[SOLVED] Phychocats mount-linux help please"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2008-01-12
I have an extra HD in my box which I have managed, thanks to the psychocats site, to get formated to Ext3 and so now I have 160 GB to use for storage. I followed the [instructions here ]("http://www.psychocats.net/ubuntu/mountlinux")to mount the HD
and the folder /system has turned up but the only thing in it is 'LOST & found'
I cannot figure where I have gone wrong.

---

### Post by The Tronyx on 2008-01-12
> **kindafunnylookin said:**
> I have an extra HD in my box which I have managed, thanks to the psychocats site, to get formated to Ext3 and so now I have 160 GB to use for storage. I followed the [instructions here ]("http://www.psychocats.net/ubuntu/mountlinux")to mount the HD
and the folder /system has turned up but the only thing in it is 'LOST & found'
I cannot figure where I have gone wrong.

Is it a usb hard drive? 

In a terminal, please enter the following commands and post their output:
> 
sudo fdisk -l

> 
sudo lsusb


---

### Post by kindafunnylookin on 2008-01-12
```
peter@Gutsy7_10:~$ sudo fdisk -l
[sudo] password for peter:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006f4f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29644   238115398+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe47c63f

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       19457   156288321   83  Linux
p
```eter@Gutsy7_10:~$

---

### Post by The Tronyx on 2008-01-12
I'm going to guess that /dev/hdc1 is your external hard drive since you said it was 160 gigs.

If you open nautilus or any file manager, are you able to view the contents of hdc1?

---

### Post by taurus on 2008-01-12
If you just formatted your /dev/hdc1, then it's a clean drive so there shouldn't be anything in /system except the Lost & Found directory.

Now, if you want to write to it, you need to change the ownership of that mount point, system, from root to your login name, _assuming_ your login name is **peter**.

```
sudo chown -R **peter**:**peter** /system
```

---

### Post by kindafunnylookin on 2008-01-12
Yes, both dev/hdc and dev/hdc1 show up using nautilus, they will not open however.
My Ubuntu 7.10 runs on a SATA drive and hdc runs on an IDE drive, could that be it?

---

### Post by The Tronyx on 2008-01-12
> **kindafunnylookin said:**
> Yes, both dev/hdc and dev/hdc1 show up using nautilus, they will not open however.
My Ubuntu 7.10 runs on a SATA drive and hdc runs on an IDE drive, could that be it?

What happens when you try to open the drives?  Any error messages or anything?

---

### Post by kindafunnylookin on 2008-01-12
> **taurus said:**
> If you just formatted your /dev/hdc1, then it's a clean drive so there shouldn't be anything in /system except the Lost & Found directory.

Now, if you want to write to it, you need to change the ownership of that mount point, system, from root to your login name, _assuming_ your login name is **peter**.

```
sudo chown -R **peter**:**peter** /system
```

Did that and got:
```
peter@Gutsy7_10:~$ sudo chown -R peter:peter /system
[sudo] password for peter:
chown: cannot access `/system': No such file or directory
peter@Gutsy7_10:~$ 

```

---

### Post by taurus on 2008-01-12
Where did you mount /dev/hdc1 to?  Can you post

```
cat /etc/fstab
df -h
```

---

### Post by kindafunnylookin on 2008-01-12
peter@Gutsy7_10:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0d2d5770-f738-4b63-a90d-2479ba0c1239 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc1 /storage ext3 defaults 0 0
peter@Gutsy7_10:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             224G  204G  9.0G  96% /
varrun               1014M   96K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M  100K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   24M  990M   3% /lib/modules/2.6.22-14-generic/volatile
/dev/hdc1             147G  188M  140G   1% /storage
peter@Gutsy7_10:~$

---

### Post by The Tronyx on 2008-01-12
> 
mkdir ~/mount
sudo mount /dev/hdc1 ~/mount

Can you access the drive after doing that?

Not that you may need to navigate to /home/peter/mount to access the drive.

---

### Post by taurus on 2008-01-12
You mount it to /storage, not /system as you have said in your original post.

```
sudo chown -R peter:peter /storage
ls -la /storage
```

---

### Post by kindafunnylookin on 2008-01-12
Ok. It's solved. It was a permissions problem. Thanks for helping and thanks to psychocats for beiing there.

---

### Post by kindafunnylookin on 2008-01-12
Thank you both. I got it with permissions.

---

### Post by kindafunnylookin on 2008-01-12
As it is now, I use the hdc1 drive for storage only and can access it through /storage in the file system.

---

### Post by kindafunnylookin on 2008-01-12
> **2point0 said:**
> Can you access the drive after doing that?

Not that you may need to navigate to /home/peter/mount to access the drive.

Yes. I have a mount point in my home directory and can access hdc1 there. That is just what I wanted, Thank you.

---

