---
title: "distro for ibook g3"
date: 2012-01-25
forum: Apple Hardware Users
---

### Post by rcbfour on 2012-01-25
I know this is an ubuntu forum, but I was wondering what the best distro is for my 2003 ibook g3, 14.1 inch, mac osx 10.2.8 (although that is probably irrelevent), with 640 mb ram, 900 mhz processor ppc, 30 or 40 gb hardrive with 18 gb left. I know that debian supports ppc still, but I want it to look really pretty, not super bland (this can be changed with gnome, right?). I also really need a distro that won't require a lot of terminal work, although I'm willing to learn, if necessary. I want it to be easy to use, and just work. If possible, it would also be nice if I could use my wireless lan adapter with minimal labor on my part. Thanks!

---

### Post by rcbfour on 2012-01-25
ps: the lan adapter is an airlink 101 AWWLL6075.

---

### Post by rsavage on 2012-01-26
These sorts of questions are impossible to answer. Since we are on an Ubuntu forum, I'm obviously going to advise you to install Ubuntu or one of its derivatives Lubuntu, Xubuntu etc. I don't have any experience with Gentoo (although they have good documentation), Archlinux, Crux or Fedora so can't give a considered opinion. Debian PPC and the spin off MintPPC have very little or dated documentation and (in all honesty) for that reason I cannot recommend them to somebody new unless you want to spend a long time searching forums (EDIT: although much of the Ubuntu documenatation obviously applies to them).
 
The PowerPC Ubuntu downloads are here [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads) and the documenation is here [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) . I like Xubuntu, it is good to look at and lightweight. Probably a good fit for your ibook. No idea about your wireless adapter, but the newer releases probably have the best chance of working. Don't worry about using the terminal, the installation process is well tested and documented.

---

### Post by Lars Noodén on 2012-01-26
I'd give Lubuntu a try, it's the lightest.  No need to spend scare system resources on just the desktop.  Otherwise, you can go with plain Debian and just add in the pieces you need.  Some would even suggest skipping the Desktop Environment completely and using just a window manager.

---

### Post by rsavage on 2012-01-26
Yep, you see everyone has their favourites and a different answer!  The best thing is to install a few and try them out!

---

### Post by rcbfour on 2012-01-26
When I said a "pretty" version of debian, I was actually thinking of fedora. Would that work with my ibook and lan adapter?

---

### Post by rcbfour on 2012-01-26
Even thorugh I do want fedora, I think im going to go with linux mintppc

---

### Post by svtguy88 on 2012-01-27
I'd give Lubuntu a try.  I fooled with Debian and Mint on my G4 tower for a while, before replacing the system.  It will likely return one day with Lubuntu/Mythbuntu as a HTPC.

Anyway, the reason I recommend Lubuntu is because I had the best luck with it out of the box.  It booted right away (no fooling with X) and performed decently.  Your results may vary, but I also tried it on a Powerbook G4 I have laying around, and it was very usable.

---

### Post by rcbfour on 2012-01-27
Indecision! I am testing out kubuntu from cd, but it looks pretty grim. a bunch of I/0 errors and squachfs errors. How do you install Lubuntu? does it have to run on top of something? I am a noob at linux, and have no idea what the heck is going on. HELP!

---

### Post by Khayyam on 2012-01-27
rcbfour ..

The Airlink 101 is wireless adaptor (wlan), or a lan (ethernet) adaptor? I know Airlink make both and so it might be worth claifying ITR. An Airlink 101 wireless card may work with some fiddling, but possibly not out of the box (ie: when booting from an install CD), as [this post]("http://www.linuxquestions.org/questions/linux-hardware-18/airlink-101-usb-wireless-on-ubuntu-9-10-a-785127/") suggests.

