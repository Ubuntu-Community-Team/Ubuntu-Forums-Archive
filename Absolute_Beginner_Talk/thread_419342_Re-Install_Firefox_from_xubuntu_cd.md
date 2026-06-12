---
title: "Re-Install Firefox from xubuntu cd?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by whitetrashprincess on 2007-04-22
Can I do this?  I have tried everything y'all suggested (plus looked around the net for a few more ideas) to repair my missing firefox and it appears that I must've really killed it, so I have decided to just start over.  

Ideally, I would like to just find out how to get the Firefox stuff to load from the Alternate version of the Xubuntu 6.10 cd that  I already have burned.  If that is not possible I figure I should just reinstall xubuntu from the cd, but I don't know how to do that, either.

Do I have to go back out and reformat my hard drive and stuff?

---

### Post by Ziox on 2007-04-22
Ideally, you don't have to clean your HD.  

Insert your alternative CD

open terminal and enter:

sudo apt-cdrom add

then sudo aptitude update

and either remove then reinstall FF or just sudo aptitude reinstall firefox

---

### Post by whitetrashprincess on 2007-04-22
Ok when I type
sudo apt-cdrom add
it says:

Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in te drive and press enter (I did-the cd icon shows on the desktop)
Mounting  CD-ROM...
E: Failed to mount the cdrom. (which I tried to right-click and told it to mount from the little menu thingy and that didn't help either)

So I tried to do 
sudo aptitude reinstall firefox
and it says:
E: Type '"deb' is not known on line 40 in source list /etc/apt/sources.list (I keep getting this on a lot of stuff I try!)

What have I done to this poor thing?

---

### Post by Ziox on 2007-04-23
what does your sources.list looks like?

cat /etc/apt/sources.list

---

