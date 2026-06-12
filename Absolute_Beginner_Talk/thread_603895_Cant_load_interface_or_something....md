---
title: "Cant load interface or something..."
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Kurenai0h on 2007-11-05
As im trying to install Feisty Fawn, by overwriting Gusty but now is gusty suddenly gone and it dont boot up to it. Well thats not my problem so far, my problem is that when I use the Feisty Fawn CD and get a bitt past the Start/Install Ubuntu page I get up and weird error thing. I took a pic of it with my mobile and it dont cover it all, but I guess if you know what to do you can answer it by the pic.It's something with dont load interface I think. [http://i63.photobucket.com/albums/h127/Alkaw/DSC00246.jpg](http://i63.photobucket.com/albums/h127/Alkaw/DSC00246.jpg) sorry if bad size.

---

### Post by LinuxGuy1234 on 2007-11-05
> **Kurenai0h said:**
> As im trying to install Feisty Fawn, by overwriting Gusty but now is gusty suddenly gone and it dont boot up to it. Well thats not my problem so far, my problem is that when I use the Feisty Fawn CD and get a bitt past the Start/Install Ubuntu page I get up and weird error thing. I took a pic of it with my mobile and it dont cover it all, but I guess if you know what to do you can answer it by the pic.It's something with dont load interface I think. [http://i63.photobucket.com/albums/h127/Alkaw/DSC00246.jpg](http://i63.photobucket.com/albums/h127/Alkaw/DSC00246.jpg) sorry if bad size.

I assume that you use the other CD (the Debian Sarge type installer). Try Yes. If it doesn't work choose No and type this after rebooting (don't include you@feisty:$)
you@feisty:$ sudo dpkg-reconfigure xserver-xorg
Try startx:
you@feisty:$ startx
If you get an error try:
you@feisty:$ sudo apt-get install ubuntu-desktop

If you still have this problem, file an bug in xserver-org or debian-installer.

If you use the Desktop CD, you are out of luck.

---

### Post by Kurenai0h on 2007-11-06
I am using the Desktop cd downloaded from here. [http://linux.softpedia.com/progDownload/Ubuntu-Feisty-Fawn-Download-20757.html](http://linux.softpedia.com/progDownload/Ubuntu-Feisty-Fawn-Download-20757.html) the i386 
Ill try what you said when I get back.

---

### Post by Kurenai0h on 2007-11-06
Nothing of it worked...

---

### Post by LinuxGuy1234 on 2007-11-08
> **Kurenai0h said:**
> Nothing of it worked...

Try the other CD (it's installer only):
[http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i368.iso]("http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i368.iso")

It should work.

---

