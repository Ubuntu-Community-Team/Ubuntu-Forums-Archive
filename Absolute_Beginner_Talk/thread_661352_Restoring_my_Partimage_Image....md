---
title: "Restoring my Partimage Image..."
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by xbhp13u on 2008-01-07
I can not get partimage to see my back up files.   The image is spread across 3 files.

The partition I want to restore is sda1 and the files are on sdb1.  I have copies of the files in both the root directory of sbd1 and also in a directory named "restore"

The files are definitely  there but partimage can't see them.  What do I have to do to get them to be seen?

i have tried  /mnt/restore/image_file.000 
/mnt/restore/image_file

and just about every variant of leaving the mnt off and leaving restore off and leaving the file numbers off.  

I guess I just don't understand the file system in linux enough yet

Please help.

Thanks

---

### Post by xyz on 2008-01-07
Hi,
Have you checked [Psychocats?]("http://www.psychocats.net/ubuntu/partimage")

> The restore process is very similar except that you choose the Restore partition from an image file option when PartImage launches. Note: the file name of the partition image to restore may have some numbers (00, for example) tacked on to the end of it—that's normal.
Good luck.

---

### Post by xbhp13u on 2008-01-07
Yeah, that doesn't help though.

I am running from the rescue cd.

When I created the image file i did the following

open terminal

cd /mnt

mkdir restore

ntfs-3g /dev/sda2 /mnt/restore

Then opened partimage

Saved sda1 image to /mnt/restore/image_file

This was successful in creating the files.

Now when reboot with the rescue cd and try to restore the image, partimage says it can't find the file.

I have tried doing it with doing the same terminal commands (i.e. mkdir and /mnt, etc.) and without doing anything in terminal.

---

### Post by bodhi.zazen on 2008-01-07
You run partimage (as root) to restore (best form a live CD). Form there choose the restore option and when it asks for an image, point to the one with ".00"

---

### Post by xbhp13u on 2008-01-07
> **bodhi.zazen said:**
> You run partimage (as root) to restore (best form a live CD). Form there choose the restore option and when it asks for an image, point to the one with ".00"



So, by that do you mean that I just go into partimage without doing anything in terminal?  I don't have to mount the sdb1 drive?

---

### Post by xbhp13u on 2008-01-07
I guess I am having trouble mounting the drive with the image files.  How do I do that?

---

### Post by bodhi.zazen on 2008-01-07
1. Boot the live CD, install partimage

2. mount (you said sdb1)

```
sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
```

3. Run partimage as root :

```
sudo partimage
```

---

