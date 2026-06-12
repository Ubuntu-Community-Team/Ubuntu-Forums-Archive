---
title: "Is it possible?"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by benjiej on 2006-02-08
I would like to know if it is possible to move files from one Fat  32 partition to another while runnind Live CD?

---

### Post by TrendyDark on 2006-02-08
Should be possible if you mount them correctly.

```

sudo mkdir /media/drive1
sudo mount /dev/hda1 /media/drive1/ -t vfat -o iocharset=utf8,umask=000

sudo mkdir /media/drive2
sudo mount /dev/hda1 /media/drive2/ -t vfat -o iocharset=utf8,umask=000

```

That should work. Try it, let me know.

edit: make sure you get the drive/partition correct when mount, those are just examples.

---

### Post by benjiej on 2006-02-08
Trendy,
     I wanted to say thanks for your help. I was able to mount my windows partition and pull my save files onto my external HD. So now worst case is simply to reformat my C: Drive and reinstall windows.

Benjie

---

### Post by warleggon on 2006-02-08
I'm not using the live cd, but I have two partitions that are ntfs that appear in Ubuntu. How can I set the mount so that they are accessable? Where are the files that would need to be changed?

---

### Post by Sutekh on 2006-02-08
[QUOTE=warleggon]I'm not using the live cd, but I have two partitions that are ntfs that appear in Ubuntu. How can I set the mount so that they are accessable? Where are the files that would need to be changed?[/QUOTE]
You can mount them very easily.

Check out this great link
[Mounting Windows Partitions in Ubuntu - by ]("http://www.psychocats.net/linux/mountwindows.php")[aysiu]("http://www.ubuntuforums.org/member.php?u=21941")

---

### Post by warleggon on 2006-02-08
Thank you. That was very easy and now I can do what I need to with them.

Warleggon :)

---

