---
title: "[SOLVED] Mounting a USB to IDEhard drive on ubuntu"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by ~L~ on 2008-04-16
Can you please help me mount it
[http://i42.photobucket.com/albums/e310/Morgoth_Bauglir/Screenshot-1.png](http://i42.photobucket.com/albums/e310/Morgoth_Bauglir/Screenshot-1.png)

---

### Post by joshrobinson on 2008-04-16
looks like you unplugged it without ejecting it in windows, can you boot into windows or have a windows machine?

it says you can force it, if you want to try that

---

### Post by ~L~ on 2008-04-16
i want to force it yes andi  am using ubuntu ONLY ..

---

### Post by joshrobinson on 2008-04-16
> **~L~ said:**
> i want to force it yes andi  am using ubuntu ONLY ..

since your forcing it, i cant be held responsible for data loss or anything

```
sudo mkdir /media/disk
```
```
sudo mount -t ntfs-3g /dev/sdg1 /media/disk -o force
```
if the code above works, you can add a line to your fstab to mount the drive at boot

```
sudo cp /etc/fstab /etc/fstab.backup
```
this will backup your fstab file

```
sudo gedit /etc/fstab
```
add this line to the bottom

```
/dev/sdg1 /media/disk ntfs-3g defaults,force 0 0
```

---

### Post by MrFSL on 2008-04-16
It's an NTFS drive you need to run ntfsfix...
```
sudo apt-get install ntfsprogs
sudo ntfsfix <device name>
```

Obviously replace device name above with your actual device name.
See: man ntfsfix for more details.

(From the man page)
> NTFSFIX(8)                                                          NTFSFIX(8)

NAME
       ntfsfix - fix common errors and force Windows to check NTFS

SYNOPSIS
       ntfsfix [options] device

DESCRIPTION
       ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk. It only repairs  some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.

       You may run ntfsfix on an NTFS volume if you think it  was  damaged  by
       Windows or some other way and it can’t be mounted.


---

### Post by ~L~ on 2008-04-16
> **joshrobinson said:**
> since your forcing it, i cant be held responsible for data loss or anything

```
sudo mkdir /media/disk
```
```
sudo mount -t ntfs-3g /dev/sdg1 /media/disk -o force
```
if the code above works, you can add a line to your fstab to mount the drive at boot

```
sudo cp /etc/fstab /etc/fstab.backup
```
this will backup your fstab file

```
sudo gedit /etc/fstab
```
add this line to the bottom

```
/dev/sdg1 /media/disk ntfs-3g defaults,force 0 0
```

Thanks a lot , everything worked fine.
If you could also tell me what these commands did, I'd me most grateful.:KS

---

