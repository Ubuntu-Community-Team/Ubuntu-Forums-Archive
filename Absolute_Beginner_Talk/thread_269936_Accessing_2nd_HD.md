---
title: "Accessing 2nd HD"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by Dual Cortex on 2006-10-02
Hi, this is the first time that I REALLY try out linux (over 1 day of using it).
Now, I'm a complete beginner when it comes to linux, and I have NO idea how to access my other HD. I went to the media folder and it only had 2 items, CDROM And CDROM. (I only have 1 dvd drive)
I also went to tmp/disks-conf-hda1 which i believe is the HD but when I double click on it the following textbox appears:
"The folder contents could not be displayed"
You do not have the permissions necessary to view the contents of disks-conf-hda1".
I dont even know if that's supposed to be the HD...](*,) 

Hope someone can help, thanks.
;)

---

### Post by aysiu on 2006-10-02
One of these should help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Dual Cortex on 2006-10-02
I don't know if I missed something before but from the FEW posts I've read the drive is supposed to be in the media folder. Mine's in the tmp folder. Do I follow the steps from that web page or am I supposed to mount it in the media folder first?
Thanks for the fast reply.

---

### Post by aysiu on 2006-10-02
It doesn't need to be in any folder. You can mount it wherever you like.

If you mount it to the /media folder (/media/windows, for example), it'll automatically show up on your desktop. I deliberately do not advise people to mount to /media, though, in case they're using FAT32. I've seen too many people have permissions problems when mounting FAT32 to within /media

---

### Post by Dual Cortex on 2006-10-02
Hey, I just tried to follow the steps you gave me. When going to edit the fstab file, I don't see the hard drive I'm trying to mount :|
](*,)

---

### Post by Dual Cortex on 2006-10-02
nvm guys, I got it working. I added the line, then I forgot to make a folder and couldnt mount it where I wanted to, but later noticed. Thanks again, aysiu

---

