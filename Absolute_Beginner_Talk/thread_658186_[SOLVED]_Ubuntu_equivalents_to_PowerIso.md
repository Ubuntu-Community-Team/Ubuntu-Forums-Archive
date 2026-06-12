---
title: "[SOLVED] Ubuntu equivalents to PowerIso?"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by 449 on 2008-01-04
I want to mount some Isos so I don't waste cds ,but don't know of a program that can do this? If anyone recommend me one that be great. Thank you for your time.

---

### Post by zeller on 2008-01-04
I'd love to do the same.

---

### Post by lgambett on 2008-01-04
Program ? What program ? You are using Linux, not Windows ! :)

mount -o loop will do the trick !

For example: suppose you have created the mount point /media/iso

sudo mount -o loop mycd.iso /media/iso

... and then you can browse the contents of the iso image...

---

### Post by edm1 on 2008-01-04
Two nautilus scripts i found somewhere on this forum ages ago serve me well. They go in ~/.gnome2/nautilus-scripts and need to be executable

Mount

```
#!/bin/bash
#
# nautilus-mount-iso

gksudo -u root -k /bin/echo "got r00t?"

sudo mkdir /media/"$*"

if sudo mount -o loop -t iso9660 "$*" /media/"$*"
then
        if zenity --question --title "ISO Mounter" --text "$* Successfully Mounted.
        
        Open Volume?"
        then
                nautilus /media/"$*" --no-desktop
        fi
        exit 0
else
        sudo rmdir /media/"$*"
        zenity --error --title "ISO Mounter" --text "Cannot mount $*!"
        exit 1
fi
```

Unmount

```
#!/bin/bash
#
for I in "$*"
do
foo=`gksudo -u root -k -m "enter your password for root terminal
access" /bin/echo "got r00t?"`

sudo umount "$I" && zenity --info --text "Successfully unmounted /media/$I/" && sudo rmdir "/media/$I/"
done
done
exit0

```

---

### Post by igknighted on 2008-01-04
The OS can just do it, you don't really need a special app.  Just use the mount command via the terminal:
```
sudo mount -t iso9660 -o ro,loop=/dev/loop0 <ISO_File> <Mount_Point>
```

That line was from bodhi's mounting how-to: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by kellemes on 2008-01-04
Or with gui..
[http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html](http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html)

---

### Post by FuturePilot on 2008-01-04
```
sudo apt-get install gmountiso
```
You'll find it under Applications>System Tools.

---

### Post by barbedsaber on 2008-01-04
If this is all sorted out, can you please mark the thread as solved, by clicking on thread tools, then going to the bottem fo the list.

---

### Post by kpkeerthi on 2008-01-04
Search for **cdemu** in the tutorials and tips section.

---

### Post by Jose Catre-Vandis on 2008-01-08
> **FuturePilot said:**
> ```
sudo apt-get install gmountiso
```
You'll find it under Applications>System Tools.

Brilliant :)

---

