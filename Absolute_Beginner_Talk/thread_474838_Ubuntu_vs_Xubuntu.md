---
title: "Ubuntu vs Xubuntu"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by winlux99 on 2007-06-15
Hi. I have a really old laptop running Ubuntu right now. I'm thinking about switching to Xubuntu because according to what I heard its made to be run on old systems. Do Ubuntu and Xubuntu share the same codes?

---

### Post by mikewhatever on 2007-06-15
Yes, most of it. The operating system is the same, but the desktop environments are different (Gnome vs XFCE).

---

### Post by candtalan on 2007-06-15
all you need to do is install the package 
xubuntu-desktop
and then you have the choice at login time of which session to use gnome (ubuntu) or xfce (xubuntu).
If later you want to uninstall
ubuntu-desktop I think there is no problem.

---

### Post by bodycoach2 on 2007-06-15
Unless you'd like to start off with a completely clean install, just do "sudo apt-get install xubuntu-desktop.

You'll be ready to go.

What are the specs on your laptop? If it's anything under 800 MHz, Xubuntu will probably run better. Also, if you have 256 MB or less of ram, Xubuntu is a better choice. Keep your ram topped out, and Xubuntu will be good.

---

### Post by NJC on 2007-06-15
winlux99;

I have a PIII/500Mhz and recently installed the Xubuntu desktop. You can install it command line or search for "xubuntu desktop" in Synaptic. 

Once installed you need to Log out and at the login screen, select Sessions and select XFCE. I didn't find that XFCE (Xubuntu) was much quicker (~20%?) but it killed off my keyboard volume controls and so I haven't used it. It's worth trying though as it looks well done.

---

### Post by byen on 2007-06-15
I would strongly advise xubuntu /xfce for any low end computers. Uses less resources compared to gnome. Its only a command away (mentioned above) so just give it a try. Its very minimal yet pretty well rounded when it comes to functionality.

---

### Post by buuntuu! on 2007-06-15
out of curiosity: would it not be wise to CLEAN-install xubuntu on a low-end machine without having ubuntu also? won't the additional packages that ubuntu/xubuntu drag on performance or is it just a matter of harddisc-space??

---

### Post by Rocket2DMn on 2007-06-15
Should just be a matter of HD space.  Even then, he can clear out the ubuntu-desktop and use only xubuntu-desktop.

---

### Post by meborc on 2007-06-15
> **buuntuu! said:**
> out of curiosity: would it not be wise to CLEAN-install xubuntu on a low-end machine without having ubuntu also? won't the additional packages that ubuntu/xubuntu drag on performance or is it just a matter of harddisc-space??

a clean install is always the best options for low end machines... one thing is HD but the other is programs that require gnome libraries... you have mousepad instead of gedit in xfce etc...

---

### Post by byen on 2007-06-15
Yes and No. If Space is a problem then yes! Installing only Xubuntu would take less space but performance wise, I do not see how having gnome installed would slow xubuntu down. I do see some gnome apps and libraries running when I log into xubuntu but I am not sure the drag would be the same as pure gnome. 
On a second thought. Yeah.. A fresh install of xubuntu might be the better option.

---

### Post by johnraff on 2007-06-26
> **bodycoach2 said:**
> if you have 256 MB or less of ram, Xubuntu is a better choice. Keep your ram topped out, and Xubuntu will be good.Sorry for this noobish question, but how do you "keep your ram topped out"?
With only 128MB I'm eager to scrape any extra bit of performance I can...

---

### Post by raul_ on 2007-06-26
I use Xfce with a 128MB RAM laptop and it runs fine.

---

### Post by johnraff on 2007-06-27
> **raul_ said:**
> I use Xfce with a 128MB RAM laptop and it runs fine.Mine too, at first at least. But it seems to slow up after a couple of hours of use, so a minimised window I haven't looked at for a while might take a minute to open... :(

Some kind of dreaded Memory Leak? ... Firefox?

(edit) Aah I notice you're using xfce with Arch Linux not Ubuntu. Would that make a difference?

---

### Post by stefan1975 on 2007-07-03
hi all,

i have a dell optiplex gx270 p4 2.8ghz with 1gb ram and a gf6200. I am currently running linux mint 3.0 after trying pardus 2007. Somehow they feel rather sluggish on my pc. I am wondering if there are performance benefits in installing Xubuntu even on somewhat faster pc's (maybe later even my laptop dell precision m65 dual core t7200 2gb ram and gf-quadro) or that xfce will run just as fast as gnome on those. Especially loading apps seems to take longer then it should, like firefox and nautilus.

the load on either mint3.0 or pardus was quite low, not really much higher then it is on xubuntu gutsy ( i am trying out the tribe 2 live cd right now). if i were to install xubuntu i would want to go the gutsy way since it has some benefits over feisty, although i don't see the new xdg home dirs in tribe2 yet.

i would start using arch with xfce or with kdemod but i have been using linux for soooo long now that sometimes it is good enough that it just works without vi-ing all day and my wife would appreciate a working system as well.

thanks,
stefan.

---

