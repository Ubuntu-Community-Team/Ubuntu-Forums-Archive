---
title: "[SOLVED] cant seem to restore with partimage"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by rusty4r on 2008-04-15
I used partimage to create an image of my Edgy system (sda5) and saved the image on an ext3 partition (sda7) before I installed Gutsy (on sda5).

Now I need to expand that image file to get something that I forgot to copy (although I was making an image file so I wasnt really worried about it).

I dont want to overwrite Gutsy, so I need to expand the image somewhere else. sda7 has nothing on it but the image file so it is a good choice. I copied the image file to a usb disk mounted at /media/disk. Then typed sudo umount /media/sda7 and then sudo partimage.

After choosing sda7 and typing the location of the image file (/media/disk/Backups/sda5partition.000) partimage will not let me choose the option for restore a partition from an image file. Am I doing something wrong that anyone can see

Thank you for any help

---

### Post by logos34 on 2008-04-15
Did you gzip it, and if so is sda7 large enough to hold the uncompressed restored image?

---

### Post by rusty4r on 2008-04-15
yes I did, and yes it is.

Thanks for your help

---

### Post by rusty4r on 2008-04-16
Ok for anyone who might have read and be interested; I finally figured this out. I never read anywhere that you needed to use the space bar to select which operation to perform. Seems silly now, but finally got the image restored. 

Thanks to all who read my question

---

