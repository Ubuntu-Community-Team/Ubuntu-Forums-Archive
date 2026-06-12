---
title: "XLDE vs Xubuntu on a iBook 500 G3"
date: 2009-05-13
forum: Apple Hardware Users
---

### Post by jtbrookreson on 2009-05-13
So i tried installing Xubuntu 9.04 last night, and after 3 attempts (installs) it finally was able to recognize my username and password. But what it wouldn't do is anything after that. Screen just turned a light blue (@ 600x800 resolution mind you). The mouse still worked, but nothing else...

So what I think I might do now is try Debain 5.0 with XLDE instead. so my questions are:
a) is there any reason not to? Does it not play well with PPC?
b) is 256 Ram enough? because that is all I have...
c) does anyone know where I can download Debain 5.0 with XLDE on the same instal disk?

Thanks in advance. I am very much so a Noob trying to feed his inner geek that I just discovered.

---

### Post by urosg3 on 2009-05-14
> **jtbrookreson said:**
> So i tried installing Xubuntu 9.04 last night, and after 3 attempts (installs) it finally was able to recognize my username and password. But what it wouldn't do is anything after that. Screen just turned a light blue (@ 600x800 resolution mind you). The mouse still worked, but nothing else...

So what I think I might do now is try Debain 5.0 with XLDE instead. so my questions are:
a) is there any reason not to? Does it not play well with PPC?
b) is 256 Ram enough? because that is all I have...
c) does anyone know where I can download Debain 5.0 with XLDE on the same instal disk?

Thanks in advance. I am very much so a Noob trying to feed his inner geek that I just discovered.


a. I don`t know, I think its a Ram issue
b. No I think you have various limitation with 256 RAM only
c. You must try net installer from here [http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/powerpc/iso-cd/debian-testing-powerpc-businesscard.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/powerpc/iso-cd/debian-testing-powerpc-businesscard.iso)
and install GUI latter. When that prompt you, install base system only, unset Complete Desktop button, after base installation you are able to install XFCE, Gnome... Gnome works fine with my PowerBook G3 on 400, with 256 RAM

---

### Post by stream303 on 2009-05-14
> **jtbrookreson said:**
> 
So what I think I might do now is try Debain 5.0 with XLDE instead. so my questions are:
a) is there any reason not to? Does it not play well with PPC?

Ubuntu is based on the upstream parent Debian so it plays extremely well, and being familiar with the upstream source helps to refine Ubuntu indirectly.

Note that you may run into the same generic issues that we face with Ubuntu - so stick around and read the threads, wikis, and whatnot for answers to common problems among both distros.

One nice thing to know is that with Debian, you won't be faced with dealing with a known problem with the initial splash-screen - since Debian doesn't have one!  One less problem to worry about out of the gate!

> b) is 256 Ram enough? because that is all I have...

You choice of LXDE should work just fine.  However, that is just the desktop - it all depends on how resource hungry your apps are, so you could have a fast desktop but bog down anyway if you are trying to do video editing or something else huge.  But if you are looking for a general purpose environment, you'll be ok.

> c) does anyone know where I can download Debain 5.0 with XLDE on the same instal disk?

You can get it here:

[http://debian.org/distrib/](http://debian.org/distrib/)

For Lenny, you'll want the "stable" release.  Note that I didn't directly point you to any ftp site - since you may want to use bittorrent or jigdo rather than an ftp or http download.  But those are available too.

You have the choice of downloading a "full" desktop, but you'll find that as soon as you install it, updates are available, so you might be wasting bandwidth downloading updates so soon.

Netinstalls set up a very minimal install, and grab what you want, and the latest updates during install - so you are up to date immediately and conserve download and server bandwidth.  Choice is yours.

Get the "powerpc" port, and note that you only need the 1st cd in a set if you see multiple cd's available.  For LXDE, look for something like this:

**debian-501-powerpc-xfce+lxde-CD-1.iso** 

Nice - you'll get both XFCE AND LXDE and can choose which to install.  If you chose a netinstall, you will be prompted during install if you want gnome, kde, xfce+lxde etc...

There isn't any guarantee you'll get any farther than what you see right now with Ubuntu 9.04 - you could be hitting the exact same problem with having to manually edit your /etc/X11/xorg.conf to take care of the screen issue.

However, with your limited ram, and desire to run LXDE, Debian Lenny 5.0.1 would make a fine choice.  Nice thing is that you can get help from Debian AND Ubuntu ppc users.  We need all the friends we can get! :)

---

### Post by jtbrookreson on 2009-05-15
thanks....

So now I have Lenny going, with LXDE, and I can feel the difference.

EXCEPT.... I stall have the 800X600 resolution problems that I had with Xubuntu 9.04. but I am totally loving the light speed. I just want to use all 1024x768 of my screen....

But HOW? I am an idiot....

thanks.

---

