---
title: "Read only NTFS folder"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Whatever6750 on 2008-03-11
I have a folder with sub-folders and files thats on a NTFS partition that I need to be read-only. I have read that with a NTFS partition you can't set permissions though. Is there anyway I could accomplish this?

Note I don't want to make the whole partition read-only.

---

### Post by ibizatunes on 2008-03-11
Which version of ubuntu are you using 7.10 or a earlier version
7.10 will allow you read \ write access by default.....

---

### Post by njparton on 2008-03-11
Are you sharing it via samba or is it within the same PC?

---

### Post by Whatever6750 on 2008-03-11
I'm using hardy heron alpha 6.  I have read / write access, thats not the problem. Its that I don't want write permissions on a particular folder/files.

The hard drive is in the same PC. Last time I used ubuntu I had the drive in another PC and shared / mounted in ubuntu and that way I was able to do what I wanted.

---

### Post by PmDematagoda on 2008-03-11
> **Whatever6750 said:**
> I'm using hardy heron alpha 6.  I have read / write access, thats not the problem. Its that I don't want write permissions on a particular folder/files.

The hard drive is in the same PC. Last time I used ubuntu I had the drive in another PC and shared / mounted in ubuntu and that way I was able to do what I wanted.

At the current state of the ntfs-3g drivers I do not think that you can change permissions on NTFS partitions.

Also may I ask as to why you are using Hardy Heron? Surely you know that it is still in development and is not recommended for beginners.

---

### Post by Whatever6750 on 2008-03-11
> **PmDematagoda said:**
> At the current state of the ntfs-3g drivers I do not think that you can change permissions on NTFS partitions.

Also may I ask as to why you are using Hardy Heron? Surely you know that it is still in development and is not recommended for beginners.

Thats what I was fearing.

Well I guess I'm not a total beginner. I Have used ubuntu off an on and just wasent sure if there was any way to do what I wanted and couldent find any way to myself.

---

### Post by forrestcupp on 2008-03-11
Actually, you can set permissions.  You just have to be root to do it.

Open up a terminal and type:
```
sudo nautilus
```
That opens your file browser with root privileges. **Be Careful.**

Find your NTFS drive, usually mounted in /media.  Then you can navigate to the folder you want to change, right click and choose properties.  Click the Permissions tab and change the 'Folder Access' options to either 'Access Files' or 'List Files Only' if you don't even want to open them.

---

### Post by Whatever6750 on 2008-03-11
> **forrestcupp said:**
> Actually, you can set permissions.  You just have to be root to do it.

Open up a terminal and type:
```
sudo nautilus
```
That opens your file browser with root privileges. **Be Careful.**

Find your NTFS drive, usually mounted in /media.  Then you can navigate to the folder you want to change, right click and choose properties.  Click the Permissions tab and change the 'Folder Access' options to either 'Access Files' or 'List Files Only' if you don't even want to open them.

I tried that and it doesn't seam to do anything. It either closes on its own or has some error in the terminal and doesn't save any settings.

---

