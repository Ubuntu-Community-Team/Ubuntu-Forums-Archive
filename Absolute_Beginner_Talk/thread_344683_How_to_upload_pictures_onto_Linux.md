---
title: "How to upload pictures onto Linux"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by aggscott on 2007-01-23
I want to upload pictures from a memory card onto my computer. If I were in Windows I would put the card into a slot on the side of the laptop and a screen would come up and ask which program I wanted to use. 

What can I install that will help me do this? I really don't want to have to go over to Windows to upload pictures-I want to show my husband that we can use Linux for all that we need and want to do. :D

---

### Post by bodhi.zazen on 2007-01-23
Plug in your card and see if it is auto mounted.

If not, with the card plugged in:```
sudo fdisk -l
```to see the device.

Most likely it is at /dev/sda1

Thus:```
sudo mkdir /media/pictures
sudo mount /dev/sda1 /media/pictures
```

read-write permissions depend on the file system, likley fat, thus you can try to add -o umask=000 like this:

```
sudo mount /dev/sda1 /media/pictures -o umask=000
```

---

### Post by aggscott on 2007-01-23
I entered the command above the first one and I had the memory card in the slot and this is what came up-

sudo: fsdisk: command not found


I know I wrote it right because I did the copy and paste.

---

### Post by Wikzo on 2007-01-23
> **aggscott said:**
> I entered the command above the first one and I had the memory card in the slot and this is what came up-

sudo: fsdisk: command not found


I know I wrote it right because I did the copy and paste.
Same here. Just tried to plug in a Memory Duo Card from Sony.

---

### Post by Bachstelze on 2007-01-23
It's *fdisk*, not *f**s**disk*.

---

### Post by bodhi.zazen on 2007-01-23
Ooops, sorry for the typo.

Thanks HymnToLife. I'll edit my first post ...

---

### Post by Sbarton on 2007-01-23
Not so much a reply as a comment. I attempted this the other day with my USB card reader, it mounted straight away and all the photos were visible.
I created a couple of folders for the various images and then copied these to my home folder. It worked flawlessly and they are now ready for editing/viewing. So, just another tick for linux and Ubuntu.
regards :)

---

### Post by infoseeker on 2007-01-23
When I plug in my Samsung digital camera Kubuntu automatically detects it as a removable drive and I can copy the pictures to my ~/Pictures directory (or any self-created directory under ~/Pictures) using Konqueror.  Piece of cake =D> .

---

### Post by aggscott on 2007-01-23
O.K. thanks for that-it did come up with a bunch of things I do not understand-if someone could tell me what this means-that would be great..

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4275    34338906    7  HPFS/NTFS
/dev/hda2            4276        7169    23246055   83  Linux
/dev/hda3            7170        7296     1020127+   5  Extended
/dev/hda5            7170        7296     1020096   82  Linux swap / Solaris

---

### Post by oilchangeguy on 2007-01-23
have you tried clicking on places, home folder? it should be listed on the left side of that page under floppy or cd/rw, as removable media, or something like that. click on it and then click on the file or whatever is showing in the drive and you should be able to see your pictures.

---

### Post by bodhi.zazen on 2007-01-23
> **aggscott said:**
> O.K. thanks for that-it did come up with a bunch of things I do not understand-if someone could tell me what this means-that would be great..

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4275    34338906    7  HPFS/NTFS
/dev/hda2            4276        7169    23246055   83  Linux
/dev/hda3            7170        7296     1020127+   5  Extended
/dev/hda5            7170        7296     1020096   82  Linux swap / Solaris

If your camera/card reader is plugged in it looks like it is not recognized.

hda = your first hard drive

USB devices will be sda1

[list=number][*]If is a camera, turn it on (I have made this mistake with my camera :lol: ).
[*]If you camera is on and plugged in , re-run sudo fdisk -l
[*]If you still do not see the device listed as /dev/sda1, what type of camera/usb device is it ?[/list]

---

