---
title: "help setting up simple samba server on light hardware using Feisty"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by rotarymike on 2007-08-07
Hi all. I'm trying to set up a very simple file server using Feisty server install on an old laptop with some usb drives.

Hardware:
Thinkpad 600E (300MHz P3) sans keyboard or screen (using externals to set up)
160MB ram
12GB HD (1G swap, rest is root)
using a 3com etherlink 3 pcmcia card for network
using a 3rd party (? manufacturer) USB 2.0 pcmcia card
2 USB external HD's

Software: 7.04 server install ISO, running fine after default setup.

on my daily use laptop, I use Gnome and plug-n-play stuff like PCMCIA cards and USB drives just magically start to work :) How do I achieve the same thing using the command line?

I'm not a total n00b, I've been using Ubuntu as a desktop OS on my modern laptop for a while now, but I am a command line idiot beyond the ls, rmdir kinda stuff.

I would like this PC to be able to boot unattended, share the contents of these hard drives to anyone on my subnet mask, and basically become an appliance that sits next to my router.

Help/ links/ tutorials welcome. Yes, I have exhausted my google-fu and the server docs; or at least the limits of my understanding of them.

mike AT rotarymike DOT com

---

### Post by dave-5B on 2007-08-07
i have a box doing exactly that

mount is the command your looking for, also /etc/fstab is the file which decides how all devices will be mounted

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server) 
is how i set up my samba

EDIT:
but i cant rememer the exact command for mounting usb devices

---

### Post by rotarymike on 2007-08-08
I'm in the process of d/ling the xubuntu iso, so maybe it will run on my lightweight machine. I can do all the things I want to do graphically on my daily usage laptop ubuntu install (tried and got most of it working) so I'll give that a shot.

Thanks for the help. I'll see where the xcfe interface gets me.

---

### Post by Nythain on 2007-08-08
assuming you have your network set up via router, to get your machine to do everything you want it to should only consist of
A: making sure you have samba installed... the server, not just the client (or nfs if all boxes are linux i guess)
B. a few edits to your /etc/fstab to make sure the usb drives auto mount on boot... you can google or search here for how to edit fstab if you are unfamiliar
C. setting up /etc/network/interfaces if need be to make sure you have a connection to the router/internet or whatever you need to connect to
D. edit /etc/samba/smb.conf to set up the share's however you want... since you are looking for a simple server set up that anyone on the network can access i would suggest security = share instead of security = user, this will negate the need to set up multiple other users on the server and the need to login each time.

Side note: i would also suggest researching ssh if you are unfamiliar and installing it for remote access and maintenance of the machine

once you have made all the appropriate edits and set everything up it should be good to go...
post back if you need any help or suggestions with any of the above files... or you could just continue on yoru way installing a gui for an "appliance" server box :)

---

### Post by armandh on 2007-08-08
these use linux too
some people change the os to accommodate other linux programs
[http://www.nslu2-linux.org/](http://www.nslu2-linux.org/)
something to keep in mind when the old laptop quits

---

### Post by rotarymike on 2007-08-09
I actually have one of those (a linksys slug) and I don't care for it. It tends to want to die after about 5 minutes online time - not nearly enough time to stream a movie avi file, for example. I've tried the linksys firmware as well as slugbox and pretty sure it's a hardware issue. Naturally, it's out of warranty.

On the other hand, the old 600 series of Thinkpads are pretty indestructable. I have three - the two I'm using as appliances and a slightly newer one that my wife uses as her laptop. The one she's using is also my car tuning laptop (serial port, yay) and needless to say it's been beaten around a bit in the car. 

Besides, the two 600s I'm setting up already have the failure-prone hardware removed - no screens or keyboards. I'm using a docking station with external mouse, kbd, and monitor to set everything up. And, depending on what I break, I have two sets of almost complete spares :)

They seem to be on ebay in slightly less than perfect shape for $20-40 each (I got both of mine for under $20 due to the lack of screens). I think I paid $100 for the Slug.

---

### Post by rotarymike on 2007-08-12
Got xubuntu up and running and everything is working fine... with one exception. It helps that I turned off all the services that I don't need or use on that laptop, with the exception of the fairly lightweight GUI. Samba is working fine and it's communicating well with both my other networked PCs. 

These old laptops have USB 1.1 built-in. I use a PCMCIA USB 2.0 card... under winxp it works flawlessly. Ubuntu doesn't seem to recognize it, and certainly doesn't see any drives connected to it. I've got win and Mac OS X drivers for it... anyway I can bastardize the mac drivers into working (seeing as how OS X is a *nix)?

---

### Post by DarKirby on 2007-08-12
when you plug the usb in, do any new devices such as sda or sdb come up in /dev ?

---

### Post by rotarymike on 2007-08-12
Not using the USB 2.0 card. 

Using the USB 1.1 internal port, yes - and they appear on the desktop albeit unmounted. 

Since this is intended to be a fileserver, I'd *really* like to be able to get USB 2.0 to work - can't stream video otherwise, and file transfers become eternal.

I've done some google-fu, and it seems some cards are supported and some are not although I couldn't get a real good idea of what does and doesn't work.

For comparison, I tried the card in my thinkpad R51 (dual booting xp and Feisty) and I get the same issues - works fine under Win, complete nothing under Linux. ???

---

