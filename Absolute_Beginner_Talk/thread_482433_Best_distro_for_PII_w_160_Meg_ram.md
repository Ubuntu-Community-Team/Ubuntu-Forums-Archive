---
title: "Best distro for PII w/ 160 Meg ram"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by MartyNg on 2007-06-23
This may be a little off-topic, but you guys have been very knowledgeable and have answered many Ubuntu questions for me, so I figure you might have some suggestions.

I have stumbled across an old laptop I thought a friend might be able to use. She has a desktop PC, and doesn't want to buy a laptop, but would like to have a basic one she could use in her backyard as a word processor. Any suggestions on a distribution for a Pentium II w/160 meg ram, and a whopping 4 GIG hard drive? (Although I'm new to *buntu, I get the impression that this old hardware might be better suited to a quicker version of Linux.)

Abiword would probably work for her. Good hardware detection is needed. She needs to be able to save files to a USB flash drive to transfer to her desktop PC. Also, it would be nice to be able to install new programs easily. How about PuppyLinux?

Thank you very much for any advice!

---

### Post by Kobalt on 2007-06-23
You can start off with [Xubuntu]("http://xubuntu.org") (it ships with Abiword by the way). If it's still a bit slow, you may try using OpenBox after that maybe..

---

### Post by ugm6hr on 2007-06-23
PuppyLinux is a good choice for simple usage on that hardware.  (X)ubuntu makes adding extra packages easier (from Ubuntu repo), but if AbiWord is all that is required - then there should be no problem with Puppy.  

Be aware that you auto-login as root with Puppy - so it is relatively easy to make a mess of things if you don't know what you're doing.  

Also - USB flash drives work fine, but they do not auto-mount in Puppy (although there is an easy desktop mounting / unmounting GUI).

I'd suggest she try Puppy from the LiveCD (which will run from RAM - so will be pretty fast - especially if you create a swap partition) to see if it suits her.  If so - it's pretty easy to install.  

Otherwise a light Ubuntu install would be an option.  See [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Nythain on 2007-06-23
i would download the ubuntu alternate insall iso... install a Command Line System... then from there install xorg, xdm, and fluxbox... thats a pretty minimal system, should run great.

basically anything that doesnt run kde or gnome... xfce should run great, can look into xubuntu, fluxbox will run awesome, can look into fluxbuntu (though i prefer a clean install from a command line system, and build from there... i use a lot of terminal apps and try to rely as little as possible on gtk and qt apps)

---

### Post by jrusso2 on 2007-06-23
I would run xubuntu or sam linux.

---

### Post by kerry_s on 2007-06-23
i would go custom, just install exactly what you need.

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

grab the mini.iso or alternate cd
do the server install
login
sudo su
apt-get install xorg gdm synaptic fluxbox
reboot(ctrl+alt+delete)
select fluxbox in the session menu and login
open synaptic and install just what you need.

you can improve performance by using small apps that don't depend on a desktop environment.

---

### Post by louieb on 2007-06-23
> **ugm6hr said:**
> PuppyLinux is a good choice for simple usage on that hardware.  (X)ubuntu makes adding extra packages easier (from Ubuntu repo),  

Puppy would probably be a bit faster. But I echo ugm6hr:  I haven't found an easier distro that Ubuntu to add software to. BTW: xUbuntu will fit on a 4 gig drive I've done it. If you go with Puppy try the Community Edition I really like the way the desktop looks.

---

### Post by MartyNg on 2007-06-24
Thanks for all the suggestions! I will ponder and try these as time allows. Right now, I'm evaluating PuppyLinux.

---

### Post by mattg89 on 2007-06-24
You could do a debian install, and then add the window manager of your choice (on that system probably Fluxbox, or XFCE at a pinch). Any server variety of linux would work, pick your favourite, though one's that are designed to go on a small system, such as Puppy, would probably be a bit snappier.

---

