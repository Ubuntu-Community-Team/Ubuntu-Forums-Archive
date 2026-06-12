---
title: "Accessing Windows files on separate HD?"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by bugmenot on 2006-02-09
I just installed Samba, which is what I was told I needed, but I'm not sure how to get to my windows files on my separate SATA HD from here. There are guides on how to do it from a separate partition, but this is a different HD entirely. 

Can anyone help me out?

---

### Post by Sutekh on 2006-02-09
Dont need samba, need aysiu's great guide

[Mounting Windows Partitions in Ubuntu - by ]("http://www.psychocats.net/linux/mountwindows.php")[aysiu]("http://www.ubuntuforums.org/member.php?u=21941")

Different partition, different disc, it doesn't matter just use the same method.

Use ```
sudo fdisk -l
```to determine your SATA drive, its probably sda, so when mounting, mount the partition sda1

---

### Post by GTvulse on 2006-02-09
[QUOTE=bugmenot]I just installed Samba, which is what I was told I needed, but I'm not sure how to get to my windows files on my separate SATA HD from here. There are guides on how to do it from a separate partition, but this is a different HD entirely. 

Can anyone help me out?[/QUOTE]

That would be because you were given the wrong advice. Snakeoil.

What kind of filesystem has your windows partition in the other hard drive?

---

### Post by bugmenot on 2006-02-09
It's a NTFS. 

I tried: *sudo mount /dev/sda /media/windows/ -t ntfs -o nls=utf8,umask=0222*
but I got: */dev/sda already mounted or /media/windows/ busy*

I just realized I left the "1" off of sda, and it's mounted now. I guess I didn't need to post this thread at all. That was a lot easier than I thougth it'd be. Sorry guys!

---

