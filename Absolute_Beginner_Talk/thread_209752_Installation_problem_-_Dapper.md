---
title: "Installation problem - Dapper"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by Jax Kovak on 2006-07-05
Hi, I have a copy of the Ubuntu Dapper release and I am eager to install it, however I have a rather minor problem that becomes rather more serious as soon as I click on the 'install' icon.

I have an NVIDIA GeForce 6600LE GFX card and Ubuntu will only boot into a screen resolution of 640x480, which is no use to anyone whatsoever when it comes to manipulating the installation screens!

Iv read the documentation, installed the NVIDIA driver, re-configured the xserver and followed several different sets of instructions to do all of this, including making sure the monitor refresh is set properly etc.

All to no avail.

I now have a nice packet of Ubuntu CD's which are likely to become coasters unless I can get the live cd to boot onto a more sensible resolution.

Can anyone give me any help please?

All the best

Jax

---

### Post by Mike_N on 2006-07-05
try the Alternate Install disc, it's more bare bones so that you can install and then use Ubuntu, rather then trying to run it durring install... worked great on my old G3 iMac...

---

### Post by Jax Kovak on 2006-07-06
Thanks for the reply Mike.

"Alternate Install disc"

Okay, Id love to, but there isn't one. The disc I have is just the live CD with the install icon on the desktop. There is no alternate disc, just this one. Its the one that was sent out to me.

I'm now also a little concerned about the prospect of dual booting with Dapper as Iv read about some problems with it when using anything that is even a slightly non-standard partitioning setup. My system has 3 hard disks with a total of 9 partitions and I need to install Dapper on HD2 partition 3. Is this likely to cause a problem?

Jax

---

### Post by mssever on 2006-07-06
When it comes to partitions, I didn't have any trouble with my dual-boot partition setup (2 disks ~10 partitions total). However, I used the manal partition setup tool (part of the installer) to tell Ubuntu what to do. It quto-detected Windows properly.

As far as the install and screen res goes, I've heard, but not tested, that you can type "server" at the install CD's boot prompt to get a text-based setup. If so, thaafter the setup is finisted, you can use aptitude to install gnome-desktop. If everything works, you should end up with pretty much a default install, although I can't say for sure since I've never actually tried it.

---

### Post by Jax Kovak on 2006-07-06
Thanks mssever, I intended to use the manual setup anyway (If and when I can actually see it!)

Typing server? Ill try that later on, but since I'm not really a text based kind of person I'm not sure it will do me much good! Whats aptitude (Other than something I'm clearly lacking for Linux!!)

Jax

---

### Post by mssever on 2006-07-06
Aptitude is a text-based package management tool (you use it to install and uninstal programs). The graphical equivalent is Synaptic once you get everything working properly.

After installing and rebooting, type [FONT="Courier New"]sudo aptitude[/FONT] at a command prompt. To search type a slash (/)followed by what you want to search for (gnome-desktop in this case). Type "+" to select a package and "g" to install it. Ctrl+T activates the menus.

Another text-based alternative to aptitude is dselect. Use whichever is easier, until you get a full install.

*By the way, is this your first experience with Linux? if so, welcome aboard!*

---

### Post by mssever on 2006-07-06
I just found this link, which might be helpful to you: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Jax Kovak on 2006-07-06
Thanks for that link mssever, there is a lot of information there that I'm working my way through as I get the time. The GAG boot disk utility is a great idea that Ill look into (Since my machine has some critical work stuff on the windows installation)

BTW: Out of interest - Is it possible to install KUbuntu and then convert it to Ubuntu?

I ask because I have the live CD of KUbuntu here and there is no problem with the screen resolution at all (Which means I could install from this disk), but I'm really not at all fond of the KDE desktop at all.

Thanks for all your help

Jax

---

### Post by crystal on 2006-07-06
> BTW: Out of interest - Is it possible to install KUbuntu and then convert it to Ubuntu?
Yes, you can read [Installing Gnome on Kubuntu](http://psychocats.net/ubuntu/gnome.html).

---

### Post by Jax Kovak on 2006-07-06
Thanks crystal, I might well go that route if I can.

---

