---
title: "minimum requirements"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by sem7ex on 2007-01-20
Hi ppl,

i cant find any official system requirements. I was wondering if  a PIII 450MHz, 128 MB SDRAM and 6GB HDD would do the job for Ubuntu 6.10.
If not, what linux version would you recommend?

---

### Post by halitech on 2007-01-20
that system is a little light for Ubuntu but Xubuntu should work better. I have Ubuntu running on an AMD K6/2-350 with 256 and 8gig drive for a server. Okay for a server but when opening a browser and other apps, it lags a bit.

---

### Post by taurus on 2007-01-20
That will be probably too slow for Ubuntu & Kubuntu.  However your machine should be good or ideal for Xubuntu (XFce4 window manager) or fluxbuntu (Fluxbox window manager).

[http://www.xubuntu.org](http://www.xubuntu.org)
[http://www.fluxbuntu.org](http://www.fluxbuntu.org)

---

### Post by arochester on 2007-01-20
The recommended minimum requirements for Ubuntu are 256Mb of RAM. If you cannot increase the amount - I have found ebay a useful source of memory - look a Xubuntu or even Zenwalk. These are both Xface, rather than Gnome or KDE and have the recommended minimum of 128Mb

---

### Post by mcduck on 2007-01-20
> **arochester said:**
> The recommended minimum requirements for Ubuntu are 256Mb of RAM. If you cannot increase the amount - I have found ebay a useful source of memory - look a Xubuntu or even Zenwalk. These are both Xface, rather than Gnome or KDE and have the recommended minimum of 128Mb

That 256MB is the minimum for running the Desktop CD. Ubuntu itself works just fine with less. Alternate CD only needs 64MB to install Ubuntu..

Actually I'm running Edgy on AMD-K6-2 @ 500MHz with only 120MB of RAM (integrated graphics card takes 8MB). XFCE4 works great and even Gnome is usable. (Notice that K6-2 is even slower than Pentium 2 CPU's)

---

### Post by sem7ex on 2007-01-20
you guys are quick!

i want to use this machine only as a low power consuming router with a torrent client running, not as a regular desktop.

thanks for the replies.

---

### Post by halitech on 2007-01-20
I would still probably go with Xubuntu so it has more resources for the torrent clients

---

### Post by Mike_Longbow on 2007-01-20
I agree.
You should use either Xubuntu (xfce) or Fluxbuntu (fluxbox). I use them both as a regular desktop in a machine with the same specs as yours, since Ubuntu (gnome) is a little slow.
I would recommend fluxbox, it's a lot faster, but requieres some configuration...
Anyway, follow the links provided by taurus.

---

### Post by sem7ex on 2007-01-20
i am switching from windoz and i am a absolute beginner with linux so i need it to be as easy to configure as possible. i need to set up a wireless network and to be able to control it remotely. So, is Xubuntu user friendly enough?

---

### Post by Mike_Longbow on 2007-01-20
> **sem7ex said:**
> i am switching from windoz and i am a absolute beginner with linux so i need it to be as easy to configure as possible. i need to set up a wireless network and to be able to control it remotely. So, is Xubuntu user friendly enough?

mmm....
In that case you can use ubuntu, networking works almost "out of the box" there, and there's no need of too much configuration.
You can also setup a wireless network from xubuntu, but it's a little tricky... not as user-friendly as ubuntu.
As I told you, ubuntu will work a liitle slow with a machine like yours... but I think it's worth it.
Also I recommend using the Alternate Install CD, it gives you some options for low-ram systems installation

---

### Post by mcduck on 2007-01-20
If you install Gnome desktop you can easily make a bit lighter easily:Press Alt-F2 and run 'gconf-editor' to open Configuration Editor.

Then browse to apps/metacity/general and select 'reduced_resources'. This makes Metacity to show window contents when you move windows. 

Next go to apps/panel/global/ and deselect 'enable_animations'. This disables animations when you minimize and maximize windows. The animation is so ugly that it deserves to be disabled anyway.

Finally go to desktop/gnome/interface and deselect 'enable_animations'. This should disable all animations from gnome interface. For example the gnome foot animation in Nautilus browser view stops.

---

### Post by lpmasterblow on 2007-01-20
I was about to ask the same question, I run a pIII 750MHz with 128mb and 20Gb HDD, installed from the alt-cd, no problem, hoping that it should run a little smoother once i get another 128mb of RAM fitted next week. It has been a little difficult to find old RAM, but it's fairly cheap.  Unfortunately the computer can only take 256mb maximum, so I'll never know any better.
What would happen if I put more than that in the machine? would it use the 1st 128 and then ignore the rest or would the entire DIMM not work?

---

### Post by freeqaz on 2007-02-24
You should be able to go up to 2 gigs. Its a 32-bit from what you've said. So my guess is that it would. Try it, if it doesnt work you have some extra ram is you run into another ghetto comp!
Im installing fluxbox on my p2 400MHz W/ 64MBs of ram. I hope it will work.

---

### Post by Mike_Longbow on 2007-02-25
> **freeqaz said:**
> Im installing fluxbox on my p2 400MHz W/ 64MBs of ram. I hope it will work.

It will. I have installed it on a P3 450 Mhz / 64 MB SDRAM. I just recommend to install a server first, and then add all the packages you need, because the default desktop loads a lot of unneeded services.

---

### Post by kerry_s on 2007-02-25
> **Mike_Longbow said:**
> mmm....
In that case you can use ubuntu, networking works almost "out of the box" there, and there's no need of too much configuration.
You can also setup a wireless network from xubuntu, but it's a little tricky... not as user-friendly as ubuntu.
As I told you, ubuntu will work a liitle slow with a machine like yours... but I think it's worth it.
Also I recommend using the Alternate Install CD, it gives you some options for low-ram systems installation


Actually if you use edgy xubuntu, the network setup is the same as gnome.(see pic)

Here's the link to the mini.iso net installer, with this you can install all the *ubuntu desktops or when you get the hang of things you might want to try a server buildup and have a custom system.-> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)

---

