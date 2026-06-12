---
title: "Harddrive from CD"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-03-19
Is there anyway I can see my windows files from the live CD in Ubuntu.

---

### Post by o_fortuna on 2007-03-19
> **ProjectWhat said:**
> Is there anyway I can see my windows files from the live CD in Ubuntu.
The easiest way I can think of is to open a terminal (Applications--Accessories--Terminal) and do the following:
```
sudo fdisk -l
```
This will list your partitions. You should see something sort of like this:
```
/dev/sda1   *           1        3917    31461376    7  HPFS/NTFS
```
You are looking for the line with NTFS at the end. Note the beginning of the line. In my case it's /dev/sda1, but for you it might be /dev/hda1 or something else. Once you have that, paste this into the terminal:
```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```
Now just open the Places menu. If windows isn't listed, select computer and browse from Filesystem, to media, to windows.

---

### Post by ProjectWhat on 2007-03-19
Thanks So Much.

<edit>
But it only read only. How do I fix that?

---

### Post by zvacet on 2007-03-19
Naturaly,bacause it is not safe to write,but if you want give i try change umask=0222 to umask-a u 0000

---

### Post by o_fortuna on 2007-03-19
> **ProjectWhat said:**
> Thanks So Much.

<edit>
But it only read only. How do I fix that?
Hi -- enabling read-write support by the way posted above can damage your ntfs data. HOWEVER -- there is a safe and stable way to do it (which I use every day) which involves installing some extra stuff. First, restart the live CD to clean up the old stuff

In a terminal again:
```
sudo apt-get install ntfs-3g
sudo mkdir /media/windows
gksu gedit /etc/fstab
```
Now you have an edit window. Add a line to the bottom of that file like this:
```
/dev/<your partition>     /media/<mount point>     ntfs-3g     defaults,locale=en_US.utf8   0    0
```
/dev/<your partition> is gained from the method I posted above.
Finally, do this in the terminal:
```
sudo mount -a
```
That should do the job

---

