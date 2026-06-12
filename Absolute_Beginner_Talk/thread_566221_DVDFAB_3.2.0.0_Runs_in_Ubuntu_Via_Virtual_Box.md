---
title: "DVDFAB 3.2.0.0 Runs in Ubuntu Via Virtual Box"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-10-03
This is the only version i have managed to get working so far. 

YEE-HAWW!!!!

I have got DVDFAB up and running using version 3.2.0.0

After you install Ubuntu install Virtual Box.
Also make sure you install the Virtual guest package and share a directory between Linux/Virtual box.
Next install your copy of XP Pro you got rid of to install Ubuntu.
Fireup XP Pro via Virtual box (install virtual box via [Automatix]("http://www.getautomatix.com/wiki/index.php?title=Installation") 2)
Install[ VLC Media player inside XP pro]("http://www.videolan.org/vlc/download-windows.html") (to test your final output)
Also install [IMGBURN]("http://www.imgburn.com/") freeware (need this to make an ISO of the DVD you want to copy or DVDFAB will crash and burn)
Now install[ DVDFAB 3.2.0.0]("http://www.dvdidle.com/")

You will need to setup Virtual box so it can also you the DVDROM drive in your pc.This is done via the settings of Virtual box.

Also make sure you enable the sound card in your machine via virtial box settings so you can use the sound card in XP Pro.

While inside XP Pro, startup IMGBURN. Make an iso image of the disc you want to copy.
You must make an iso first,if you dont DVDFAB will crash.Every version of DVDFAB i have tried will crash unless you make an iso.
After you have made your iso file, startup DVDFAB and tell it to read the iso file and output it to a temp directory.
Let dvdfab run and in no time it will create a new directory with all the vob files in it.
Test the vob files work by running VLC media player on them inside windows. 


You can now copy these files to a swap directory between Linux/XP if you have installed the Virtual guest package.

Now burn the vob files to dvd via K3B or Nero or whatever

Easy Peasy.

Enjoy!
:guitar:

---

### Post by ryanVickers on 2007-10-06
Your title implies that this works in ubuntu running as a guest OS in VirtualBox!  You should say something like "Runs in Windows VM" ;)

---

### Post by wild77 on 2007-10-27
The latest beta 4.0.0.0 of DVDFab also runs on Ubuntu Gutsy 7.10 using Wine

Here are some screen shots
[http://my.afterdawn.com/wolfmanz/show_image.cfm/15098/full](http://my.afterdawn.com/wolfmanz/show_image.cfm/15098/full)

[http://my.afterdawn.com/wolfmanz/show_image.cfm/15076/full](http://my.afterdawn.com/wolfmanz/show_image.cfm/15076/full)

---

### Post by stinger30au on 2007-10-29
> **wild77 said:**
> The latest beta 4.0.0.0 of DVDFab also runs on Ubuntu Gutsy 7.10 using Wine




SSSSWWWWEEEEEEEETTTT!!!!!!!

---

### Post by stinger30au on 2007-11-10
anyone know what version of wine they are using to make it work in Ubuntu 7.10?

---

