---
title: "Problems with accessing external HDD &amp; playing video files"
date: 2008-10-05
forum: Arch and derivatives
---

### Post by Dani Filth on 2008-10-05
Hello folks,

I'm quite new to Arch (I've been using Arch for about more than one month, but I tried various distros before, so I'm not a total newbie to Linux at all). I have some problems with Arch and I hope some experienced Arch users will help me to solve :

(I posted this same thread in Arch forum for 2 days, but I haven't got any answer, since ubuntuforums is very active, I hope some people here will help me through this)

1. I have problem to view the content of my external HDDs, before I add my username to the group "storage", I couldn't even view the content of the HDDs unless I tried "su" or login as root. After I added my username to the group "storage", now I can view the content of the HDD but I still can't copy nor modify anything. If I want to change anything with the HDD, I need to login as root. As for copying, I have to login as root, copy the files to /home/username/Desktop/The_Destination_Folder, but then I still couldn't do anything with the files unless I login as root again, change the permission to "Read & Write" for my username.

2. Video playing doesn't seem very "smooth" to me (sorry, I can't find any better words-English is not my mother tongue), I can't play .avi, .wmv with MPlayer but I can play .avi with Xine & VLC. However, .wmv files are played as if there are scratches on the surface of the disk, the sound is bad even though I tried VLC which has its own codecs.

These are my two main problems now, so far, Arch seems ok for me, just only these two need to be solved.
Any help is appreciated 

Cheers

---

### Post by handy on 2008-10-05
[B][I][U][chgrp]("http://www.ss64.com/bash/chgrp.html")
[chmod]("http://www.ss64.com/bash/chmod.html")
[chown]("http://www.ss64.com/bash/chown.html")
[chroot]("http://www.ss64.com/bash/chroot.html")[/U][/I][/B]

Best I can do sorry.

Are you using ATi or nVidia proprietary drivers for your GPU?

---

### Post by Louis de Broglie on 2008-10-05
Have you installed "codecs" ? :)

> 
pacman -S codecs


---

### Post by Dani Filth on 2008-10-06
I followed the instruction in the Archwiki (Beginners' Guide) so I guess my driver is for ATI as I installed the xf86-ati-something (can't recall the exact name, sorry).

I did install "codecs" package.
A guy in the Arch forum suggests me to install
> pacman -S codecs gstreamer0.10-ugly-plugins gstreamer0.10-bad-plugins gstreamer0.10-ffmpeg

Now I'm able to play avi files with MPlayer, but wmv files are still unable to play.

Cheers for your helps

---

