---
title: "USB key question"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by Connollyir on 2006-01-14
This is a really simple question, and I did do a quick scan on the net but I need to know so I figured it would be faster to just ask. 

Does a USB key need to be formatted with a different filesystem than fat 32 in order to be used in Linux? I want to be able to use the key between many machines so that would be a problem.

Thanks


-Ian

---

### Post by 23meg on 2006-01-15
You can format it with any filesystem that Linux can read and write to, including FAT32.

---

### Post by Connollyir on 2006-01-15
[QUOTE=23meg]You can format it with any filesystem that Linux can read and write to, including FAT32.[/QUOTE]

Sweet. But I run into problems when I try and mount it. I use <sudo mount /dev/sda1/> but I get 

e@IansDreamMachine:~$ sudo mount /dev/sda1
Password:
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
e@IansDreamMachine:~$

when I use the lsusb command I get

e@IansDreamMachine:~$ lsusb
Bus 002 Device 005: ID 0781:7113 SanDisk Corp. Cruzer Micro 256MB Flash Drive
Bus 002 Device 004: ID 046d:c510 Logitech, Inc.
Bus 002 Device 003: ID 046d:c30a Logitech, Inc.
Bus 002 Device 002: ID 050d:0416 Belkin Components
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
e@IansDreamMachine:~$

The key is the first in the list.
I am used to mounting cds in my cdrom using the same command above with the cdrom ending (mount /dev/cdrom) but I don't know what I'm supposed to call the key. I imagine I could add a line in /etc/fstab to correct the problem but I don't know where the mount point is.


I feel really silly asking about it but I have looked and I can't seem to find anything that isn't about putting the Ubuntu cd on a key or something else that didn't apply to me.


Thanks


-Ian

---

### Post by steve.horsley on 2006-01-15
Try the following command sequence:

sudo mkdir /media/usb-pen
sudo mount -t vfat /dev/sda1 /media/usb-pen

I came across an MP3 player recently that was formatted such that you had to mount it as /dev/sda rather than /dev/sda1 - i.e. it had no partition table.

HTH
Steve

---

### Post by Connollyir on 2006-01-15
[QUOTE=steve.horsley]Try the following command sequence:

sudo mkdir /media/usb-pen
sudo mount -t vfat /dev/sda1 /media/usb-pen

I came across an MP3 player recently that was formatted such that you had to mount it as /dev/sda rather than /dev/sda1 - i.e. it had no partition table.

HTH
Steve[/QUOTE]

Awesome - that worked.

Thanks a bunch

-Ian

---

### Post by Connollyir on 2006-01-15
Ok I retract my previous statement. I can't write to the drive or delete files from it - I only have read status. How do I change it?

PS. Why doesn't my stuff automount? It does in the Ubuntu I installed on my laptop but not here. I am using KUbuntu on this machine and when my laptop gets internet access I will install the K desktop on that also - is that a KDE and Gnome difference?

-Ian

---

### Post by kingsidy on 2006-01-15
you can try removing the line in fstab that refers to the usb drive if there are any. back up first before you make any changes. then plug the usb drive in, it should automount it and allow you to read and write. I have added the disk mount applet on the top menu bar. so whenever i plug in one of flash drive, i just click and then select mount device. the applet comes in handy in other situations as well give it a try.

---

### Post by Connollyir on 2006-01-15
[QUOTE=kingsidy]you can try removing the line in fstab that refers to the usb drive if there are any. back up first before you make any changes. then plug the usb drive in, it should automount it and allow you to read and write. I have added the disk mount applet on the top menu bar. so whenever i plug in one of flash drive, i just click and then select mount device. the applet comes in handy in other situations as well give it a try.[/QUOTE]

Well I removed the line for usb in fstab (btw I put that line there so I wouldn't have to type mount /dev/sda1 /media/usb-pen every time I wanted to mount the disk) which read like this < /dev/sda1    /media/usb-pen   auto   rw, user, noauto   0   0>. But when I removed that line the usb icon in the removable media applet in my taskbar disappeared. So I figured I would go back to what I had previously accomplished but when I placed the line I removed from fstab back in it verbatim I could no longer get to the usb drive, as in I got weird "you must specify a filesystem" errors. I checked the fstab entry and everything looks ok to me. 

Whats up now?

---

### Post by utabintarbo on 2006-01-20
[QUOTE=Connollyir]Ok I retract my previous statement. I can't write to the drive or delete files from it - I only have read status. How do I change it?

...

-Ian[/QUOTE]

Add an "-o rw" to your mount command ie.
```
sudo mount -t vfat -o rw /dev/sda1 /media/usb-pen
```

---

### Post by WirelessMike on 2006-01-26
[QUOTE=Connollyir]Well I removed the line for usb in fstab (btw I put that line there so I wouldn't have to type mount /dev/sda1 /media/usb-pen every time I wanted to mount the disk) which read like this < /dev/sda1    /media/usb-pen   auto   rw, user, noauto   0   0>. But when I removed that line the usb icon in the removable media applet in my taskbar disappeared. So I figured I would go back to what I had previously accomplished but when I placed the line I removed from fstab back in it verbatim I could no longer get to the usb drive, as in I got weird "you must specify a filesystem" errors. I checked the fstab entry and everything looks ok to me. 

Whats up now?[/QUOTE]

Add that line back in again, following up with making sure you have a directory usb-pen under /media but change that auto to vfat.

In other words, put everything back like it was, but change
 /dev/sda1    /media/usb-pen   auto   rw, user, noauto   0   0
to
 /dev/sda1    /media/usb-pen   vfat   rw, user, noauto   0   0

---

