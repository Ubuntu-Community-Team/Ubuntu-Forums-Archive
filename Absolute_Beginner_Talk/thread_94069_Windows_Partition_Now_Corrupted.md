---
title: "Windows Partition Now Corrupted"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by jdgiotta on 2005-11-23
I accidentally erased part of my Windows XP partition on my machine. I had Linux and windows both bootable. Now windows won’t boot at all and when I try to mount it I get read errors.
    Is there anything that would repair the NTFS partition errors? I just want to recover my files… I can deal with a re-install of windows, but I’m worried I lost something important.

---

### Post by Brunellus on 2005-11-23
you didn't set the NTFS partition to be writeable did you?

---

### Post by jdgiotta on 2005-11-23
Negative. I was installing Breezy to a new partition, but I think the resizing of the NTFS partition did something very bad.

---

### Post by Brunellus on 2005-11-23
did you defrag the NTFS partition before resizing?

---

### Post by jdgiotta on 2005-11-23
Yes I did.

---

### Post by aznboi on 2005-11-23
have u tried a repair installation with the windows xp cd on the xp partition?

---

### Post by jdgiotta on 2005-11-23
Yes, but I don't get anything from the disk.
I'm prompted if I want to boot from disk then I get a blank screen.

Nothing happens.

---

### Post by Kapre on 2005-11-23
[QUOTE=jdgiotta]Yes, but I don't get anything from the disk.
I'm prompted if I want to boot from disk then I get a blank screen.

Nothing happens.[/QUOTE]

jdgiotta - If you want to get files off your M$ drive, try using the LiveCd (Ubuntu, Knoppix, Mepis) so you'll have access to your NTFS. If the M$ Cd wont boot also, try using a boot diskette (download it or if you have one use it) and use fdisk /mbr (to fix the boot record).

K

---

### Post by jdgiotta on 2005-11-23
@Kapre: I have the Ubuntu 5.10 LiveCD. I just want to try and rescue some of files from the errored MS partition.

The Windows boot CD won't work and I don't have a floppy drive.

---

### Post by jdgiotta on 2005-11-27
I logged in as root and I mounted the partition to /media/windows
Then I try to list the directory and I get the following error(s):
```
[4294883.560000] NTFS-fs error (device hda1): ntfs_end_buffer_async_read(): Buffer I/O error, logical block 39335008
```
[SIZE="1"]* Error goes on, but I'm unable to copy it's entirety.[/SIZE]

Can I repair ntfs blocks within linux?

---

