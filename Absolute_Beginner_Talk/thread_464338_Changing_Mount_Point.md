---
title: "Changing Mount Point"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by 42Wired on 2007-06-04
I like to keep a fairly empty desktop, and I know that anything mounted under /media appears on the desktop, so to resolve this, I want to change where some extra partitions are mounted, but I don't know how to go about doing this.

---

### Post by Ek0nomik on 2007-06-04
If you want to get rid of the icons on your desktop, simply:

```
gconf-editor
```

I believe it is under Apps > Nautilus > Desktop, but I could be mistaken.  I am at work on Windows right now.

---

### Post by Bohlio on 2007-06-04
Im guessing the command is ```
 mount /dev/sda2 /mnt/storage 
```
Replace "sda2" with the disk and partition you want to mount, and change "storage" to whatever label you want your drive to have. But i am not 100% sure here, so I'd wait for another opinion :-P

Edit: I guess you could remove the Icon with gconf-editor, I never thought of that. And using the method i supplied, I think you would also have to change /etc/fstab in order to get it to work correctly also. Once again, this is just guessing, as i recently mounted my windows partition with nfts-g3 and am going from memory here.

---

### Post by Nekiruhs on 2007-06-04
@ Above poster: You got it right.
@ OP what I would do is ```
mount /dev/??? /home/USERNAME/whatever/
```
where ??? is the designation (sda, hda) and USERNAME is your user name, and whatever is the folder you want it to be.

---

### Post by Bohlio on 2007-06-04
> **Nekiruhs said:**
> @ Above poster: You got it right.


Woohoo! I'm learning correctly! Anyways, Will the thread starter have to add another line with the mount point he chooses in the Fstab file? I had to add this ```
/dev/sda2 /media/windows ntfs-3g defaults 0 0
``` In order to get my windows partition to mount automatically using the ntfs-3g driver.

---

### Post by Nekiruhs on 2007-06-04
> **Bohlio said:**
> Woohoo! I'm learning correctly! Anyways, Will the thread starter have to add another line with the mount point he chooses in the Fstab file? I had to add this ```
/dev/sda2 /media/windows ntfs-3g defaults 0 0
``` In order to get my windows partition to mount automatically using the ntfs-3g driver.
Yeah, but, to have it automount in his home dir youd change /media/windows to ~/windows

---

### Post by bapoumba on 2007-06-04
1- make a file to mount your extra partition:
```
sudo mkdir /mnt/storage
```
assuming storage is the filename you choose.

2- save your current fstab:
```
sudo cp /etc/fstab /etc/fstab.bak
```

3- edit your fstab
```
sudo nano /etc/fstab
```
go to the line of your extra partition, change the mount point to the new file (/media/storage for ex).
CTRL-O to save the file (same name, hit <enter>), CRTL-X to exit nano.

Will take effect next reboot.

As an example, here is my fstab. In red are the mount points. You should have one that reads /media/<something>, other than cdrom or floppy. This is the one you want to change.
```
~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=671c9026-99b7-4b8c-9456-2c893897de48 [COLOR="Red"]/ [/COLOR]              ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=36cd4898-7cc2-4bac-b482-fd7fcef827c3 [COLOR="Red"]/home[/COLOR]           ext3    defaults        0       2
# /dev/hda3
UUID=35f61872-a12a-4b97-a938-daf3fdb21b04 none            swap    sw              0       0
/dev/hdc        [COLOR="Red"]/media/cdrom0[/COLOR]   udf,iso9660 user,noauto     0       0
/dev/fd0        [COLOR="Red"]/media/floppy0[/COLOR]  auto    rw,user,noauto  0       0

```

---

### Post by 42Wired on 2007-06-04
> **Bohlio said:**
> Im guessing the command is ```
 mount /dev/sda2 /mnt/storage 
```
Replace "sda2" with the disk and partition you want to mount, and change "storage" to whatever label you want your drive to have. But i am not 100% sure here, so I'd wait for another opinion :-P

Edit: I guess you could remove the Icon with gconf-editor, I never thought of that. And using the method i supplied, I think you would also have to change /etc/fstab in order to get it to work correctly also. Once again, this is just guessing, as i recently mounted my windows partition with nfts-g3 and am going from memory here.

I get "mount point /media/[new name] does not exist." How do I tell it to create it?

---

### Post by bapoumba on 2007-06-04
> **42Wired said:**
> I get "mount point /media/[new name] does not exist." How do I tell it to create it?
See point 1-in my post above yours. Then manually mount your partition.

BTW: removing the files mounted in /media from the desktop in gconf-editor will also prevent any other files mounted there to show up (cdroms, usb drives, floppies etc.).

---

### Post by Bohlio on 2007-06-04
Ahh I forgot about making the directory, That stumped me for a good 10 minutes when i set it up :-P

---

### Post by 42Wired on 2007-06-04
> **bapoumba said:**
> See point 1-in my post above yours. Then manually mount your partition.

BTW: removing the files mounted in /media from the desktop in gconf-editor will also prevent any other files mounted there to show up (cdroms, usb drives, floppies etc.).

I probably should have read the posts above mine before posting. lol

I just wanted to move two Windows partitions. I don't need to access them through Ubuntu, so I don't want them on the desktop. *That* won't affect the USB and CD-ROM drives' icons on the desktop, will it?

---

### Post by bapoumba on 2007-06-05
> **42Wired said:**
> I probably should have read the posts above mine before posting. lol

I just wanted to move two Windows partitions. I don't need to access them through Ubuntu, so I don't want them on the desktop. *That* won't affect the USB and CD-ROM drives' icons on the desktop, will it?
No, if you kept the /media mount point in fstab for cdrom, and kept the gconf key ticked (> Apps > Nautilus > Desktop > volume_visible ticked).

If not sure, paste in here your fstab:
```
cat /etc/fstab

```

---

