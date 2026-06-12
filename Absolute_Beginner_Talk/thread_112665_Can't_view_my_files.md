---
title: "Can't view my files"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by catalytic on 2006-01-04
I just installed Ubuntu yesterday... and I'm lost already.

I thought that you could still read your windows files in Ubuntu?

I know that they are in different formats and I can't write to those files, but why can't I access them?

I have mounted the hard drives, they appear on my desktop, but I don't have access to them. How do I get access? Or have I installed them wrong and have to re install linux?

Thanks....

---

### Post by lreyes6 on 2006-01-04
you have to use de "sudo" or be superuser to access them... for example in my case i do ```
sudo xmms
``` from a console to access my mp3 files on my NTFS partition

---

### Post by catalytic on 2006-01-04
[QUOTE=lreyes6]you have to use de "sudo" or be superuser to access them... for example in my case i do ```
sudo xmms
``` from a console to access my mp3 files on my NTFS partition[/QUOTE]


Ok tried that, but there's nothing there my windows partitions show on my desktop, but I can't view any of the files in them.

---

### Post by lreyes6 on 2006-01-04
try to do this ```
sudo nautilus
``` and then browse them from there

---

### Post by Omnios on 2006-01-04
This is a link to the unofficial Ubuntu users guide dealing with mounting windows partitions. ALso you will not be able to rwite to ntfs from Linux though you can write to fat32. 

[http://ubuntuguide.org/#windows]("http://ubuntuguide.org/#windows")

```
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
/dev/hda1 hd?? is the partition you are trying to mount


```

 Personaly for my vfat32 partition I use in my fstab listing which showed my windows mount in menu places computer
```
/dev/hda2       /media/vfat     vfat    rw,users,gid=users,umask=000,       0       0
 hda2 is my vfat partition /media/vfat is where I have it mounted
```

 ALso this is a good page explainging fstab entries

[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by catalytic on 2006-01-04
[QUOTE=lreyes6]try to do this ```
sudo nautilus
``` and then browse them from there[/QUOTE]

Thanks that worked!! now why couldn't I just see them when I clicked on the desktop icon? I'm obvioulsy too used to windows!

---

### Post by Omnios on 2006-01-04
If you want a desktop windows drive icon check out the mounting from the guide and the example I used above.

 Open menu / Applications / System Tools / Configuration editor

 From within the editor go to  apps / nautilus / desktop , and check off volumes visable this will show your win drive on the desktop if mounted properly

---

