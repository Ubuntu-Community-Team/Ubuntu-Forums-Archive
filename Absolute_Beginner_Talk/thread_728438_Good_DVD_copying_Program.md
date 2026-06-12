---
title: "Good DVD copying Program"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by articwolf939 on 2008-03-18
can someone plz give me one and a tutorial or how to about it i need it to copy copy-righted DVD plz

---

### Post by fenian on 2008-03-18
I recommend k9copy to install open a terminal and enter...

> sudo apt-get install k9copy

a guide to use it can be found [here.]("http://www.dvd-guides.com/content/view/213/59/")

---

### Post by Hospadar on 2008-03-18
If you are just copying the dvd to a backup disk, you don't need any special program do it, you can just burn all the files on the disk to another disk.  The easiest way to do this is with a program like k9copy, also I think in gnome you can just right click the disk on the desktop and choose "copy disk".  If you only have one cd drive, you'll need to either: write a disk image (.iso) file to your hard drive, and then burn that to a disk, or just copy all the files on the disk to your hard drive, and then burn them to a disk.

If you want to rip the disk to your hard drive so it doesn't take up so much space, you'll need to first install libdvdcss2 from medibuntu so your machine can decrypt the content.  Then you can use any dvd ripping program to rip the video(s).  k9copy does this well, another good choice is dvd::rip, which are both available in Add/Remove programs or Synaptic

Furthermore, if you are trying to back up stuff, you may want to shrink down the videos and re-author a new dvd.  For this, you will probably first want to rip the videos, then use ffmpeg, mencoder, avidemux, or qdvdauthor to re-encode the videos, and then use something like qdvdauthor to re-create a new dvd (qdvdauthor lets you make menus, etc, it also functions as a simple frontend for various command-line transcoders)

---

