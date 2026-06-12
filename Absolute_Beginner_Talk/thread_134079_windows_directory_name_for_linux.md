---
title: "windows directory name for linux"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by drifter0000 on 2006-02-21
This probly sounds silly to you guys but here goes.  I am really new to linux and I am installing the iso image from a hard drive.  When I get to the installer it asks me for the directory name that has the iso image.
The image is in win98 on c:mydocuments.

Now can anyone please tell me how to phrase this in the linux installer so it can find the iso image file???

---

### Post by Garyu on 2006-02-21
[QUOTE=drifter0000]This probly sounds silly to you guys but here goes.  I am really new to linux and I am installing the iso image from a hard drive.  When I get to the installer it asks me for the directory name that has the iso image.
The image is in win98 on c:mydocuments.

Now can anyone please tell me how to phrase this in the linux installer so it can find the iso image file???[/QUOTE]

Uh, this might be a silly answer, but shouldn't you burn you .iso to a CD and then boot from the CD to install? That's what I did anyways, and it should be a whole lot easier than trying to figure out how to mount the windows drive and access the .iso there...

OR if you don't want to burn a CD, there is a way to install from the Internet without burning or anything. Don't remember where that howto was though, but try this wiki page:
[https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)
Maybe you will get some hints from there. :cool:

---

### Post by drifter0000 on 2006-02-21
I dont have a cd burner but I have all the iso images,  everything is working just fine, but, when I get to the linux installer it asks me for the partition and for the directory of the iso image...everywhere I have looked on the net tells me to just type in the directory name and some say also the name of the iso image file.....however none tell you the linux convention so the installer can find the file on fat32

---

### Post by opticyclic on 2006-02-21
YOu are going to have to point to the correct partition
Something like fd0
(fd stands for Fixed Disc)
Im not sure if it needs to be mounted at this point

It could just be fdo/c/my documents

---

