---
title: "Mounting &quot;Shared Partitions&quot;"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Stevo0687 on 2007-04-09
Hey all! 
    I've got 6.06LTS running.  Now I've got to start configuring how I want it.  I have a shared partition that I use for XP and Vista and want to also have access to in Ubuntu.  

> **halitech said:**
> 
for your windows stuff, don't worry about mounting that now, when you get into Ubuntu, you can use the disk tool to mount in in your home folder.


I figure I go into DisK Manager under System-> Administration->Disks

Then I went to to the partitions tab.  Beyond that I am not sure what I need to do so that I can use the partition to save and access files.  I'm not even sure how to save files if I wanted to save them on the main partition for Ubuntu only.  Any and all help would be appriciated.  Thanks in advance.

---

### Post by bodhi.zazen on 2007-04-09
Try this : 

[http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

---

### Post by Stevo0687 on 2007-04-09
hmm...well, the partition I have setup is a fat 32 file system because I was told that, that would be the easiest way to do this.  From what it looks like, what you hav posted appears to be for ntfs.  Is that correct?  Maybe that program is so that I can use an ntfs instead of fat 32 which I hear isn't as good.  Or am I wrong and that tool will work for fat 32.

---

### Post by bodhi.zazen on 2007-04-09
> **Stevo0687 said:**
> hmm...well, the partition I have setup is a fat 32 file system because I was told that, that would be the easiest way to do this.  From what it looks like, what you hav posted appears to be for ntfs.  Is that correct?  Maybe that program is so that I can use an ntfs instead of fat 32 which I hear isn't as good.  Or am I wrong and that tool will work for fat 32.

The tool will work for fat32

To mount a fat partition, you need to know the partition. I will assume it is /dev/hda2 ???

```
mkdir /media/fat32
sudo mount /dev/hda2 /media/fat32 -o uid=1000,gid=100,umask=007
```

Of course you can /hange /media/fat32 to /home/user_name/fat32 or what have you.

If you want to mount at boot, add this to fstab:

```
gksudo gedit /etc/fstab
```

Add;> /dev/hda2 /media/fat32 auto users,uid=1000,gid=100,umask=007 0 0

If you want more options, see here : [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

