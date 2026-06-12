---
title: "How do I format a USB stick"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by jsmidt on 2006-08-14
I have a USB memory stick and I would like to format it.  How do I?

---

### Post by Buzzygirl on 2006-08-14
Are you talking about a USB flash drive?

---

### Post by jsmidt on 2006-08-14
> **Buzzygirl said:**
> Are you talking about a USB flash drive?

Yes

---

### Post by kaamos on 2006-08-14
1) use synaptic to install gparted

2) disable automounting in System->Preferences->Removeble drives and media

3) use gparted to format the drive

4) re-enable automounting

---

### Post by geokok1981 on 2006-08-14
isn't there anything faster kamos?
all that seems to much to just format a usb flash...

---

### Post by amoser on 2006-08-18
yeah there is a faster way

1. Plug in the USB drive, and open a terminal.
2. On the USB drive icon, right click and go to eject
3. In the terminal, type sudo mkdosfs -I /dev/sda
4. Unplug the usb drive and plug it back in

~Alan

---

### Post by anaconda on 2006-08-18
And that is IF your USB-drive is indeed sda !!
If you have a SATA disk (which is sda) then you would be formatting your SATA disk..

Be careful..

---

### Post by dca on 2006-08-18
I got around okay sticking it in a MSWin2k box and right-clicking USB drive and used format option to quick-format in 'FAT'...  Works on my Win2k Server boxes, my Linux laptop, etc...

---

### Post by Turtle.net on 2006-11-05
That would be nice to have a right-click feature to format it (as a floppy).

Maybe, I'm just dreaming... :)

---

### Post by Harin on 2007-01-18
kaamos you are awesome. gparted worked where qtparted failed rather miserably.

---

### Post by diskotek on 2007-05-22
prefer gparted! thanks

---

