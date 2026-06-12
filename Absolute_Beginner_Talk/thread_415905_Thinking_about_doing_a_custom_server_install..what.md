---
title: "Thinking about doing a custom server install..what do I need to know??"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by zazen666 on 2007-04-20
Hi all,
I am thinking about taking this oppertunity to do a custom install using the server cd as the begining, and just installing the programs that I want later using synaptic. I have read a bit on the forum but am looking for a clear guide or how to.

Can anyone walk me thru the steps to get it set up?

Oh, and I would like to use the xfce destop environment.

Thank you in advance.

---

### Post by aysiu on 2007-04-20
Here's a clear guide:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by zazen666 on 2007-04-20
Hey thanks
I notice you answer a lot of my newbie questions-its much appericated!!

---

### Post by zazen666 on 2007-04-20
About this part of the instructions:

Getting a usable home desktop
Be careful to type these exact commands (pick the appropriate set of commands for the version you're installing). Spaces are important, as is case (upper or lower).

If you're using Feisty Fawn (7.04) or Edgy Eft (6.10):
sudo apt-get update

sudo apt-get install xorg xterm gdm icewm menu firefox gksu synaptic

sudo dpkg-reconfigure xserver-xorg

sudo /etc/init.d/gdm start

I want to use OPERA instead of firefox, and the xfce desktop.
so do I simply do the following?

sudo apt-get install xorg xterm gdm xfce menu opera gksu synaptic

sudo dpkg-reconfigure xserver-xorg

sudo /etc/init.d/gdm start


Thank you

---

### Post by aysiu on 2007-04-20
Well... sort of.

Opera isn't in the standard set of repositories, and I think Xfce is called *xfce4*.

So you'd do ```
sudo apt-get install xorg xterm gdm xfce4 menu gksu synaptic
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
``` Once you got up and running, you could add Opera later by downloading and double-clicking the .deb from the Opera website.

---

### Post by kerry_s on 2007-04-20
Keep it simple.

server install
login
sudo su
apt-get install xorg gdm synaptic (your wm or de)
reboot
select your session and login

Just install enough to get you to the desktop and do the rest from there, now you can just open synaptic and pick what ever you want.

example, i use fluxbox:
apt-get install xorg gdm synaptic fluxbox
then i reboot, select fluxbox in session and login, open synaptic and pick what i want. 
I take my time picking what i want installed, i normally get my browser first so i can look around the web for alternatives.

---

### Post by zazen666 on 2007-04-20
Thanks guys,
Final question:
I have a sony vaio laptop with 
528 ram, 40 gigs space, and I think 1 gig of pentinum 3.
Now I am happly using xubuntu 7.04 (after some hiccups durning install).

By doing a server install, I know I will get the benefit of less bloat and custom picking my programs, which is very appealing.

But do you think I can expect a resonable increase in speed of performace with my system vs xubuntu?

thanks again
-

---

### Post by kerry_s on 2007-04-21
It really depends on what applications you choose. You want to get things that don't depend on the environment., that don't depend on desktop things from gnome or kde, even xfce4. the more independent the better. You don't want bloated applications.

For example:

filemanger= rox-filer, pcmanfm, emelfm, worker, mc, etc...
editor= leafpad, geany, nedit
etc...

Just do a little looking around and see what light applications are out there.

---

### Post by jpatton on 2007-04-21
> **aysiu said:**
> Here's a clear guide:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

That is very nice indeed, but I'm unable to follow those instructions. I would like to do a minimal install on a dual pentium pro, with 256mb ram, 1 10gb for ubuntu, and then setup a raid across 3 20gb drives. would like this box to be a file server, the problem is its a very old micron board, it won't boot from cd, or usb, for whatever reason i can't get any of my scsi cards to allow me to boot from a scsi cd.

in one of these threads i found a guide to install from ubuntu 5.something, is there a way to do a floppy boot that will load up nic and allow me to complete the install over the internet? bandwidth is no problem, i have redundant t3 connections at work :-p

---

### Post by kerry_s on 2007-04-21
Here are the net installers, not sure which 1 you need-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/)

---

### Post by jpatton on 2007-04-22
> **kerry_s said:**
> Here are the net installers, not sure which 1 you need-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/)

thanks i believe i have seen these before, i need to be able to start install from floppies, there was a posting somewhere in the forums, but it was two versions back at least. as i think about it, i had to upgrade to 6.06 before i could go to 6.10 or something like that.

i would like to be able to start from scratch using a floppy to connect and run the install for fiesty, does anyone know if that is possible?

i'm kinda tired so this may not come out right, but could you get one of the tiny distros on a floppy and then run a net install from there? or mount the mini.iso? is that even possible?

---

### Post by kerry_s on 2007-04-22
Try this-> [http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

---

### Post by jpatton on 2007-04-22
> **kerry_s said:**
> Here are the net installers, not sure which 1 you need-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/)

OMG! that is the coolest utility i've seen in a while! thanks

i'm really tired, i quoted the wrong post..lol..i meant to quote the one about the smart boot manager, thanks again!

---

