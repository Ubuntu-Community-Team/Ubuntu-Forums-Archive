---
title: "Dual boot: XP and Ubuntu. NTFS Mount problem"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by kebabdylan on 2007-06-06
I have read a bunch of tutorials but can't find this addressed.

i have windows xp installed then installed Ubuntu as a dual boot system. I had ubuntu installation split the partition in half (it was just the c drive) and installed fine.

but the ntfs partition shows up not in the dev/ but as a media/disk and is not writeable. I installed the automatix ntfs mounter with read/write but that does not fix it.

it seems like its not seeing it as a hard drive but as something else.

any ideas?

thanks. Overall i am digging ubuntu

---

### Post by alienexplorers on 2007-06-06
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by jusmurph on 2007-06-06
open Synaptec (sp?) Package Manager...

Do a search for ntfs and  you well be able to read off the relavent package you need in the results. I think it still requires a reboot to work but other than that it was as easy as that.

---

### Post by Bohlio on 2007-06-06
to find the /dev/??? of your partition, Type in this command ```

df -h
```
That will list your drives, look for the /media/(name) that it is on your computer and the corresponding /dev/??? should be there.

then mount it with NTFS-3G, it's what i used to mount my XP partition. It works great!

Just get NTFS-3G from the packet manager, then type this into terminal 
```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda2 /media/windows

```
replace "/dev/sda2" with whatever the partition is on your system.

and if you want it to load automatically at start up, add this to the end of your /etc/fstab file
```
/dev/sda2 /media/windows ntfs-3g defaults 0 0
```
once again, replace "/dev/sda2" with whatever the partition is on your system.

I think thats all covered then... :-)

---

### Post by kebabdylan on 2007-06-07
i tried what you wrote and the response was

fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/hda1 ()

---

### Post by alienexplorers on 2007-06-07
list 
> df -h
and
> sudo fdisk -l

---

### Post by Bohlio on 2007-06-07
> **kebabdylan said:**
> i tried what you wrote and the response was

fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/hda1 ()

DId you unmount the drive before you tried this?

---

### Post by kebabdylan on 2007-06-08
> **Bohlio said:**
> DId you unmount the drive before you tried this?

haven't had a chance to try the other suggestions, but...

If its unmounted, it doesn't show up when i run the df -h command.

---

### Post by kebabdylan on 2007-06-11
i tried remounting and walla! it worked. thanks all.

---

