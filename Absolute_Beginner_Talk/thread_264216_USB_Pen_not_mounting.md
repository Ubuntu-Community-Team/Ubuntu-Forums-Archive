---
title: "USB Pen not mounting"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by tom35i on 2006-09-24
Howdy
i hav search this forum for the answer so here i am asking

i have a few usb pens but ubuntu will not detect them. i hav been told that i should not hav 2 do any thing and that ubuntu will automaticly mount the drive but no such luck so i tryed using the mount commands and still no luck

any suggestions

---

### Post by bodhi.zazen on 2006-09-24
Put the USB pen in place.

Post the output of ```
sudo fdisk -l
```
That's a small "L" and not the nubmer 1.

---

### Post by tom35i on 2006-09-24
Cheers

Disk /dev/hda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14830   119121943+  83  Linux
/dev/hda2           14831       15017     1502077+   5  Extended
/dev/hda5           14831       15017     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14946   120053713+   7  HPFS/NTFS

Disk /dev/hdc: 61.4 GB, 61473226752 bytes
255 heads, 63 sectors/track, 7473 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        7473    60026841    7  HPFS/NTFS

---

### Post by bodhi.zazen on 2006-09-24
Do you have 3 HD ? USB devices are typically recognized as sdxy.

Which of these devices is your pen drive? (how big is your pen drive?).

---

### Post by Murmex on 2006-09-24
I don't think it's just "not mounting" but even not detecting. I have the same problem with an external usb disk. I have no problem with the usb pen I have, but with that usb disk (which worked several weeks ago and still works on other configurations) it's as if it wasn't plugged. There's no way to find it in lsusb or fdisk.

---

### Post by Murmex on 2006-09-24
I've just solved my problems with :
sudo modprobe -r ehci_hcd
(there were some references about that module in dmesg)

---

### Post by bodhi.zazen on 2006-09-24
> **Murmex said:**
> I've just solved my problems with :
sudo modprobe -r ehci_hcd
(there were some references about that module in dmesg)

Great !

Now>```
 gedit /etc/modules
```

Add ehci_hcd to the end of the file on it's own line.

Save and exit. Will now be available whenever you boot.

---

### Post by tom35i on 2006-09-25
Thank You

---

### Post by rocksplit on 2006-10-20
I had the same problem but when I tried to save the module's changes, I get a " could not save the file..." You dont have the permissions...
What can I do with this?

---

### Post by bodhi.zazen on 2006-10-21
> **rocksplit said:**
> I had the same problem but when I tried to save the module's changes, I get a " could not save the file..." You dont have the permissions...
What can I do with this?

Sorry, try this[```
**sudo** echo ehci_hcd >> /etc/modules
```

Or if you prefer a gui:
```
**sudo** gedit /etc/modules
```

Edit & now you should be able to save (as you opened with sudo).

---

### Post by CujoQuarrel on 2006-10-21
In the same vein.

If you have a usb drive/card/pen and you unmount it what would you do to mount it again? 

I put in my SD card into the reader and it appears on the desktop and an entry appears in /etc/mtab. I umount it and the entry disapears. 

How would I go about remounting the card. Right now I pop it out then back into the reader but I'd like to do that from the command line for a script I'm trying to write.

Thanks

---

### Post by bodhi.zazen on 2006-10-21
> **CujoQuarrel said:**
> In the same vein.

If you have a usb drive/card/pen and you unmount it what would you do to mount it again? 

I put in my SD card into the reader and it appears on the desktop and an entry appears in /etc/mtab. I umount it and the entry disapears. 

How would I go about remounting the card. Right now I pop it out then back into the reader but I'd like to do that from the command line for a script I'm trying to write.

Thanks

1. Add an entry in fstab.```
sudo gedit /etc/fstab
```
Add a line like this:> <device> <mount_point> vfat noauto,users,rw 0 0
2. Use the mount command.```
mount <device> <moutn_point>
```

---

### Post by CujoQuarrel on 2006-10-23
When you insert the mmc card it 'self mounts' somehow and puts an entry in the /etc/mtab. Popping the card out removed the entry. There is never an entry in the /etc/fstab. If you make an entry in the fstab it screws up the automounting when the card is inserted.

Trying to get a script together that unmounts the card, format's it, and remounts.

---

### Post by penguinman007 on 2006-10-23
Heres and idea,


when I put my usb key in , ubuntu mounts it automatically.
when I copy files to the key, they are copied.
when I pull the usb key out, ubuntu knows it's gone.


Is that too difficult ?


At the moment, everytime I remove the usb stick, I have to unmount and then re-start ubuntu so it automatically re-detects next time I put it in.

this is because a don;t want to edit setup files, or sudo anything, like 90% of other computer users.
Even though I am a programmer, my head is already full of java api, there is no more room for remembering the location of ubuntu specific settings files.
And no time to edit things for something as generic as using a usb key.

](*,)

