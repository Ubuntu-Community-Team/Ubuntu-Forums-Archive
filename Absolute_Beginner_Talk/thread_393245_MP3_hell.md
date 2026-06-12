---
title: "MP3 hell"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by jrekkedal on 2007-03-25
Ok, I have one of those chinese rip-off MP3/MP4 players.  I cannot write to the thing, even though I can read it's contents.  As you can imagine, this makes synching with Amarok a living hell.  When I plugin the device, Ubuntu (Edgy 6.10) sees it, and mounts it.

Mount point is /media/usbdisk, /dev/sdb1

Here is some output that might give you an idea of what I'm working with:

```
$ sudo fdisk -l

Disk /dev/sdb: 4196 MB, 4196860928 bytes
32 heads, 63 sectors/track, 4065 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4066     4098496+   b  W95 FAT3
```2

```
$ ls -la /media

drwx------  3 jrekkeda jrekkeda 4096 1969-12-31 19:00 usbdisk
```

Any ideas would be greatly appreciated.

---

### Post by lamalex on 2007-03-25
look up see what protocol it uses to transfer, it might need libnjb or libmtp, libgpod, something like that.

---

### Post by aysiu on 2007-03-25
That's annoying. Usually FAT32 is mounted with the correct permissions, unless that really does say *FAT3* and not *FAT32*.

I suppose you could *force* it to mount with the correct permissions as a workaround. Keep the drive plugged in and paste these commands into the terminal: ```
sudo mkdir /media/usbdisk
sudo nano -B /etc/fstab
``` Add this line at the end of the file: ```
/dev/sdb1 /media/usbdisk vfat iocharset=utf8,umask=000 0 0
``` Save (Control-X, Y, Enter) and then ```
sudo mount -a
```

---

### Post by jrekkedal on 2007-03-25
> **aysiu said:**
> That's annoying. Usually FAT32 is mounted with the correct permissions, unless that really does say *FAT3* and not *FAT32*.

I suppose you could *force* it to mount with the correct permissions as a workaround. Keep the drive plugged in and paste these commands into the terminal: ```
sudo mkdir /media/usbdisk
sudo nano -B /etc/fstab
``` Add this line at the end of the file: ```
/dev/sdb1 /media/usbdisk vfat iocharset=utf8,umask=000 0 0
``` Save (Control-X, Y, Enter) and then ```
sudo mount -a
```

Thanks for the fast replies.

I tried the code you mentioned, and it looked as if it would work but no dice... still read-only.

That is supposed to say "FAT32" but the code flag cut off the "2".

---

### Post by aysiu on 2007-03-25
Can you try a reboot and see if it's still no dice?

---

### Post by timcredible on 2007-03-25
can't you just copy-paste the mp3 files onto the device?  amarok is great, but no need for it for most mp3 players, they just auto-mount as a normal usb device and you just copy-paste files to them.

---

### Post by jrekkedal on 2007-03-26
Ok, get this:  I took the player to work today and hooked it up to my XP machine.  It picked it up the same as my Ubuntu machine (Generic USB drive) and opened the folder view.

Inside was a linux hidden folder (.Trash-jrekkeda I belive it was called)  When trying to open the folder it would give an error that it was corrupted data and wouldn't even let me delete it.

I performed a windows Chkdsk on it, and the folder was gone afterwards.  Within XP I dropped a few songs on it I had on a flash drive (which I took from my linux box at home).

I'm going to take this thing home tonight, plug it back in and see if the chkdsk fixed anything previously not working.  In the meantime, anyone has any thoughts?

---

