---
title: "Mount FAT32 partition/Mount FAT32 partition on startup"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by dietMKAY on 2006-09-28
Hello everyone! I'm brand new to Ubuntu (n00bie) and I need some assistance from the wonderful Open Source community. My question:

I want to mount my FAT32 partition so that I can read/write to it from Ubuntu and be able to have that partiton mount everytime I start Ubuntu; how do I do this? :confused: 

Eh.....I'm running Ubuntu 6.06 if that helps at all. :-? 

Appreciate the help! Thank you! :-D

---

### Post by newlinux on 2006-09-28
take a look at [http://ubuntuguide.org/wiki/Dapper#Windows]("http://ubuntuguide.org/wiki/Dapper#Windows")

Let us know if you have any questions.

---

### Post by newlinux on 2006-09-28
you'll want to scroll down a bit to see how to mount the partition at bootup... you'll need to know your partition location

look at the output of 

```
df -h
```

---

### Post by dietMKAY on 2006-09-28
```
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

Yes. That's what I did before. Now, how do I have it mount when booted? Or do I have to type in that command everytime I want to use my FAT32 partition--that's the partition where my media files are.

EDIT: Oh, I see the reply now.

---

### Post by newlinux on 2006-09-28
you need to modify your /etc/fstab file
```
gksudo gedit /etc/fstab
```

then put

```
/dev/hda1    /media/windows vfat  iocharset=utf8,umask=000  0    
```

for all user read/write access if it is FAT32.

change vfat to ntfs if it is NTFS, however, you'll need some additional software to write to NTFS from Linux.

you can test it without rebooting. unmount the partition if you already mounted it. To remount everything in /etc/fstab type:

```
sudo mount -a 
```

---

### Post by bodhi.zazen on 2006-09-28
You need to edit /etc/fstab.

```
sudo mkdir /media/music
sudo gedit /etc/fstab
```

Add a line like this:
```
/dev/hdax /media/music vfat auto,users,rw 0 0
```

where /dev/hdax is your fat partition.

/media/music is you mount point.

If you use /media/music you will have a folder on yor desktop.

If yo do not want a folder on your desktop use /mnt/music.

you can of course use any name you like.

You can also create a link, or shortcut, in you home directory:
```
ln -a /mnt/music ~/music
```
For your convenience.

HTH 8-)

---

### Post by newlinux on 2006-09-28
BTW, if you are a complete newbie (and I'm not to far from being one myself) I recommend you scroll to the top of the link I sent and just see what else is there. Hope all is well...

---

### Post by dietMKAY on 2006-09-28
Oh! Thank you all! This is all good information. Tonight I do not have the time to try them out, but tommorow for sure! Thank you!:D

---

