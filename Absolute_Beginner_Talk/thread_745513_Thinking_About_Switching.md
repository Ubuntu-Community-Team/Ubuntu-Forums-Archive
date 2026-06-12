---
title: "Thinking About Switching"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by TheHumphries on 2008-04-04
Greetings All! I hope my title is original :)

I am considering switching over my home server (config will follow) from Windows Server 2008 Standard Beta (6001 Build) to an Ubuntu. Before I do that, I would like some input from others if possible on recommendations on programs and some heads up on any possible issues I may have.

First off, here are my basic functions of my server (Mostly a Media Server):
Itunes Server - 7.x (the newest version)
MyTunesRSS - Streams Itunes Library for when I travel
AIM - Sending text, etc
Super Doctor 3 - Remote Support
TeamSpeak - TS Server
SpeedFan - Monitoring Program

Hardware Setup:
Dual 2.8Ghz LV 800Mhz FSB Xeons
Supermicro X6DHE-XG2 Motherboard
4GB 400mhz DDR2 ECC/REG Memory
Single 40GB IDE ATA100 (OS) Drive
Dual 80 WD Sata150 HDs in Raid 1
2 Port Adaptec Sata 1210SA Raid Card

(Other home systems include serveral PCs, Macbook, and Mac Mini. G-Wifi and GBe ran.)

I am assuming off the bat, my 2 biggest issues will probably be Raid card and losing my itunes and its sharing capabilities.

Anyone have any recommendations, hint, tips, or anything else I should know? Any information would be helpful.

Thanks for your time!

Nick Humphries

---

### Post by Masteroc on 2008-04-04
Well, setting up the ubuntu server (install) is very easy. I have done it multiple times and it hasn't ever given me a problem (except when i ran into a bad cd drive..hardly ubuntu's fault :) )
 Secondly, for your programs:
(Sorry if these are out of order)
1) Itunes Server, google mt-daap (good guides). 
2) For AIM, Pidgin. 
3) And im pretty sure that TS and vent have linux versions (have to double check). 
4) Instead of speedfan you can use gkrellm or conky
5) I have no experience with Super Doctor 

The only hard thing that i ever ran into was setting up samba and that is just because it took me a while to get the config file correct for my setup.

Also, i have never done it myself, but I hear that Ubuntu has great raid support.

Hope this helped

P.S. An important thing to remember (especially coming from windows) is that Ubuntu Server does NOT come with a gui...that doesn't mean that it isnt easy to install, it just doesnt come with one ootb.

---

### Post by TheHumphries on 2008-04-04
Thanks for the response! I will need to start looking at those applications you recommended!

Is that a GUI that I can download for Ubuntu Server?

Are there big differences between Ubuntu Server and Desktop versions? I figured at first at least I would be better off with a GUI.

---

### Post by hyper_ch on 2008-04-04
no, a gui won't give you any improvements

server services are configured with through text files and for that it does not matter if you use a basic text editor or some highly advanced one

TS2 and ventril can on linux, I have them setup on my debian etch server

big difference between server and desktop is that the desktop version wastes previous resources that are better suited for other stuff on a server

what do you mean by remote support?

---

### Post by Fixman on 2008-04-04
> **TheHumphries said:**
> Thanks for the response! I will need to start looking at those applications you recommended!

Is that a GUI that I can download for Ubuntu Server?

Are there big differences between Ubuntu Server and Desktop versions? I figured at first at least I would be better off with a GUI.

If you want just to use iTunes and that stuff, and on server work, I reccomment you downloading the desktop version.

---

### Post by SOULRiDER on 2008-04-04
> **hyper_ch said:**
> 
what do you mean by remote support?

I believe he means VNC, he will need X if he wants to do VNC.

---

### Post by Masteroc on 2008-04-04
> **TheHumphries said:**
> 
Is that a GUI that I can download for Ubuntu Server?

Are there big differences between Ubuntu Server and Desktop versions? I figured at first at least I would be better off with a GUI.

There are many options for a GUI for Ubuntu Server...all the ones that are available for any other linux distro actually. You can choose from KDE, Gnome, Xfce4, fluxbox, openbox, icewm...the list goes on. Since this is a server (but since you are coming from Windows) i would suggest Xfce4 as a good light GUI thats still easy enough for a newer user to use. And as long as your server isn't getting slammed the GUI should not affect its performance.

The Ubuntu Server and Desktop versions are similar, in fact a lot of people use the server install disc to make a minimal Desktop install. The only reason that i would not go with a Desktop Cd install is because of the extra bloatware that you most likely do not need for running a server.

---

### Post by hyper_ch on 2008-04-05
the server install uses a different kernel than the desktop. one that is geared towards server operations... don't forget that.

---

### Post by ramjet_1953 on 2008-04-05
If you would like a GUI, have a look at the lightweight ones out there.

One that is getting some attention at the moment is LXDE.

Here's a link: [http://lxde.sourceforge.net/](http://lxde.sourceforge.net/)

Regards,
Roger :cool:

---

### Post by hyper_ch on 2008-04-05
people who ask for a gui on the server don't understand how services work on linux... they are configured by editing config files and not through some gui menu.... hence a gui is utterly useles...

---

