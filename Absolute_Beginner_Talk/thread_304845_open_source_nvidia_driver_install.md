---
title: "open source nvidia driver install"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by CareySchug on 2006-11-22
I have been running dapper drake about 6 weeks.  I am new to linux, but have general unix experiance (Solaris) and mainframes.

I have a low end machine with a sis video on the MB.  Somebody gave me an nvidia AGP board, so I plugged it in.  It works fine booting UBUNTU from the CDROM.  But my intalled system fails to initialize X, dropping me into line mode.

From what I have been able t find, I think there is an open source driver called "nv" built into the cdrom for ubuntu, and proprietary drivers from nvidia.  The built-in driver doesn't do 3-d and maybe other acceleration functions, though I presume even the nv driver will help by getting the video out of main memory.

For now, I think I would be happy with the generic driver, as the only 3-d graphics i use is in screen savers and I don't play 3-d games.  

Can I "install" the nv driver from the line mode I get when x fails to initialize?  Or do I have to remove the card, install some driver(s) and put the card back in?  I don't want to take a risk that I'll have the wrong driver and can't boot anything at all.

---

### Post by gareththegeek on 2006-11-22
First you should backup your existing xorg.conf file to make sure its safe:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Now you need to generate a new xorg.conf file:

```
sudo dpkg-reconfigure xserver-xorg
```

You can just accept the defaults for most of it.  Afterwards try to start up x server

```
xstart
```

If this doesn't work you could try editing the xorg.conf manually:

```
sudo pico /etc/X11/xorg.conf
```

Find the line:
Driver		"somedrivernamehere"

and change it to read

Driver		"nvidia"

Press Ctrl+X and then y to save the changes and quit pico editor.

HTH
G!

---

### Post by Rumor on 2006-11-22
You can install the packages you need from the command line. 

```
sudo apt-cache seach glx
sudo apt-cache seach nvidia
``` will show you what packages are available within the repositories in your /etc/apt/sources.list file. You can then "sudo apt-get install packagename" and follow Gareth's instructions to reconfigure xorg.

---

### Post by CatKiller on 2006-11-22
> **CareySchug said:**
> For now, I think I would be happy with the generic driver, as the only 3-d graphics i use is in screen savers and I don't play 3-d games.  

Can I "install" the nv driver from the line mode I get when x fails to initialize?  Or do I have to remove the card, install some driver(s) and put the card back in?  I don't want to take a risk that I'll have the wrong driver and can't boot anything at all.

Well, if X doesn't start, you can **Ctrl-Alt-F2** to get to a virtual console to fix it, anyway.

Log in, make the backup as gareththegeek suggests, but change the Driver line to **"nv"**. **nvidia** is the closed-source one that you haven't got installed yet. The **nv** driver should already be installed.

---

### Post by CareySchug on 2006-11-22
Thanks all who helped.

If anybody else reads this seeking help, please note that X11 is a capital letter x.  I had to cd into /etc and do a "ls" to figure out why I was getting "not found".

I could not get xstart to work, nor could I find the xstart command.  So I just did an "init 6".

Anyway, after doing the changes, it still didn't work, maybe because I didn't take the default modes, fearing it would try some 1600 x something mode that would be too dense. This is a hindsight guess after getting it to work and doing a "diff", on the output of dpkg-reconfigure and the xorg.conf created by booting the CDROM directly.

Not knowing (at the time) why it didn't work, I booted the CD and while running off the CD, I mounted my original system (altering slightly for my configuration and habits)

sudo mkdir /media/hda1
sudo mount /dev/hda1 /media/hda1
sudo cp -p /etc/X11/xorg.conf /media/hda1/etc/X11/xorg.conf.new

Back to my installed system, and I copied the xorg.conf.new to xorg.conf, and my system came up.  Note: I had previously done the dpkg-reconfigure step, so perhaps that copied or renamed other files and maybe is still a necessary step.

(I like the reel to reel tape recorder image...)

---

### Post by qpieus on 2006-11-22
I think it's startx not xstart.

---

