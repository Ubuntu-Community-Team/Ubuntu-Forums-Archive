---
title: "Stray file removal"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by red_Marvin on 2006-03-30
I was moving a folder from computer to an usb memory, and then unmounted.
But the next time I used the usbmem the "folder" showed up as a gnome-foot (unidentified)
file, and I couldn't remove it, standard deleting or # rm -f
Any suggestions?

Edit: I just noticed that I cannot write to *any* part of the usbdisk now, and I only had ~4MB worth of data left to move AAAAUGH!

---

### Post by nalmeth on 2006-03-30
Sounds like you're getting some permission problems.
Try doing everything you need to with "sudo"
as in 
sudo rm -i

---

### Post by red_Marvin on 2006-03-30
Sorry for being unclear, the # was to show that I have su/sudo rights, and even then it gives an input/output error.

With your suggestion:
> rm -i x8
rm: kan inte ta status (lstat) på "x8": In/ut-fel

This translates to
rm: can not read status (lstat) of "x8": I/O error.

---

### Post by nalmeth on 2006-03-30
So the USB device worked before, then you unplugged it, it left a folder/files which you can't remove, and now you can't read from the device, although it does mount?
Is this correct?

---

### Post by red_Marvin on 2006-03-30
Yeah, my guess is that I thought it had finished unmounting/writing data when unplugging it, but it hadn't

---

### Post by steve.horsley on 2006-03-30
Sounds as though the stick needs unmounting and checking with fsck.

---

### Post by red_Marvin on 2006-03-30
Output:
> root@HERCULES:/# fsck /dev/sda1
fsck 1.38 (30-Jun-2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/LEOS/X8
  Contains a free cluster (50275). Assuming EOF.
/festbilder/1/~psC5.tmp
  File size is 36634624 bytes, cluster chain length is > 36634624 bytes.
  Truncating file to 36634624 bytes.
Reclaimed 479 unused clusters (3923968 bytes).
Leaving file system unchanged.
/dev/sda1: 279 files, 50262/63964 clusters


---

### Post by red_Marvin on 2006-03-31
Thank's for the help, after reading manpages etc. I tried
dosfsck -r /dev/sda1
un+remount
rmdir /media/usbdisk/leos/x8
which worked! :D

---

