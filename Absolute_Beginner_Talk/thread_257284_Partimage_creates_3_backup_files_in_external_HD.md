---
title: "Partimage creates 3 backup files in external HD?"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-09-14
Hello everyone,

I made a Backup of my system using Partimage and the Ubuntu Dapper Live CD and all went fine.
*Good 'ol psychocats!*
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
My /dev/hda2 Ubuntu partition was safely saved to my external HD /media/usbdisk. I went in there to take a look at my Backup and found out it's split into 3 files:

> hda2partition.001 = 2G
hda2partition.002 = 2G
hda2partition.003 = 141.4 MB
Note that these added up = hda2 backup partition.
I was expecting to discover 1 single file.

1. Why is that? Doess that mean something went wrong despite the "Success" at the end of the backup process?

2. More importantly, will that create a problem (when!) if I ever needed to restore using Partimage and the Live CD as described in the Psychocats HowTo?

3. Is it possible to delete a file from this Partimage backup? (within that backup lies another backup made a different way: "tar cvpzf backup.tgz / --exclude=/....." which I don't really need there). I guess I can't since it's an image!

Thank you much.

---

### Post by xyz on 2006-09-16
Hi-
I have brought down my hda2 Ubuntu partition to 2.5G and started to back it up.
My question is why, using this guide, is it seemingly impossible to create a backup file when it "weighs" more than 2G?
And does it matter {that the backup file is split} as far as restoring is concerned?

---

### Post by sjbrun on 2006-09-16
This is normal.
Partimage, by default, splits the backup image into 2gb files.
You can set the size of the files under the "image split mode" options on the second screen of partimage.

To restore the split image, just type the name of the first file into the "Image file to create/use" box (including the numbered extension) and choose the "Restore partition from image file" option.

---

### Post by xyz on 2006-09-16
> **sjbrun said:**
> This is normal.
Partimage, by default, splits the backup image into 2gb files.
You can set the size of the files under the "image split mode" options on the second screen of partimage.

To restore the split image, just type the name of the first file into the "Image file to create/use" box (including the numbered extension) and choose the "Restore partition from image file" option.

Thanks **sjbrun!**
Now it's clear and I'm glad to know that *just type the name of the first file into the "Image file to create/use" box (including the numbered extension)* will do the trick!
Have a good weekend!

---

