---
title: "Sorry if this is the wrong place for this but..."
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by ~Beck~ on 2007-02-08
I am logged into root, I try to open up my other partition and this error message comes up:
*You do not have the permissions necessary to view the contents of "windows".*

How can I fix this? :/

---

### Post by jd65pl on 2007-02-08
First of all is there a particular reason why you logged in as root? I would read [this]("https://help.ubuntu.com/community/RootSudo") about using root/sudo before continuing.

Second is your drive ntfs? If it is then you will if so you should find [this]("https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite") useful.

---

### Post by ~Beck~ on 2007-02-09
This would be because I was getting errors about needing to be logged in as root before.

I changed the permissions on my HD in Windows and now I can't see the drive at all. :/

---

### Post by taurus on 2007-02-09
Exit root account and from your regular account, past the output of this command here.

```
sudo fdisk -l
```

---

### Post by ~Beck~ on 2007-02-09
> Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2431    19526976    7  HPFS/NTFS
/dev/hda2            2432        4761    18715725   83  Linux
/dev/hda3            4762        4864      827347+   5  Extended
/dev/hda5            4762        4864      827316   82  Linux swap / Solaris


hda1 is the one I need to mount is what I know.

---

### Post by taurus on 2007-02-09
```
sudo mkdir /media/hda1
sudo mount -t ntfs /dev/hda1 /media/hda1 -o nls=utf8,umask=0222
df -h
```

---

### Post by ~Beck~ on 2007-02-09
> beck@Beck:~$ sudo mkdir /media/hda1
mkdir: cannot create directory `/media/hda1': File exists
beck@Beck:~$ sudo mount -t ntfs /dev/hda1 /media/hda1 -o nls=utf8,umask=0222
beck@Beck:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              18G  2.2G   15G  13% /
varrun                221M   80K  221M   1% /var/run
varlock               221M  4.0K  221M   1% /var/lock
udev                  221M  128K  220M   1% /dev
devshm                221M     0  221M   0% /dev/shm
lrm                   221M   19M  202M   9% /lib/modules/2.6.15-26-386/volatile
/dev/hda1              19G  6.7G   12G  36% /media/hda1

...

---

### Post by taurus on 2007-02-09
Well, there you go.  Your Windows partition is on /media/hda1 now.

```
**/dev/hda1 19G 6.7G 12G 36% /media/hda1**
```

---

### Post by ~Beck~ on 2007-02-09
> **taurus said:**
> Well, there you go.  Your Windows partition is on /media/hda1 now.

```
**/dev/hda1 19G 6.7G 12G 36% /media/hda1**
```

beck@Beck:~$ /dev/hda1 19G 6.7G 12G 36% /media/hda1
bash: /dev/hda1: Permission denied

:/ I keep getting this error.

---

### Post by taurus on 2007-02-09
```
ls -la /media/hda1
```
or
```
cd /media/hda1
ls -la
```
or use nautilus to browse it.

---

### Post by ~Beck~ on 2007-02-09
Tells me all my files and folders in Terminal. But still can't access the partition.

EDIT: Just tried again... I can see all my files and folders now. Thanks.

One more question, is there any way I can make my Windows programs run in Ubuntu?

---

### Post by taurus on 2007-02-09
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by ~Beck~ on 2007-02-09
Thanks for all the help. If I have any problems with Wine, I'll let you know.

---

