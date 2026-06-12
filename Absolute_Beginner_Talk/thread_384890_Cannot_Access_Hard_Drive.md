---
title: "Cannot Access Hard Drive"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by morbidAUS on 2007-03-15
Hello all, thanks in advance for taking the time to read this thread and possibly help out...

Problem: The Problem I am having is that I have a hard drive with windows on it, It is the only hard drive on my computer.. Windows wont boot and just keeps restarting... I am sick of windows and my friend insisted I tried Ubuntu. But before I can install Ubuntu I have to retreive some very important files off my hard drive...

The hard drive is running windows XP.. I have a burner and will be able to burn the data off once I have accessed the hard drive... I have an AMD Athlon 3500+...

This may help you

I tried this but when I went into the drive it had no files and said it only had 200 MB free, when I attempted it again it said I have no permission..
```

sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1

```

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

any assitance would be appreciated... thanks

---

### Post by irwa82 on 2007-03-15
Hi,

I believe you will find your data at /tmp/disks-conf-sda1 not /media/sda1

Try looking at /tmp/disks-conf-sda1 and see if you have your data there.

---

### Post by morbidAUS on 2007-03-15
Thanks for the reply... but when i click on it i get this

```
You do not have the permissions necessary to view the contents of "sda1".
```

---

### Post by taurus on 2007-03-15
Edit /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda1   /media/sda1   ntfs   nls=utf8,umask=0222   0  0
```
Save it.  Then, reboot.  Now, what happens when you browse /media/sda1?  Do you see your Windows files in there?

---

### Post by morbidAUS on 2007-03-15
this will work even though i am booting off a cd?

edit: sorry to seem noobish but how exactly would i type that in?

---

### Post by taurus on 2007-03-15
> **morbidAUS said:**
> this will work even though i am booting off a cd?

Nope.  It only works if you boot Ubuntu from your harddrive.  If you want to boot from the LiveCD, then you need to run

Applications -> Accessories -> Terminal
```
sudo mkdir /media/sda1
sudo mount -t ntfs /dev/sda1 /media/sda1 -o nls=utf8,umask=0222
```

---

### Post by morbidAUS on 2007-03-15
thank you for the info i will get back to you

---

### Post by morbidAUS on 2007-03-15
OMG...!!!! Thank you so soo soooo muchh.... It worked... I am ever so greatful... :) thankyou !!! :)

---

