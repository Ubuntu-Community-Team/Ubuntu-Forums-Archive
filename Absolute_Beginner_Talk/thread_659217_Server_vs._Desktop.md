---
title: "Server vs. Desktop"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by ianai on 2008-01-05
Hello All!  I am more or less a Linux Novice, though I do have some previous experience with Ubuntu, Kubuntu, Xandros, RH, Suse and a few other flavors.  Still, I've never stuck out any of my systems running Linux long enough to really know the OS.  I tend to get frustrated when some seemingly basic installation won't take, such as spending a day installing flash or something of the sort and resort back to the familiar ;-)

I just purchased a blade server and am torn on what to load.  I'm trying to convince myself not to load server 2003 on it as there is little to gain by loading an OS I know inside and out, so I'm thinking of delving into Linux again.  

The system will be running once configured via remote control only, something I have configured on my Linux systems in the past with success and minimal frustration, so I'm not too concerned about that.  

Anyway, I guess my question is does Ubuntu Server have a lot of the same luxuries and "dumbed down (in a good way)" features that make Ubuntu such a wonderful experience for entry-level Linux users?  I want to increase my Linux knowledge, but also fear some of the nightmare's I've run into in the past with trying to set up my own Linux servers without the knowledge to deal with major issues when they arise.  I'd really like it if I can get some of that Ubuntu instant-gratification intermingled with learning the underlying system ;-) 

A few years ago I set up an RHE server and it was an absolute nightmare, and extraordinarily unstable.  Probably due to something I did wrong, but it crashed with almost Old-Faithful regularity and being detached from any peripherals, was an absolute nightmare as I'd have to hook up peripherals with regularity to restart and try to get back the remote-capabilities.  That experience managed to drive me away from Linux with angst.  

As this Blade Server will be completely stand-alone, and in a position that it will be a genuine nightmare to hook up a mouse, keyboard and monitor if something goes wrong,is Ubuntu Server novice-friendly?

Thanks :-D

---

### Post by Skivache on 2008-01-05
I know that Ubuntu Server does not have a GUI, but you probably knew that already.  If you don't mind me asking, what is this server going to be doing and where would it be (like in your house of at work).

---

### Post by ianai on 2008-01-05
Ahh, no GUI - well its out then.  I'm too novice for that.  I guess I'll install Ubuntu and then set up Samba from there.  It is going to be in my house, in a 19" rackmount in a closet, for personal media distribution, etc.  Thanks for answering that, no GUI = not for me - at least not yet ;-)

---

### Post by bunnynuts on 2008-01-05
The server you pick all depends on your goals. At times Windows is the correct choice, and other times Linux is the correct choice...all person/project/goal dependent. I wouldn't shy away from command line too quickly. Once you play with it for a while and realize that it is not as mystical as you once suspected it works well and is easy to control remotely using ssh. Additionally, there are multiple posts on 'how to' set up the different parts. Finally, there is a lot of support on the forums. This is if you want to take the time to learn something new. But it is understandable that we don't always have the luxury to spend time learning these things...in which case maybe Windows is better for you at the moment. Finally, there are ways to set up a server with Ubuntu and the GUI. I have never done so, but do a search and see what you can find. As far as reliability goes, I have 2 separate servers that I have not actually seen for about 1 year and I manage them both remotely via cmd line. I haven't had any problems with samba, openvpn, apache, openssh etc...

Good Luck on whatever you choose.

---

### Post by HermanAB on 2008-01-05
Well, a Linux 'server' is just a desktop without a desktop.  There is no reason why you can't install all the GUI schtuff and just run in level 3 though and that happens to be how I do all my servers.

I suggest that you install Xubuntu, then once it is set up the way you want using a keyboard mouse and screen, change to runlevel 3 and manage the machine remotely over SSH.  That way, using X forwarding, you can run all the GUI utilities remotely.

Cheers,

Herman

---

### Post by Dr Small on 2008-01-05
You could install the server and then install GUI as you need it for certain applications, but you'd have to learn your way in the black abyss in order to first install a GUI...

---

### Post by ~LoKe on 2008-01-05
> **Dr Small said:**
> You could install the server and then install GUI as you need it for certain applications, but you'd have to learn your way in the black abyss in order to first install a GUI...

And it seems kind of pointless, since you'd have to install all the packages and libraries that are missing from a server install.

---

### Post by Dr Small on 2008-01-05
> **~LoKe said:**
> And it seems kind of pointless, since you'd have to install all the packages and libraries that are missing from a server install.
Just xorg and a window manager would be sufficent.

---

### Post by ~LoKe on 2008-01-05
> **Dr Small said:**
> Just xorg and a window manager would be sufficent.

I imagine the server edition wouldn't come with any gui/gtk apps (firefox, evolution, gaim/pidgim, etc).  Or is that not the case?

---

### Post by zero-9376 on 2008-01-05
alternatively you could look at something like webmin which is a nice web based admin tool for linux, you can control numerous services via this interface. although if your only planning on doing some samba shares within your house i dont think you need to go to minimal

---

### Post by Nythain on 2008-01-05
im with hermanAB... just install a desktop flavor of your liking, set everything up utilizing all those pretty gui's (users, shares, etc.)... then just set it up to load runlevel 3 and tunnel the jazz through a stable secure ssh connection for remote maintenance and configurations later.

i also suggest once getting it up and running, using ssh to log in remotely and familiarizing yourself with "console" commands as much as possible... it makes life easier in the long run, even if using a GUI Desktop... some things are just much easier accomplished via command prompt...

---

### Post by dcstar on 2008-01-05
> **~LoKe said:**
> I imagine the server edition wouldn't come with any gui/gtk apps (firefox, evolution, gaim/pidgim, etc).  Or is that not the case?

AFAIK the main differences are that the Server package installs the LAMP suite instead of the GUI stuff, and the Server kernel is optimised for that environment rather than the desktop (that the generic kernel is optimised for).

A server install can be turned into a desktop install and (vice-versa) just by installing packages, so the different CDs just help people by initially installing the environment needed, but there should be no loss in changing functionality later.

A server install can simply have all the GUI stuff by installing a "-desktop" meta-package, just sit back and wait for the downloads to complete..........

---

