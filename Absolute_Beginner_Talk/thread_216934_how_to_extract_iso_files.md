---
title: "how to extract iso files ?"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-07-16
I used ark but it didn't detect .iso format
I used archive manager but it only exctracted folders - but no files
and most of all it takes AGES to exctract...
what program should I use ?

---

### Post by christhemonkey on 2006-07-16
You can just mount the .iso and then copy the files out of it.
```
sudo mount -o loop -t iso9660 /path/to/iso/file.iso /media/cdrom 
```

Replacing /path/to/iso/file.iso and /media/cdrom with the actual place of the iso and where you want it mounted.

---

### Post by GarethMB on 2006-07-16
Using Gnome:

Right click CD icon.

Click Copy Disc.

Choose Create Image only.

Using K3b:
Choose Copy CD.

Choose Only create image

---

### Post by MaximB on 2006-07-16
1.I have managed to mount with the command line - but now I can't unmount
it says :umount: /media/cdrom0 mount disagrees with the fstab

2.I don't want to burn ISO image... I just want to extract it.
is there a program or somthing easier then the command line ?

---

### Post by christhemonkey on 2006-07-16
Hmm, maybe it shouldnt have been mounted there.
Next time maybe make a folder like /media/iso and mount it there.
But if you reboot it will be unmounted.
You can probably unmount without rebooting.
Mayhaps by using the -f option.
```
sudo umount -f /media/cdrom0 
```

---

### Post by MaximB on 2006-07-16
thanks - it helped
but is there a "GUI" for it ?
I don't really need to mount I need just to exctract the content of the .iso.
you know - like ISO buster or somthing...?

---

### Post by christhemonkey on 2006-07-16
Well, by mounting it, you can view the contents and copy it across.
There is a nautilus script for mounting iso and othe image types.
Howto available here:
[http://www.ubuntuforums.org/showthread.php?t=149963](http://www.ubuntuforums.org/showthread.php?t=149963)

---