If your internal ethernet (Sun GEM) still works (I know, from experience, the iBook G4's have a nasty design flaw where the ethernet socket snaps away from the motherboard) I'd suggest using it for the install. The Airport (bcm43xx) will work but you need to create a firmware driver before the bcm43xx driver will operate, and the tool to do this (bcm43xx-fwcutter) doesn't come on most (any?) install disks.

Having maintaned two iBook G4's on which the ethernet port had broken off the mainboard I can report that the [usbnet]("http://www.linux-usb.org/usbnet/") driver worked for various (noname) USB ethernet addaptors, but I may have just been lucky.    

As for distribution recommendations: from your stated wants I would say Ubuntu of some flavour would probably suit. If your new to Linux and migrating from MacOS X then Ubuntu (Lubuntu, or what-have-you) shouldn't be too steep an incline. That said (and not wanting to start any distro-war) I have run/installed [Gentoo]("http://www.gentoo.org") on numerious PPC's and can recommend it highly .. with some proviso's. The primary provisio, at least with your 'wants' in mind, is that it has a steeper learning curve. As has been mentioned, its well documented (and supported), but if you don't want to be bothered with the specifics of how an OS is put together, or want simply to direct an installer at a given hardrive, then its probably not for you.

However, it does have its upside.

I own a G3 Powerbook (Lombard) 300Mhz 1GB RAM. I installed Gentoo on it in 2001, it has been used everyday (work days, 8hrs+ per day, as its the machine I use for work), all software is currently up-to-date, and I've had little or no problems in keeping it so. Every aspect of the hardware works, and other than a replacement HD, and than a slight 'redishness' that occurs when the screen is un-dimmed (which soon disapears), the machines and OS are in tip-top condition. Considering the additonal time spent when first installing, which wasn't anything major, but certainly more than would be required with a binary based install, I'd say that effort has been recouped.

Anyhow, distributions are often a matter of meeting ones initial requirements, and again, I would say Ubuntu should do that in your case. There are certainly more to choose from these days, when I first started using Linux on PPC there was only one possible choice .. LinuxPPC.

---

### Post by johnduran on 2012-01-27
I don't know if you still want this answer but I've tried the few options that are still available there for my Clamshell G3, 366mhz, 576 RAM, 40 GB HD and, definitely, it works fine with **ubuntu 10.10** although I haven't managed to make Airport work (I'm a real novice with Linux). 
 
You can install ubuntu 10.10 using the ISO CD without problems, instructions are very clear to follow (use the **alternative** version ISO). Once installed, it is very custumizable (the true reason why I prefer it to Tiger), I can't configure Airport yet but with a wired connection works fine (with 9.10 Airport it used to work). Pidgin, Mozilla, OpenOffice, GIMP, and some other programs work slowly but steadily considering that it is a +10 year-old computer.
 
I've tried **Debian Lenny** which worked fine but with no sound, **MintPPC 9 **(a good option and it can still configure Airport), **Xubuntu** (to be honest I've found not much difference in performance compared to ubuntu) but works fine too (but again, no Airport), **Kubuntu** is heavy but it did run. 
 
I chose ubuntu 10.10 and I'm happy with this distro because it lets me take advantage of my old but pretty laptop.

---

### Post by Lars Noodén on 2012-01-28
> **rcbfour said:**
> Even thorugh I do want fedora, I think im going to go with linux mintppc

Did you get Linux Mintppc running?  I tried to but the CD images were unavailable for some days and then when I got them they gave kernel panics.

> **rcbfour said:**
> Indecision! I am testing out kubuntu from cd, but it looks pretty grim. a bunch of I/0 errors and squachfs errors. How do you install Lubuntu? does it have to run on top of something? I am a noob at linux, and have no idea what the heck is going on. HELP!

Kubuntu (KDE4) is a bit heavy for older processors now.  Better to use LXDE which is part of Lubuntu or even just a plain window manager like Openbox, Fluxbox or FVWM-Crystal.  You can find the Lubuntu CD here:

[http://cdimage.ubuntu.com/lubuntu/daily/current/](http://cdimage.ubuntu.com/lubuntu/daily/current/)

---

### Post by svtguy88 on 2012-01-28
Agreed.  LXDE makes a huge difference versus the heavyweight window managers.

---

### Post by rcbfour on 2012-01-28
wlan

---

### Post by rsavage on 2012-01-30
> **johnduran said:**
> although I haven't managed to make Airport work (I'm a real novice with Linux). 
 
Have you had a look at the PowerPC FAQ?

---

