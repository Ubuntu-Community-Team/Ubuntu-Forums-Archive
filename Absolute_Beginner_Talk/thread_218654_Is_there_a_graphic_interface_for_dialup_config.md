---
title: "Is there a graphic interface for dialup config?"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by gargoyle on 2006-07-18
I have looked through my Application and other places.
The only thing I found was under Administrator Network.

Is this the only graphic interface for setting up a dialup connection?

I read the was something called Kppp and I tried installing it but it would not install. Said it could not find it. I also looked in the Synaptic manager for it but could not find it.

Is there an easy to use graphic interface to configure for dialup or do I have to use the command line configurers?

---

### Post by Afishionado on 2006-07-18
KPPP is under "Networking". However, it's only visible in the menu under KDE; you'll need to install Kubuntu for it to be really helpful.

AFAIK, there's no GUI tools for dailup under Gnome.

---

### Post by gargoyle on 2006-07-18
Afishionado said:
> AFAIK, there's no GUI tools for dailup under Gnome.

Well does not that just suck. In other words I am suck using the archaic command line?

I am using a isa hardware modem and it is not being detected, so I have to do this manually. That is one reason for looking for a GUI 

Will guess I will try to do it by command line. Damn

---

### Post by Hexx on 2006-07-19
> **gargoyle said:**
> Afishionado said:


Well does not that just suck. In other words I am suck using the archaic command line?

I am using a isa hardware modem and it is not being detected, so I have to do this manually. That is one reason for looking for a GUI 

Will guess I will try to do it by command line. Damn

I use gnome-ppp. You can install it via apt-get or Synaptic.

---

### Post by gargoyle on 2006-07-19
Hexx said:
> I use gnome-ppp. You can install it via apt-get or Synaptic.

I have done a search **gnome-ppp**in File Browser and Synaptic and I can not find it anywhere.

Is it supposted to be part of the Ubuntu 6.06 ? 

I did a search on the **Ubuntu packages** for *gnome-ppp* and found *Package: gnome-ppp (0.3.23-0ubuntu2) [universe]modem internet connection tool for GNOME*

Is this the program you are refering to? Also do I have to download everything on the page?

---

### Post by Sonic Alpha on 2006-07-19
Have you enabled the extra repositories yet? (This would enable you to download everything through synaptic, including the dependencies)

---

### Post by kinematic on 2006-07-19
if you mean the dependencies synaptic selected then yes they will also have to be installed.

---

### Post by gargoyle on 2006-07-19
> **Sonic Alpha said:**
> Have you enabled the extra repositories yet? (This would enable you to download everything through synaptic, including the dependencies)

I am unable to do this because I just can not get my modem to connect yet.

I have a separate post on this problem already. When I get it working I will do that however I do not know how to enable it.

Is it under Setting - Repositories ?

---

### Post by Sonic Alpha on 2006-07-19
No, you have to edit a config file, I can't remember the command off the top of my head, but it is mentioned in the help section :) (Plus, if you use [Automatix]("http://www.getautomatix.com/"), I believe it does it for you)

When you go to the [package site]("http://packages.ubuntu.com/"), make sure you download all the dependencies.  It may take a while to get them all (some dependencies have their own dependencies and so on).

---

