---
title: "Help! i cannot load my external hard drive"
date: 2008-12-23
forum: Apple Hardware Users
---

### Post by llfirefighter on 2008-12-23
Please bare with me... I know only enough to get me in trouble. Here's the story. I have a G3 with OS X 10.4.11. As u can imagine I hm running out of hard-drive space. My buddy gave me an HP 450 gb 3.5" SATA External Hard-drive. I have bought an enclosure, its an Eagle - Consus. with USB 2.0 Well when I power up my Mac will not recognize anything. Nothing initiates. When I connect to my girls compaq running vista it recognizes it. So it is not a hardware problem< its a compatibility issue. Can anyone shed some light on this for me please. It would be greatly appreciated!

Thank Luis

---

### Post by pxwpxw on 2008-12-23
> **llfirefighter said:**
> Please bare with me... I know only enough to get me in trouble. Here's the story. I have a G3 with OS X 10.4.11. As u can imagine I hm running out of hard-drive space. My buddy gave me an HP 450 gb 3.5" SATA External Hard-drive. I have bought an enclosure, its an Eagle - Consus. with USB 2.0 Well when I power up my Mac will not recognize anything. Nothing initiates. When I connect to my girls compaq running vista it recognizes it. So it is not a hardware problem< its a compatibility issue. Can anyone shed some light on this for me please. It would be greatly appreciated!

Thank Luis

The drive may be formatted so the macosx does not mount it, or maybe the G3 has a usb drive problem.
Use Macosx Applications:Utilities:Disk Utility and it should show you the drive is connected and what partitoning it is using, if it can see the drive at all.

You can also run terminal 
```

diskutil list

```
and that should  list all drives

---

### Post by llfirefighter on 2008-12-23
thanks for the quick reply pxwpxw
ya it wont recognize it in my disk utility...
when i input in terminal this is what i got:

/dev/disk0
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *76.7 GB  disk0
   1:    Apple_partition_map                    31.5 KB   disk0s1
   2:              Apple_HFS Macintosh HD       76.6 GB   disk0s3


Do you think I can some how format it on my pc to read on both pc and mac and then plug into my mac for recognition?

Thank you so much,
Luis

---

### Post by pxwpxw on 2008-12-23
> **llfirefighter said:**
> thanks for the quick reply pxwpxw
ya it wont recognize it in my disk utility...
when i input in terminal this is what i got:

/dev/disk0
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *76.7 GB  disk0
   1:    Apple_partition_map                    31.5 KB   disk0s1
   2:              Apple_HFS Macintosh HD       76.6 GB   disk0s3


Do you think I can some how format it on my pc to read on both pc and mac and then plug into my mac for recognition?

Thank you so much,
Luis
Well that is just showing the internal hard disk, so it looks as if the G3 is not recognizing the usb external at all - but make sure you have the external drive powered on and running before the G3 is started up and give it a few tries restarting, sometimes there is a problem there.
Try unpugging and replugging it in also to make sure

Some of the earlier G3 had limitations for usb, I dont know about that, someone else will help you with that if you post the G3 version/model (menubar-apple-about this mac-more-hardware)

If the enclosure and the g3 have a firewire connection, that could work better.

Someone else can probably say if it is the G3 limitation - my G4 ibook can certainly do usb and firewire external drives.

---