---

### Post by bodhi.zazen on 2006-10-24
> **penguinman007 said:**
> Heres and idea,


when I put my usb key in , ubuntu mounts it automatically.
when I copy files to the key, they are copied.
when I pull the usb key out, ubuntu knows it's gone.


Is that too difficult ?


At the moment, everytime I remove the usb stick, I have to unmount and then re-start ubuntu so it automatically re-detects next time I put it in.

this is because a don;t want to edit setup files, or sudo anything, like 90% of other computer users.
Even though I am a programmer, my head is already full of java api, there is no more room for remembering the location of ubuntu specific settings files.
And no time to edit things for something as generic as using a usb key.

](*,)

Add an entry in /etc/fstab using a label.

With the USB device attached:
```
ls /dev/disk/by-label
```To determine the USB label.

The add an entry in /etc/fstab like this:> LABEL=<label> /media/usb auto users,rw 0 0

With this entry your USB should always be automounted by gnome-volume-manager.

---

### Post by TiredBird on 2006-10-24
Penguinman007,

I empathize completely with your desire to just have it work the way it should. Maybe I can help.

I have three thumb-drives and a USB connected external hard-drive. Whenever I insert one of them it mounts properly and other actions are carried out automatically. If I understand you correctly, you want that without a bunch of programming or complicated configuration files.

On some of my stuff the only difference is a colored dot on the outside and the manufacturer's serial number. It seemed reasonable to me to specify what I wanted each of them to do. 

However, there is no programming involved in any of what I did. I wrote a few udev rules, maybe 10 or 12 lines worth, and wrote a few scripts to automate some system commands. The scripts are short, some as small as two or three lines, the longest maybe ten or twelve lines.

I thought I was going to include a link in this post to the thread where all this got worked out, but it wasn't readily available. However, if you're interested it won't be hard for me to find. Just ask.

---

### Post by penguinman007 on 2006-10-24
Thanks for the responses.

Im interested in any script that I can put a link-to on my desktop, to unmount and re-mount the usb key.
Or anything that will allow me to re-mount the usb key after I have unmounted (right click usb key shortcut->unmount).

the command :
ls/dev/disk/by-label does not work for me.
My /dev doesn't have a subdirectory called /disk.

also the by-label option is not available in my ls command (ls --help)

my usb device is just a usb stick (sda1).

---

### Post by TiredBird on 2006-10-24
Penguinman007,

If you are using any flavor of ubuntu (kubuntu, xubuntu, edubuntu, etc.) then  /dev should have a sub-folder of 'disk' and 'disk' should have a sub-folder of 'by-label'. The command: ls /dev/disk/by-label should list the devices in there and if your USB device is plugged in, it should be in there. 'by-label' is not an option to the ls command, it is the sub-directory under 'disk' which is a sub-directory under 'dev'. It is possible that 'disk' and 'by-label' do not exist when your USB is not plugged in. However, when your USB is plugged in they should exist.

---

### Post by bodhi.zazen on 2006-10-24
> **penguinman007 said:**
> the command :
ls/dev/disk/by-label does not work for me.
My /dev doesn't have a subdirectory called /disk.

also the by-label option is not available in my ls command (ls --help)

my usb device is just a usb stick (sda1).

You need a space between ls and /dev: ls <sp> /dev/disk/by-label like this:
```
ls /dev/disk/by-label/
```

If you do not have an entry in fstab, you are automounting with gnome-volume-manager, which in turn uses pmount.

Thus to re-mount you would use:```
pmount /dev/sda1
```

A "script" to do this would be:> #! bin/bash
pumount /dev/sda1 && pmount /dev/sda1

Call it remount.

Save it to /usr/bin

make it executable:```
sudo chmod a+x /usr/bin/remount
```

Add a desktip icon or launcher.

Name = Remount

Command /usr/bin/remount

---

