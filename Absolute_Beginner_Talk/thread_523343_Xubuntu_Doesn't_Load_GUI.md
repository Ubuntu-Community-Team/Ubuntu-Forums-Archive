---
title: "Xubuntu Doesn't Load GUI"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by 0graham0 on 2007-08-11
So I had a near-perfect install o Xubuntu 7.04 using the alternative cd on a Dell Latitude LM machine, except it would not install grub (Detailed here: [http://ubuntuforums.org/showthread.php?t=522474](http://ubuntuforums.org/showthread.php?t=522474)). I finally got it to boot up using super grub disk, but it only brings me to an ubuntu command prompt, and I have no idea how to load the GUI? Any help is greatly appreciated, thanks.

EDIT: I tried startx and it says the program is not installed and that start is not a recognized command

---

### Post by DBStevens on 2007-08-11
If the alternate cd of Xubuntu actually completed the install, startx would exist.

It looks like the install went south well before the grub issue.

I've installed from the alternate cd on two systems a white box and a Dell Dimension 2350.

You will have to discover what didn't install and install it using the cli versions of the package manager.

I would start with the meta packages xorg and xface4  which should install both x, a display manager, and a window manager.

sudo apt-get install xorg xface4

Then a startx just might get you somewhere.

---

### Post by 0graham0 on 2007-08-11
Thanks,

do i need a net connection, or will apt-get use the cdrom as a source?

---

### Post by DBStevens on 2007-08-11
I don't think you need a net connection, I've never been in that position to know for certain.  

Try i t the worst it can do is tell you it has a problem.

---

### Post by Ptero-4 on 2007-08-11
Instead of xorg and xfce4, install xubuntu-desktop, it installs everything off the CD.

---

### Post by aysiu on 2007-08-11
Type these commands into the terminal: ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by 0graham0 on 2007-08-11
i'll try it, thanks

---

### Post by macogw on 2007-08-11
To add the cd rom as a source, type this:
sudo apt-cdrom add

---

### Post by 0graham0 on 2007-08-11
I recieve the message "E: Couldn't find package xubuntu-desktop"

edit: I just saw the message about adding the cdrom entry...I will try that.

---

### Post by 0graham0 on 2007-08-11
Thank you all very much, this worked for me:

```
sudo apt-cdrom add
```

Insert cd-rom and press enter

```
sudo apt-get install xubuntu-desktop
```

p.s. Is it safe to install grub the same way?

---

### Post by 0graham0 on 2007-08-11
Well the install failed, the MD5 of the xfonts didn't match up. I guess with no internet connection on this computer I should try burning the cd again?

---

### Post by DBStevens on 2007-08-11
Did you verify that your original download was actually complete?

Then did you verify you actually burned an image that matched a valid downloaded image?

Those MD5 didn't fail for no reason and they probably are the reason that both  x wasn't installed and that grub wasn't there. 

BTW the two packages I suggested you install would have given you a minimum x system and windows manager without all of the other stuff.

---

### Post by 0graham0 on 2007-08-11
Thanks, I am attempting the xubuntu-desktop install again, its going better this time. I guess I learned the hard way...I'll never run another install without checking hte MD5 from now on ;)

---

