---
title: "USB mounting mayhem"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by aijazbaig1 on 2007-05-17
Hello there.
I have been trying to get my USB working..Ive read a whole bunch of documentation..managed to get it fat formatted..and even transferred a 700MB chunk to see if its working..and it does..

Now the thing thats bothering me is that..i wanna revert back to the original (default) location where ubuntu normally mounts up a USB stick..

I think it is /media/usbdisk/ cuz whenever i remove the usb the dir disappears..so i changed the line in the /etc/fstab file from

```

/dev/sda1 /mnt/usbdrive auto users,noauto 0 0

```

to 
```

/dev/sda1 /media/usbdisk auto users,noauto 0 0

```

Now when i use the explorer GUI to check the contents..and when i click on the USB flash in the left menu..it gives an error which says that mount couldnt determine the file type. how is this a problem as the mtab files does say something abt the file type of the /dev/sda1 device as being vfat.

By the way heres what i see when i use the lsscsi command:
```

[10:0:0:0]   disk    SanDisk  Cruzer Micro     0.4   /dev/sde

```

what the heck does sde mean??..i mean i guess its cuz im removing that darn thing before unmounting it and hence it still has sda,sdb,sdc.......sde...alongwith corresponding folders in the /media/ directory which look like usbdisk-1,usbdisk-2......usbdisk-4.....chk out the 2nd pic...

i dont really get this. SInce my GUI says it isnt mounted...i mean isnt mounted at the given location which i specified in the mtab file...so how am i now being able to access it in those newly created folders..(directories..each time i can find the stuff in the last in the list directory..for instance..the 4th time i plugged it in i cud find the stuff in usbdisk-4)

I am getting really irritated at all this.:mad:

.is there a way to get things to square one and do all the stuff again..im inlcudin the snapshots which shoes the errors that it gives in addition to the /etc/fstab and /etc/mtab files(had to rename them to .txt or else ubuntu wudnt allow em to get uploaded)

hope to hear from u guys..

---

### Post by Iokua on 2007-05-17
You said you formatted your USB drive as FAT32? Try specifying the filetype in fstab instead of auto. So change:

```
/dev/sda1 /media/usbdisk auto users,noauto 0 0
```

to this:

```
/dev/sda1 /media/usbdisk vfat users,noauto 0 0
```

And then remount it with:

```
mount -a
```

---

### Post by gn2 on 2007-05-17
Have you tried the Automatix auto-mounter for NTFS and Fat32?

It mounts and makes NTFS and Fat32 writeable automatically.

Once Automatix is installed, it's in the "Miscellaneous" category.

[www.getautomatix.com](www.getautomatix.com)

---

### Post by Iokua on 2007-05-17
Wait. Are you sure your USB drive is /dev/sda1? Or is it /dev/sde? 

What is the output of:

```
sudo fdisk -l
```

---

