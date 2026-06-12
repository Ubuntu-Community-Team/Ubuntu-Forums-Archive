---
title: "Is FreeBSD overkill for a laptop?"
date: 2008-10-15
forum: BSD
---

### Post by HuBaghdadi on 2008-10-15
Hey,
Do you think that FreeBSD is an over kill OS for laptops?
My friends keep telling me that FreeBSD will cause me headaches, no good support for Bluetooth, WiFi, audio, video ...
(I'm a developer, I use JDK, Python, Apache, PostgreSQL ...)
Thanks.

---

### Post by johnidi on 2008-10-15
are you planning on switching over from ubuntu? If anything why dont you just try the live cd and find out for your self?

---

### Post by HuBaghdadi on 2008-10-15
I don't think FreeBSD 7 has a live CD.

---

### Post by perfecttao on 2008-10-15
Personally I'd install VirtualBox and run FreeBSD (command line only) in that.  FreeBSD is notorious for not being great with various hardware and needing loads of config time....getting bluetooth/wifi etc working well will probably cause you headaches...

---

### Post by Sorivenul on 2008-10-15
I've used FreeBSD on multiple laptops with no problems of sound, resolution, wireless, etc.  It does require more configuration than Ubuntu, but that's something that can be said for almost any system other than Ubuntu.

[Check here for a FreeBSD HCL]("http://www.freebsd.org/releases/7.0R/hardware.html").

---

### Post by HuBaghdadi on 2008-10-15
> **Sorivenul said:**
> I've used FreeBSD on multiple laptops with no problems of sound, resolution, wireless, etc.  It does require more configuration than Ubuntu, but that's something that can be said for almost any system other than Ubuntu.

[Check here for a FreeBSD HCL]("http://www.freebsd.org/releases/7.0R/hardware.html").
It does require more configuration than Ubuntu, but that's something that can be said for almost any system other than Ubuntu.
would you please tell us like what? and how to get help if I'm stuck?

---

### Post by HuBaghdadi on 2008-10-15
> **Sorivenul said:**
> I've used FreeBSD on multiple laptops with no problems of sound, resolution, wireless, etc.  It does require more configuration than Ubuntu, but that's something that can be said for almost any system other than Ubuntu.

[Check here for a FreeBSD HCL]("http://www.freebsd.org/releases/7.0R/hardware.html").
And you are using Ubuntu and FreeBSD, what are the advantages of Ubuntu over FreeBSD 7 (and vice versa)?

---

### Post by Sorivenul on 2008-10-15
I'm still using FreeBSD.  I have Intel chipsets on the laptops I'm using, so nothing too fancy.  To get wireless working, for instance I needed to edit rc.conf and loader.conf to reflect my wireless card.  

There are instructions easily available on bsdforums.org and the FreeBSD mailing lists.  Some specific information about your hardware may help.  And those of us who use FreeBSD and are members here are always willing to help.  

The FreeBSD ports collection offers more applications, libraries, etc. than any user could ever need.  Of course this system requires you compile from source, but it is laid out in any easy-to-use manner (think Gentoo's portage).  Of course, if you don't care about the small benefits gained from compiling from source, binaries are also available for almost all software in the ports collection, and a simple "pkg_add -r <package>" will do the trick. This to me is offering the best of both worlds.

A user can also stay up-to-date with the latest FreeBSD sourcecode using csup/cvsup.  While this is a bit more advanced, the users who wish to stay current and on the "bleeding edge" of FreeBSD take advantage of this system.     

If you're looking to try FreeBSD before you jump in headfirst I suggest DesktopBSD, which comes configured for more hardware compatibility than its parent by default, and comes with KDE desktop environment.  It doesn't teach you as much as building from the ground up, but is a good way to familiarize yourself with how FreeBSD can work should you choose to install from the ground up.

I use many systems other than Ubuntu.  My Ubuntu is a custom build from a minimal install, and I am also testing the Xubuntu Intrepid release.  Advantages will vary from user to user.  For my server needs I choose FreeBSD.  It is also excellent, IMO, as a development platform and most of my applications are written on BSD systems.

---

### Post by HuBaghdadi on 2008-10-16
I noticed many gurus here prefer DesktopBSD to PC-BSD, maybe it is due the PBI system of PC-BSD.
But PC-BSD doesn't stop you from being a BSD guy, you can be a BSD purist.
Please correct me if I'm wrong, but why many gurus here prefer DesktopBSD?

---

### Post by mips on 2008-10-16
> **HuBaghdadi said:**
> 
Please correct me if I'm wrong, but why many gurus here prefer DesktopBSD?

I think it is purely because Desktop BSD stays closer/truer to FreeBSD than PCBSD.

---

### Post by ukripper on 2008-10-16
Try Arch linux if you like things configured your way on your laptop.

---

### Post by Sorivenul on 2008-10-16
DesktopBSD *does* stay closer to FreeBSD than PC-BSD does.  A third installable package-type (PBI) is not needed and causes undue confusion, IMO.

---

### Post by cardinals_fan on 2008-10-16
> **HuBaghdadi said:**
> I noticed many gurus here prefer DesktopBSD to PC-BSD, maybe it is due the PBI system of PC-BSD.
But PC-BSD doesn't stop you from being a BSD guy, you can be a BSD purist.
Please correct me if I'm wrong, but why many gurus here prefer DesktopBSD?
The goal of DesktopBSD is to provide FreeBSD with an easy GUI.  The goal of PC-BSD is to be its own system.  I see nothing worthwhile with the PC-BSD way of doing things (PBIs, etc.), so I recommend that people stick with what's pure.

---

### Post by Niniel on 2008-10-17
Lol, "purity" for "purity's" sake... what an argument.
The PC-BSD makers claim that it's 100 % the same as the "normal" FreeBSD 7 in that all software will run, and that they most certainly do not want to make their own system, but provide a more accessible and easy to install FreeBSD (their words, paraphrased; I don't know the "real" FreeBSD so I can't say if they are correct of if they're lying douchebags).
The reason why "gurus" seem to prefer DesktopBSD may therefore be simply inertia and hostility toward that which is different. And I think DesktopBSD has been around longer, so if you're already running that, why change?
Or PC-BSD may not be stable enough yet (like Ubuntu, some people are having a horrible time, and a lot are having a fairly good one; it works mostly ok for me, except for minor glitches, such as I can't log out, have to shut down or reboot :) The journaling file system is also crap, I already suffered a non-recoverable disk error after a failed shutdown and am now using the default file system, which does recover from improperly dismounted / partitions). 
Or they don't like that it's essentially married to KDE4 (although Gnome can be installed now too via PBI). 
Regarding PBIs, that works well, although the selection of software is still somewhat limited. It is a bit like Windoze - you go to the PBI (repository) site, download the program, and then (double-)click on the downloaded file, which also acts as the installer (think msi-files).
Uninstall is supposed to be easy as well, but I haven't tried that yet.
If you're new to BSD this is a neat system and not confusing at all. If you are used to the traditional method/s then I guess you won't need it. But to my knowledge, nothing prevents you from not using the PBI system to install software. 
As for your original question, I don't think BSD is any more "overkill" than Ubuntu, but it may not have as good a hardware support. 
Only one way to find out. :)

---

### Post by DemonBob on 2008-10-17
I've used FreeBSD on mutiple laptop's without issues. 

First was an HP, then a Dell Latitude, now and Acer 5315, never had a problem.

---

### Post by cammin on 2008-10-17
I've tried Free,Open,Net, and DragonFly bsd's on my laptop.
I'd rate them in about that order as far as usability goes.
Since PC-BSD was mentioned. PC-BSD 6.5 was a better desktop system than Kubuntu 7.10 was. I don't recommend PBI's though.

---

### Post by cammin on 2008-10-17
> **HuBaghdadi said:**
> I noticed many gurus here prefer DesktopBSD to PC-BSD, maybe it is due the PBI system of PC-BSD.
But PC-BSD doesn't stop you from being a BSD guy, you can be a BSD purist.
Please correct me if I'm wrong, but why many gurus here prefer DesktopBSD?

Because the only real difference between the two was that Desktop was a liveCD and PC-BSD had PBI's.
PBI's are pointless and having a LiveCD was a bonus, so Desktop BSD got the nod.

---

### Post by kk0sse54 on 2008-10-21
> **Niniel said:**
> Lol, "purity" for "purity's" sake... what an argument.
The PC-BSD makers claim that it's 100 % the same as the "normal" FreeBSD 7 in that all software will run, and that they most certainly do not want to make their own system, but provide a more accessible and easy to install FreeBSD (their words, paraphrased; I don't know the "real" FreeBSD so I can't say if they are correct of if they're lying douchebags).
The reason why "gurus" seem to prefer DesktopBSD may therefore be simply inertia and hostility toward that which is different. And I think DesktopBSD has been around longer, so if you're already running that, why change?
Or PC-BSD may not be stable enough yet (like Ubuntu, some people are having a horrible time, and a lot are having a fairly good one; it works mostly ok for me, except for minor glitches, such as I can't log out, have to shut down or reboot :) The journaling file system is also crap, I already suffered a non-recoverable disk error after a failed shutdown and am now using the default file system, which does recover from improperly dismounted / partitions). 
Or they don't like that it's essentially married to KDE4 (although Gnome can be installed now too via PBI). 
Regarding PBIs, that works well, although the selection of software is still somewhat limited. It is a bit like Windoze - you go to the PBI (repository) site, download the program, and then (double-)click on the downloaded file, which also acts as the installer (think msi-files).
Uninstall is supposed to be easy as well, but I haven't tried that yet.
If you're new to BSD this is a neat system and not confusing at all. If you are used to the traditional method/s then I guess you won't need it. But to my knowledge, nothing prevents you from not using the PBI system to install software. 
As for your original question, I don't think BSD is any more "overkill" than Ubuntu, but it may not have as good a hardware support. 
Only one way to find out. :)
PC-BSD is not 100% FreeBSD but closely based off it while internally DesktopBSD is in fact exactly FreeBSD with a few gui tools slapped on along with KDE. As for PBI's they work alright but like you mentioned software selection is limited and I don't want to have to go through an exe like installer instead I much prefer ports or pkgsrc. And no I wasn't running DesktopBSD when PC-BSD came out nor do I run either of them now and I don't find myself hostile against PC-BSD but then again I'm not a guru ;)

---

