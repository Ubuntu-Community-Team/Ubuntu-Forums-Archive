---
title: "cannot connect to external usb hard drive"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by Tobitas on 2006-03-15
I have a 160 GB external hard drive formated in ntfs connected via USB to my old toshiba laptop. 
fdisk -l tells me that I have a connected disk, the device is /dev/sda1
I created a folder in /media called 160gb
I edited fstab and added this line:
/dev/sda1   /media/160gb   ntfs   rw,user,auto,sync  0  0
I confirmed with enter and saved the file
I then typed: sudo mount /dev/sda1

If I now navigate to the media folder in a file manager window and click on the 160gb folder it tells me: error scannint 'media/160gb' can't open directory: permission denied. 
Typing sudo chmod 666 /media/160gb results in this output:
chmod changing permissions of '/media/160gb': Read-only file system.

I still cannot access the folder.
Please help me localising the mistake.
Thanks 
Tobias

---

### Post by shof2k on 2006-03-15
See if you have read permission as user or as root.  This sounds like a permission issue.

You won't get write access as Breezy doesn't support NTFS writing.

---

### Post by Tobitas on 2006-03-15
I only have read permissions as root. How do I get read permissions as user.
Typing sudo chmod 444 /media/160 gb gives me: chmod changing permissions of '/media/160gb': Read-only file system
I still cannot access the folder. So yes, it is a permission problem. How can I solve this? Probably trivial, but I am really new to Ubuntu and Linux in general
Thanks
T

---

### Post by mlind on 2006-03-15
don't change the permissions of the mount point!

you need to mount your drive using umask attribute.
For example

```

/dev/hda5       /media/E        ntfs    ro,auto,nls=utf8,umask=0222     0      0

```

will allow everybody to access already mounted NTFS partition.
It will be mounted automatically and only root can umount/mount it.

---

### Post by JayjayAbnormal on 2006-03-15
I dont mean to go offtopic or anything, but since this thread is about external USB hard-drive's, is it possible, if I buy one, will I be able to install Ubuntu on it, and boot Ubuntu off of it using my pc? (I know it will only work on 1 pc cause the hardware configuration)

---

### Post by Tobitas on 2006-03-15
Hi mlind:
Is that the fstab entry I have to change again? can you explain me the meaning of the 4th column: ro,auto,nls=utf8,umask=0222?
Thanks

---

### Post by mlind on 2006-03-15
[QUOTE=Tobitas]Hi mlind:
Is that the fstab entry I have to change again? can you explain me the meaning of the 4th column: ro,auto,nls=utf8,umask=0222?
Thanks[/QUOTE]

yes, sorry. It's an /etc/fstab entry

ro --> read-only
auto --> drive is mounted automatically on boot sequence
nls=utf8 --> use UTF-8 character set for converting filenames
umask=0222 --> allow normal users to access the contents of this drive

there's bunch of other useful switches too, *man mount* will show them all.

If I wanted to mount this drive without corresponding fstab entry, I would do
```

sudo mount -t ntfs -o ro,umask=0222 /dev/hda5 /media/E

```

---

