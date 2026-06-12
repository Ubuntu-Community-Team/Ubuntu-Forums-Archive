---
title: "Can't mount flash drive, still in use by ntfs?"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Axis on 2007-12-19
I tried to mount my flash drive. It says that it was improperly unmounted (i'm guilty of that often when I am in a hurry). It says

Choice 1: if you have windows then disconnect the external devices by clicking on the 'safely remove hardware' icon in the winodws taskbar then shutdown windows cleanly.
Choice 2: If you don't have windows then you can use the 'force' option for your own responisbility. for example type on the command line: mount -t ntfs-3g/dev/sda1/media/disk-1 -o force
Or add the option to the releant row in the etc/fstab file:

/dev/sda1/meadia/disk-1 ntfs-3g defaults,force 0 0

How do I fix this? I tried some of the things they mentioned but I don't know if I did them correctly.

Thanks, Axis

---

### Post by approaching on 2007-12-19
If you have a windows box that mounts the flash, I would just go there and dump the files, then format the flash drive to fat 32 so that it can be properly used by both os's. (not saying that linux can't do ntfs, IMHO it's just a bit more reliable that way). then put the files back on it.

And don't you be ripping that poor drive out anymore!

---

### Post by Inxsible on 2007-12-19
> **Axis said:**
> 
How do I fix this? I tried some of the things they mentioned but I don't know if I did them correctly.

Thanks, Axis
Well, if you didn't perform the instructions clearly, they will not work. Make sure you do exactly what the instructions are. That should work. What else do you want us to tell you ?

---

### Post by Axis on 2007-12-19
> **approaching said:**
> If you have a windows box that mounts the flash, I would just go there and dump the files, then format the flash drive to fat 32 so that it can be properly used by both os's. (not saying that linux can't do ntfs, IMHO it's just a bit more reliable that way). then put the files back on it.

And don't you be ripping that poor drive out anymore!

Thanks, I have a windows box and I will give that a try.


> **Inxsible said:**
> Well, if you didn't perform the instructions clearly, they will not work. Make sure you do exactly what the instructions are. That should work. What else do you want us to tell you ?

Something a bit more constructive is what I was aiming for. My telling you that I had tried the instructions so that you didn't tell me to do what the instructions suggest. Which is what you did anyways so my mentioning that was a waste of time.

(Also you are told to give as many details as possible when describing a problem, so I did)

Thanks guys,

Axis

---

### Post by tech9 on 2007-12-19
> **Axis said:**
> I tried to mount my flash drive. It says that it was improperly unmounted (i'm guilty of that often when I am in a hurry). It says

Choice 1: if you have windows then disconnect the external devices by clicking on the 'safely remove hardware' icon in the winodws taskbar then shutdown windows cleanly.
Choice 2: If you don't have windows then you can use the 'force' option for your own responisbility. for example type on the command line: mount -t ntfs-3g/dev/sda1/media/disk-1 -o force
Or add the option to the releant row in the etc/fstab file:

/dev/sda1/meadia/disk-1 ntfs-3g defaults,force 0 0

How do I fix this? I tried some of the things they mentioned but I don't know if I did them correctly.

Thanks, Axis

you could try backing up your data, then format the drive as vfat - let me know if you need help doing that.

That may work

---

