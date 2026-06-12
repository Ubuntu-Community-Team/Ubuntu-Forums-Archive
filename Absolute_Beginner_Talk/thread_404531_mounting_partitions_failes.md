---
title: "mounting partitions failes"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by YSH on 2007-04-08
I have this script, diskmounter, which would mount my other partition, the C-disk, on which all the old windows-documents are, but when that script asks for my passwords i can't type my password, i also tryed the next line, but than he said it was false.

---

### Post by happymellon on 2007-04-08
> **YSH said:**
> I have this script, diskmounter, which would mount my other partition, the C-disk, on which all the old windows-documents are, but when that script asks for my passwords i can't type my password, i also tryed the next line, but than he said it was false.

I'm not sure what the question is so I'm going to cover a couple of option here.

If you want to mount a Windows drive you can always follow this tutorial:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

The simple command to access if you left Windows as the first partition on the first drive it should be:

sudo mount /dev/hda1 /media/c

If you don't know what partition and drive it's on you can always use gparted as this lists all the drive and partitions even if they're not mounted:

sudo apt-get install gparted

---

### Post by Najand on 2007-04-08
> **YSH said:**
> I have this script, diskmounter, which would mount my other partition, the C-disk, on which all the old windows-documents are, but when that script asks for my passwords i can't type my password, i also tryed the next line, but than he said it was false.

Well... Maybe some oarts of your script is removed or it is not working good. Better to copy/paste it again and try again. It is at [http://media.ubuntu-nl.org/scripts/diskmounter]("http://media.ubuntu-nl.org/scripts/diskmounter")

---

