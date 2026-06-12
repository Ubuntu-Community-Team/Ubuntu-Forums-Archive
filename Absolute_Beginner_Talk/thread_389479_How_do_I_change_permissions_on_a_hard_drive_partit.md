---
title: "How do I change permissions on a hard drive partition?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by toecutter on 2007-03-20
I installed Ubuntu on a 'clean' drive (repartitioned after backing up 37gb of mp3 files)

The partitions on my first physical disc are:
Linux boot
Linux swap
Windows XP
XP games
shared media stuff (hda5)

On hda5 I want to copy all of my media files (mp3's to start with) that I had backed up, but using the GNOME desktop I can't copy in anything because I don't have the right permissions. 

How do modify permissions for my various other partitions? I have another physical hard drive with 3 partitions on it, if I make one an EXT3 partition will I need to modify permissions for that as well?

I'm not fully up to speed on moving around directories and such (I am reading manuals and such online though), much less chmodding for permissions, so I need a bit of help to get things going. 

Thanks as always for any help! :)

---

### Post by steve101101 on 2007-03-20
```
sudo chown -R username /location 
```

will change the ownership. (the "-R" includes all sub folders)

```
 sudo chgrp -R username /location 
```

will change the group (the "-R" includes all sub folders)

---

### Post by steve101101 on 2007-03-20
if you want to just copy use the code ...

```

sudo cp /old_location/ /new_location/

```

If you have any questions just send me a private message

---

### Post by Tony3286 on 2007-10-21
Steve,
 
    You were a life saver ! I'm fairly new to Linux - I had purchased an external Western Digital
hard drive to use for backups. It was formated with Fat 32. I decided to partition it in 1/2 with Gpart leaving 1/2  the drive as Fat 32 and the other I formated to ext3. Thats when I ran into problems.Thanks to your previous post, I was able to get permissions changed from Root to myself. The only problem I have noticed is that when  I mount  that  partition      /media/disk  and view its contents, it will not allow me to create a new folder. If I click on "File" at the top left, the "create folder" is grayed out and can't figure out how to create a new folder in that partition. I have used Simple Backup and , from there, can create a folder for my backups, which does show in   /media/disk,  but from within that partition I'm lost. Any help is greatly appreciated.

Tony

---

### Post by Tony3286 on 2007-10-21
Sorry  - Once I rebooted , all the options appeared

---

### Post by ricjazza on 2007-11-09
[SIZE="5"]Run [COLOR="#ff0000"]gksudo[/COLOR] in Terminal and place to Run Program :[/SIZE]

[SIZE="5"][COLOR="Red"]nautilus --no-desktop --browser[/COLOR][/SIZE]


[SIZE="5"]1[/SIZE] 

 [img]http://prikachi.com/files/47408l.png[/img]

[SIZE="5"]2 [/SIZE]

 [img]http://prikachi.com/files/47409d.png[/img]

[SIZE="5"]3[/SIZE] 

 [img]http://prikachi.com/files/47420s.png[/img]

[SIZE="5"]4[/SIZE] 

 [img]http://prikachi.com/files/47425s.png[/img]

[SIZE="5"]5[/SIZE] 

 [img]http://prikachi.com/files/47427T.png[/img]

---

