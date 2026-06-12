---
title: "UBUNTU with VMware player"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by hilfer on 2007-11-19
Hi all:

I started ubuntu 7.10 on a virtual machine called VMware player.
Of course I'm using a pre-mounted ubuntu image.
My question is: May I install  new programs to ubuntu?
I have been trying and everything goes fine, but after download and install I can never find the program !!Am I doing wrong or its not possible ??

hilfer.

---

### Post by hyper_ch on 2007-11-19
How did you install new programs? What programs?

---

### Post by hilfer on 2007-11-19
> **hyper_ch said:**
> How did you install new programs? What programs?

I used the synaptic package manager.

Trying to install Rtorrent

hilfer.

---

### Post by hyper_ch on 2007-11-19
well, rtorrent ist a ncurses (command line) based application. If you want to use it, have a look here (that hooked me up):  [http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

Before that I used KTorrent (which was more designed for KDE but also works fine in Ubuntu). Other torrent clients with a gui would be Deluge, Transmission and Azureus (but Azureus is a real memory hog IMHO).

---

### Post by hilfer on 2007-11-19
> **hyper_ch said:**
> well, rtorrent ist a ncurses (command line) based application. If you want to use it, have a look here (that hooked me up):  [http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

Before that I used KTorrent (which was more designed for KDE but also works fine in Ubuntu). Other torrent clients with a gui would be Deluge, Transmission and Azureus (but Azureus is a real memory hog IMHO).

Tks for yr sugestions will try deluge (used it on windows too)

But I still have another question:

The mounted ubuntu image comes with a diferrent keyboard system (mine is PT-PT) is there any way to change that ??

hilfer.

EDIT : I FOUND IT. TKS.

---

### Post by hyper_ch on 2007-11-19
There is, go to the System settings and change the keyboard layout there.

---

### Post by wrightflyer on 2007-11-19
Sorry for slight thread hijack but this actually had the same title as a thread I was going to start and I have a feeling folks here may know the answer to this (and, yes, I've tried searching for this)

I started off at vmware.com where I got a copy of VMWare Player and the "appliance" for Gutsy 7.10 in English.

When I load this image into VMWare player I see a normal enough Linux boot sequence but rather than it going on to laod a GUI and allow me to login there it stops at a console prompt inviting me to login and when I do that I just remain stuck at a console prompt rather than it going on to run Gnome.

I've tried googling for solutions and have seen suggestions such as "startx" to start the GUI or "init 5" but there is no "startx" in the PATH and "init 5" doesn't have the desired effect.

So is there some simple "magic" for kicking the GUI into action?

(thanks in advance!)

---

### Post by wrightflyer on 2007-11-19
Sorry, I think I just answered my own question. There are several 7.10 images for VMWare Player available. The one I got was 187MB from "thoughtpolice" while the one actually linked from the VMWare site is 657MB. I'm guessing the +470MB is the bit I'm missing :(

(yup, just confirmed this - the site I got it from says "Where is the GUI?    It's not installed. This is a server installation. If you still want a gui, run:    sudo aptitude install xorg gnome " - rats, wish I'd bothered to read everything before the download, ho hum!)

---

