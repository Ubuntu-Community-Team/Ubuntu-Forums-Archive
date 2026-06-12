---
title: "Naming ext3 partitions?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Zalbor on 2007-05-25
I have a portable (USB) hard drive, on which I've made 3 partitions. One is NTFS, the other FAT32, the third ext3.
When formatting the first two (from windows) I had the option to name them. Now when I connect the disk while in ubuntu, these two partitions get mounted at /media/<partition name>. The ext3 partition however is mounted at /media/disk.
Is there a way to name the ext3 partition, so that it will be mounted in a differently named directory? If not, is there a way to make sure that this partition will be mounted to a directory I've set whenever I plug the disk in? I assume that making an fstab entry wouldn't work, since this disk won't always be connected.
Thanks.

---

### Post by Inxsible on 2007-05-25
first, delete the existing mount point.

then,
```
 
sudo fdisk -l

```

Note the device name of the drive/partition that you want to mount. Then do:
```

sudo pmount /dev/sd** <whatever-name you want>

```

pmount is specifically used to mount external drives. They will always mount under /media
so for eg
```

sudo pmount /dev/sdb1 MyStuff

```
will mount it under /media/MyStuff


Hope that helps !

---

### Post by Zalbor on 2007-05-25
It kind of helps, thanks. But I want them to be automatically mounted to a specific place, so that I won't have to manually mount it every time I plug it in.

---

### Post by ruy_lopez on 2007-05-25
You can change the name of a ext2/3 volume with:
```

e2label /dev/(device) new-label
```

Or you can control the name of the mountpoint by checking the properties of the already mounted disk, on the desktop, by clicking right-clicking the icon. There's a tab called volume, you can specify the mount point name. Just the name will do. From then on it will mount in /media/ using the name you give it. (This last is Feisty only, as far as I can tell).

---

### Post by Zalbor on 2007-05-25
It is possible to label an ext3 parititon then? Thanks, I think this will work for me! :D

---

### Post by Inxsible on 2007-05-25
With pmount you don't have to mount them every time. They mount automatically as external (removable) drives. At least it does for me !!

---

### Post by Inxsible on 2007-05-25
> **ruy_lopez said:**
> You can change the name of a ext2/3 volume with:
```

e2label /dev/(device) new-label
```[COLOR=Red]Or you can control the name of the mountpoint by checking the properties of the already mounted disk, on the desktop, by clicking right-clicking the icon. There's a tab called volume, you can specify the mount point name. Just the name will do. From then on it will mount in /media/ using the name you give it. (This last is Feisty only, as far as I can tell).[/COLOR]


This is exactly what the pmount command does. So there you have it, a graphical and a CLI way to do things. Linux is awesome, I tell ya !!:)

---

### Post by ruy_lopez on 2007-05-25
What I didn't mention above is that the GUI version sucks. It shows the current mount point as "/media/whatever" and there is a blank input field called "mount point", so you'd think it would take the same format. ie "/media/whatever" But after I tried it, the system refused to mount the usb disk, saying something about having a "/" in the name. If I didn't know better, I'd have thought I'd just ruined my disk. And there's no way to change it back, either. It has to be mounted to be changed with the GUI. Thankfully, I knew better, and forced a manual mount.

---

### Post by Inxsible on 2007-05-25
Well, thats one of the reasons why i prefer the command line, but its nice to know that we can do it via GUI too

---

### Post by coffeecat on 2007-05-25
I agree about using e2label. I've labelled all my multiboot and external HD ext3 partititions and I get meaningful labels on the Gnome desktop icons whenever they are mounted.

I know you didn't ask this, **Zalbor**, but I'd like to share something I discovered only recently. Someone may find it useful. It's a Windows thing I'm afraid. :(

If you want to label or relabel pre-existing NTFS or FAT32 partitions you can do so easily in Windows by:

Control Centre > Administrative Tools > Computer Management > Disk Management

Right click on partition, choose properties. Type in new label. Click Apply. Click OK.

Phew! I think I prefer 'sudo e2label /dev/partition new-label'. Much easier :)

---

### Post by bodhi.zazen on 2007-05-25
> **coffeecat said:**
> Phew! I think I prefer 'sudo e2label /dev/partition new-label'. Much easier :)

he he he, try this :

```
sudo mlabel i:NEW_LABEL
```

changes label of FAT from the linux command line (you have to install and configure mtools)

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

Scroll down to the label section ...

---

### Post by coffeecat on 2007-05-25
> **bodhi.zazen said:**
> he he he, try this :

```
sudo mlabel i:NEW_LABEL
```changes label of FAT from the linux command line (you have to install and configure mtools)

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

Scroll down to the label section ...

Thanks for that. I installed mtools once and never did work out how to (re)label fat32 partitions.

But has anyone done an NTFS relabel app for Linux? :D

Oh yes! Just read your link. They have. Wonderful. :lol:

---

