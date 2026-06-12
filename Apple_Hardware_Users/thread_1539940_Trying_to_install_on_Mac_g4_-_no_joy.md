---
title: "Trying to install on Mac g4 - no joy"
date: 2010-07-27
forum: Apple Hardware Users
---

### Post by jellygraphics on 2010-07-27
Hi all,

I'm getting very frustrated now!! 

<rant>
Have old(ish) Mac G4 it's a Quicksilver single processor, 867Mhz, with 1.2GB Ram and a 60GB hard-drive. 

Will comfortably run Mac OS 10.4 (Tiger)

I wish to use this mac as a Ubuntu system, with HFS+ 500GB sata hard-drive (as second, non-booting drive) using an internal PCI SATA controller card.

I'm trying to install Ubuntu on the mac. I've tried:

10.04 live (both PPC version and regular, PPC version I've even redownloaded and reburnt to a new disk)
10.04 Alternative
xUbuntu 10.04
9.04 Ubuntu PPC version
Ubuntu 6.06 PPC alternative install
and even tried Debian 5 

All the above open to a "prompt" where I've tried install, tried the video=ofonly, nosplash etc etc and the powerpc versions etc etc

All I get is a hanging solid White Screen - for upto an hour, no harddrive sound and I think the CD drive has stopped doing anything. Tried pressing a few keys too, nothing.

With one exception and that is the Debian - this will kind of boot to the point where I get a menu, go through all options like choosing a country etc etc, but this hangs on Partitioning section - either at 39%, 46% or 50% - thought I was being impatient, so left it at 50% yesterday - again for well over an hour = nothing.

Have reset the PRAM and NVRAM this AM - still only ever get the white screen.

One occasion saw the Ubuntu black screen with the red dots which then froze completely - this was the case with ubuntu 6.06 (i think as I've tried that many varients!!) again I waited for quite some time before having to hard reset.

I've set up Ubuntu on two PC laptops without too much trouble, but this is beyond me - I have no idea what to try next!!

any help/suggestions gratefully received!!

</rant>

---

### Post by Doobie9 on 2010-07-27
I've had a similar experience with an old iMac G4 (800 mhz). The white screen is an incompatibility with the Kernel Mode Setting in newer Linux distributions (I even tried Fedora and Yellow Dog). 

The first distro that I got that 'stuck' was Debian Lenny, with the net install. My first suggestion in you care would be to try a different install method for Debian (such as the full disk, or the DVD, or the net install--just something different from what you've been trying).

When it finally installed it worked pretty well. I can get the machine to suspend if I use a shell script to get it to switch to a tty beforehand (and I need to figure out how to integrate it better). Sound didn't work out-of-the-box, but that was fixed relatively easily with a `modprobe snd-powermac` command. I'd still like to be able to turn off the monitor...

In all honesty, these old PowerPC machines are a total PITA. This hardware is a perfect storm of old, weird, and proprietary :|. Whenever I try to install a Linux distro on one of these machines, I just burn a bunch of different PowerPC distros and then just go through them all methodically until I find one that works. Not a very elegant solution, I know :P. 

Good luck. :)

---

### Post by jellygraphics on 2010-07-27
Thanks

I'm literally just trying the Debian Net install - current;y hanging up on 1% of the Retrieving apt-setup-udeb??

It's really weird!

Will try the DVD download I guess, but 4.4Gb download will have to wait till everyone's gone home!!

---

### Post by Doobie9 on 2010-07-27
When it stops can you ctrl-alt-f-key into another tty? If this happens again it might be worth checking /var/log/messages to at least get a lead. It could very well be a driver problem.

If Debian doesn't work out, you may want to go back and try an Ubuntu server install. Since it is (last time I checked) a non-x-windowed environment, there are going to be fewer stray variables (which is, to be honest, why Debian should work). 

I haven't had much luck at all getting LiveCDs to boot on PowerPCs. The best strategy, from my experience, is to just get your Linux system installed--no matter how simple it is--and then Google search for specific tricks and tweaks to get the environment you want up and running on your machine. 

Don't lose patience--you're going to need it :P. For this you're going to need a positive mental outlook and it wouldn't hurt to practice some deep-breathing exercises.

---

### Post by jellygraphics on 2010-07-28
Hi

I've tried again this AM with Damn Small Linux - won't boot from CD, Kubuntu,  tried pressing CTRL + ALT + F on white screen and does nothing, is that what you mean? i.e. should I wait till white screen before mashing those keys or do it before?

Incidentally, as soon as I type install or whatever command I'm trying, it says "loading Elf32 Kernal" then few seconds later bang. White Screen of nothingness (WSN - bit like BSOD)

Am burning Debian 5.05 powerpc net install disk at the moment to try again...

Tres frustrating as I really have lots of work to be getting on with

---

### Post by jellygraphics on 2010-07-28
So, tried using Debian 5.05 new disk, using install-powerpc video=ofonly

then 

Loading Elf32 Kernal

then it says loading RAM disk...white screen of death!

No amount of ctrl alt f does anything either...


Perplexing. 

What to try next...I wonder?

---

### Post by jellygraphics on 2010-07-28
Just trying Debian using just install command...

got a load of text on screen - obviously loads of checks taking place.

It's getting stuck saying

[               8.825491] usbhid: v2.6:USB HID core driver

then does nothing??

Anyone got any ideas?

Thanks

---

### Post by jellygraphics on 2010-07-28
should state it's a debian net install disk
:(

---

### Post by jellygraphics on 2010-07-28
Guys what's noapic and how would I change the boot options for one of these installs???! thanks

---

### Post by rrrrob on 2010-07-28
Hello,

I'm having and had the same basic issue with a G4 dual 500.  However I believe I've gotten Ubuntu 10.04 server to now install.  What I did to get around the hanging install is to type the following, and it did seem to make a difference as to the order of the commands. If I typed it in in opposite or any other order it would not work.

boot: install-powerpc Mem=1024m video=ofonly

Now I have 1GB of ram in the machine thus the 1024, you will have to adjust this according to your system.

That is what I've done to get it to install.  I can't get it to boot due to the white screen yet, but at least it seems to be installed.  I have been told and have read that now that I have it installed and that these commands helped make that happen, I should add them to my /etc/ yaboot.conf file.  Thing is I don't know how.

Anyway, give this a try. I'm curious if this trick works for you as well.  If I figure out how to boot around the white screen I'll post answer.

Rob

---

### Post by avtolle on 2010-07-28
What I've been able to do with Ubuntu PPC on a G4 Cube is to d/l alternate iso, then do a comand line only install. Once I'm installed and updated, I create an /etc/X11/xorg.conf file with the appropriate settings for my setup. Once that's finished, I make sure the appropriate repos are enabled, install the desktop (usually, Gnome, but have done lxde too) using the meta package in the repos, and once that's done, reboot. This has been successful for me from 9.04 on, but YMMV. Obviously, I've a copy of an appropriate xorg file that I've used before, and tweaked as needed. Good luck.

---

### Post by Doobie9 on 2010-07-28
> **jellygraphics said:**
> Guys what's noapic and how would I change the boot options for one of these installs???! thanks

When you get to the first boot screen you can hit tab and get a list of options. On yaboot these are typed in, IIRC. (Either that, or you type in 'help'.)

Additional options are entered just by typing them after the initial command. For example if you typed 'install' at launch you'd add in your options like this:

> install napic

You may have to do some Googling to find out what special parameters you may need to be successful.

---

### Post by jellygraphics on 2010-07-29
Have thrown the towel in - grabbed an old PC intel machine Ubutnu works straight away and it's all up and running from the live install CD

thanks you all for trying to help!:p:D:D:D:D

---

### Post by oswaldkelso on 2010-07-29
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=589701](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=589701) ???

---

### Post by yaga on 2010-08-01
Hey folks, 

Just wanted to let you know i installed Hardy Heron on a G4 iMac "iLamp" Power-PC architecture w/no problems whatsoever. ***Edit***: It has NVIDIA GeForce2 MX graphics & a 700 MHz processor.

---

