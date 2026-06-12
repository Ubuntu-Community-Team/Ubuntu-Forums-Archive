---
title: "Mounting an Internal HD"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by nuclearj on 2006-11-15
```
nuclearj@Venice-610:~$ sudo mount -t nfs /dev/hda5 /media/15GB_HD
mount: directory to mount not in host:dir format

```

I am trying to mount a backup drive I had from my old computer (has all the pictures and files from it that I wanted to keep)

Could someone tell me if 1) the syntax is correct and 2) what does that error msg mean?

---

### Post by aidanr on 2006-11-15
nfs is network file system, maybe you want n**t**fs

---

### Post by nuclearj on 2006-11-15
```
nuclearj@Venice-610:~$ sudo mount -t ntfs /dev/hda5 /media/test
mount: /dev/hda5 already mounted or /media/test busy
nuclearj@Venice-610:~$

```

I changed it and now i have this ^

---

### Post by taurus on 2006-11-15
What is the output of this command?

```
df -h
```

---

### Post by nuclearj on 2006-11-15
Hmmm dev/hda5 is not on there.  I got that from the fstab file.


```
nuclearj@Venice-610:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              73G   14G   56G  20% /
varrun                506M   80K  505M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  136K  505M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  487M   4% /lib/modules/2.6.15-27-386/volatile
nuclearj@Venice-610:~$

```

---

### Post by taurus on 2006-11-16
What about this command?

```
sudo fdisk -l
```
I am going to guess that your /dev/hda5 is your swap so your NTFS is probably somewhere else.  Of course, the above commend will tell us more about /dev/hda5...

---

### Post by nuclearj on 2006-11-16
You're correct the hda5 is my swap and here is the output

```
sudo fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9588    77015578+  83  Linux
/dev/hda2            9589        9964     3020220    5  Extended
/dev/hda5            9589        9964     3020188+  82  Linux swap / Solaris

Disk /dev/hdb: 15.0 GB, 15000330240 bytes
255 heads, 63 sectors/track, 1823 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1822    14635183+   7  HPFS/NTFS
nuclearj@Venice-610:~$

```

So shoud i try mounting it with:
```
$ sudo mount -t ntfs /dev/hdb1 /media/15GB_HD
```

---

### Post by taurus on 2006-11-16
> **nuclearj said:**
> You're correct the hda5 is my swap and here is the output

```
sudo fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9588    77015578+  83  Linux
/dev/hda2            9589        9964     3020220    5  Extended
/dev/hda5            9589        9964     3020188+  82  Linux swap / Solaris

Disk /dev/hdb: 15.0 GB, 15000330240 bytes
255 heads, 63 sectors/track, 1823 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1822    14635183+   7  HPFS/NTFS
nuclearj@Venice-610:~$

```

So shoud i try mounting it with:
```
$ sudo mount -t ntfs /dev/hdb1 /media/15GB_HD
```
See, I knew it!!!  Why don't you modify your /etc/fstab so your NTFS would be mounted automatically each time you boot Ubuntu?  Open a terminal and do

```
sudo cp /etc/fstab /etc/fstab  <-- make a back up copy just in case...
gksudo gedit /etc/fstab
```
Now, add this line to the end of it.

```

/dev/hdb1   /media/15GB_HD   nls=utf8,umask=0222   0   0

```
Save it and run these two commands.

```
sudo mount -a
df -h
```

---

### Post by nuclearj on 2006-11-16
After some trial and error I got it to work.  I had to add the filesystem type:
```
/dev/hdb1   /media/15GB_HD   nls=utf8,**ntfs** umask=0222   0   0
```

> nuclearj@Venice-610:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              73G   14G   56G  20% /
varrun                506M   80K  505M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  136K  505M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  487M   4% /lib/modules/2.6.15-27-386/volatile
/dev/hdb1              14G   14G  430M  97% /media/15GB_HD



Thanks for all your help Taurus.  Also a shout to Aidnar for getting me started.  My next lesson is learning about about permissions.  :D

---

