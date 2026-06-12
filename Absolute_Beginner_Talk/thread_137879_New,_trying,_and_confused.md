---
title: "New, trying, and confused"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by mroark on 2006-02-28
I have been reading these forums and it is womderful how you help others out!  I am totally new to Ubuntu/Linux.  I've wanted to try Linux for years and I finally got this copy of Ubuntu.  I have installed the "Installation Disk" and my machine is very very slow.  It is on a P3 500Mhz, 64Mb RAM, with intergrated graphics.  From what I have read 64 Mb RAM is too little of resource for 5.10.  One reference suggested 5.04 or "small Linux"?  Also, I need to know what Blackbox, Window Maker, or IceWM?  Would something of this nature revive this obsolete pc?  One more, would installing the Live CD allow my pc to perform better rather than using the install disk?:confused:

---

### Post by taurus on 2006-02-28
With 64MB of RAM, it's not a good idea to run Gnome which is a desktop manager.  So, boot your machine with the CD and at the prompt, type "server" (without the " ").  Just follow the instructions on screen and when it's all done, log in with the name and password that you have created during the installing process.  Then, at the prompt, install Xfce4 which is a light window manager (and so are windowmaker, fluxbox/blackbox, icemw, enlightenment, etc.)

```

sudo apt-get update
sudo apt-get install xubuntu-desktop

```

---

### Post by mroark on 2006-02-28
Taurus thanks so much!  I assumed ( I not we should not).  I really want to understand the language and become proficient with Linux.  Again, thanks... I'll give it a try and let you know how I do!:-D

---

### Post by ekarni on 2006-02-28
5.04 is the old April 2005 release of Ubuntu; I don't think using it would help any over the current 5.10 version.  

"small linux" probably refers to the "Damn Small Linux" distribution (yes, it's really called that!).  That's seperate from Ubuntu, but might work better on your machine.  I haven't used it...

The live CD doesn't install anything on your hard disk; everything stays in RAM.  Since you're tight on RAM, using it won't speed things up any.

Yes, Blackbox, Fluxbox, or IceWM should make it possible to run basic tasks like web surfing, e-mail, simple word processing etc. on your machine.  Suggest you search the forums for the appropriate "how-to" on installing them.

---

### Post by Turtle.net on 2006-02-28
Maybe I can just add that this will only work if your old computer is connected to the internet to be able to download xubuntu-desktop packages.
If not you can maybe download the add-on CD created by aysiu (look at [http://ubuntuforums.org/showpost.php?p=775979&postcount=24]("http://ubuntuforums.org/showpost.php?p=775979&postcount=24") ) you will just need bitorrent and a cd-burner (obviously on another computer ;) )

---

### Post by xhie on 2006-02-28
[QUOTE=mroark]One more, would installing the Live CD allow my pc to perform better rather than using the install disk?:confused:[/QUOTE]

The live CD doesnt actually install anyting on your system, it loads ubuntu and lets you play around with it without installing it, mainly its used to "try out" ubuntu, see how well your hardware is suppored, and fix some problems after instalation.

---

### Post by gingermark on 2006-02-28
[Ubuntu Lite](http://ubuntuforums.org/showthread.php?t=98233) is a 3rd party project that uses IceWM. It might be of interest to you.

---

### Post by jal on 2006-03-01
As a matter of interest I just installed 5.04 onto a PIII 450mhz machine with 512Mb ram. 

Runs brilliantly. Sometimes a bit slow for cpu bound tasks (compilling) but no problems at all with KDE.

Can you find/purchase/borrow some more RAM?

---

### Post by mroark on 2006-03-01
Thanks to all of you who have replied.  I will look at these recommedations and see what works the best for me.  This is an old machine that I wanted to learn Linux on beofre migrating from Windows (I am looking forward to that day), I do have internet connection via cable.  I recently built an AMD 3100 w/ 512 Ram and 128 DDR Gforce video and HP DVD burner with Lightscribe.  I know it would push the Ubuntu, but I'm not ready to make that transition.  Again, thank you to all!:-D

---

### Post by yatesDELTA on 2006-03-01
ha!!!!
well topic-maker we are in the same boat. exscept my commputor is a p11 400mhx with 250 RAM. i am having truoble with partitioning htough

---

### Post by Brunellus on 2006-03-01
64MB of RAM is not a lot to work with if you want a full graphical environment.  The limiting factor will be RAM, not processor, for you.  I recommend buying & installing a bit more RAM-- 128 minimum for a very bare ubuntu install using fluxbox as the graphical environment, 256 MB for XFCE (XFCE can and has run on less), and more for full GNOME or KDE.  

DamnSmallLinux ([http://www.damnsmalllinux.org](http://www.damnsmalllinux.org)) may be an option for you, but it's very stripped-down.  I use it, though, as a Linux-in-my-pocket system:  I have DSL Embedded on a USB thumbdrive, and boot it from inside windows.  Quite a cunning trick.

---

### Post by mroark on 2006-03-01
[QUOTE=Brunellus]64MB of RAM is not a lot to work with if you want a full graphical environment.  The limiting factor will be RAM, not processor, for you.  I recommend buying & installing a bit more RAM-- 128 minimum for a very bare ubuntu install using fluxbox as the graphical environment, 256 MB for XFCE (XFCE can and has run on less), and more for full GNOME or KDE.  

DamnSmallLinux ([http://www.damnsmalllinux.org](http://www.damnsmalllinux.org)) may be an option for you, but it's very stripped-down.  I use it, though, as a Linux-in-my-pocket system:  I have DSL Embedded on a USB thumbdrive, and boot it from inside windows.  Quite a cunning trick.[/QUOTE]


Thanks Brunellus... I'm now reading up on flubox.  :D

---

