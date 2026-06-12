---
title: "Installation Woes"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by JewelledDragon13 on 2007-08-06
I've been pleased with Ubuntu overall.  I love the GUI and have not had much trouble learning console basics.  I'm impressed with the amount of available software, and love that everything is freeware.  (I never realized how much I hated trial software that has half its functions disabled until I switched.)

My big frustration: installing software.  I'm sorry, but it is just more complicated than in Windows.
Yes, sudo apt-get install x is a nice simple command, but when I started, I didn't know that command existed.  (I mean, it isn't written down in big letters anywhere.)  It took a lot of following instructions one by one before I realized this.
Plus, is there somewhere you can access a list of program names that work with that command?  I've had difficulties with this:  for example, I found out I needed libdvdcss, but it took me a while before I realized I couldn't install it because the actual name was libdvdcss2.

Further, there are so many different ways to install.  Command line is the fastest and easiest, but only if you already know what you want.  The add/remove software application is good for searching software and giving me a break from the terminal.  But all too often, I end up having to download tarballs and follow a long series of cryptic instructions that usually don't end up working.

There are so many little things you end up needing to install!  I don't have a good sense of which ones I actually need, which ones I don't need but will want, and which ones are completely superfluous for me, so I just end up installing long lists of programs that might help fix one of the things that randomly won't work right away.

I'm sticking with Ubuntu, but i see this as by far its biggest weakness.

---

### Post by arijarot on 2007-08-06
have you tried using synaptic?

---

### Post by mcurtiss1970 on 2007-08-06
what apps are you having issues with? 

 most if not all the things i want can be downloaded through synaptic and/or [http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by eapache on 2007-08-06
Try System > Admin > Synaptic

It lists all the available packages (by apt-get package name, unlike add/remove) and allows you to install them. It also runs somewhat faster than add/remove.

---

### Post by Ek0nomik on 2007-08-06
To find "missing packages" you can try apt-file:

[http://www.howtoforge.com/apt_file_debian_ubuntu](http://www.howtoforge.com/apt_file_debian_ubuntu)

If I run into that problem I will usually search for the file name using aptitude and leave off the end number.  This way I can just install the newest package.

You can search via the terminal too:

```
sudo aptitude search x
```

---

### Post by por100pre1 on 2007-08-06
If you're looking for some programs to install use Add/Remove... You see in these forums  people posting commands to be used in terminal because it's the fastest way to do the job. It would take hours to guide using the GNOME interface... Actually it's faster than the typical Windows help: "First click Start, then click Control Panel..." :popcorn:

---

