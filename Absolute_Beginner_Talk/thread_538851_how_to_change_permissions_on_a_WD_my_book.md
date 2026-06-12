---
title: "how to change permissions on a WD my book"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by yon2501 on 2007-08-30
hey ive got a 500gb Western Digital my my book essentials edition that for some reason decided that it wouldnt let me write or move any data on it, it just decided this today it was working last night. when i plug it in it reads as a read and write drive but the second i try and write something to it, it changes to a read-only drive i tried simply changing permissions but that wont let me it says its a read only drive. it then switches to a read only drive and says i cannot change the permissions because i am not the owner. i have had this drive since before i had ubuntu and i used it with windows on the same computer, i dont know if that has anything to do with it but im just throwing that out there. also for some reason i cannot right click and unmount it because it just mounts itself again. anyone out there know anything to help me?

---

### Post by marco123 on 2007-08-30
First, to unmount the drive type "sudo umount -v /path/to/drive" (usually /media/name) into the Terminal.  There's a bug in feisty that wont let you unmount using the GUI.

Second, you probably need to install the ntfs-3g driver (it's in Synaptic) enable it, reboot, then type "sudo chown <yourname> /path/to/drive"  into the terminal.

---

### Post by LowSky on 2007-08-30
Ubuntu doesn't like NTFS (windows xp formated) drives. Using NTFS-3g helps but for some reason if you log into a NTFS drive on a windows computer and you dont disconnect it properly, Ubuntu can not write to it. It is a problem because the NTFS format doesn't finalize data until it is to be disconnected, this way the drive seems to work fast also leads to fragmented files which can lead to more errors

So if you use windows with the drive run on USB, always use the "safely remove hardware" icon in the toolbar. otherwise reformat the drive to ext3 or FAT32... this way your errors wont show up.

---

### Post by yon2501 on 2007-09-09
well this is just a recent problem i had lost the power adapter for the drive and just recently i got the new one in the mail but before that it worked perfectally and even with the whole not writing it immediately thing it would still work when i hit the power button on the drive. it only started acting up when i went through and cleaned it up a bit. by "yourname" you mean my profile name right?

---

### Post by nonewmsgs on 2007-09-09
```

sudo nautilus

```
will let you modify files as root.  it by passes things if permissions are messed up, but it's really only a temporary solution.

---

