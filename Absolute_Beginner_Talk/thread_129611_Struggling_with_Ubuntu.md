---
title: "Struggling with Ubuntu"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by don_c on 2006-02-14
No problems installing Ubuntu on an old spare PC at work and am able to look at the internet and shared MSoft server files but I can't get my head around installing software.  I am posting here because everyone suggests that Synaptic is simple but i can't get it to work for me.

I want to run GNUCash - I search (under "Provided Packages") in Synaptic Package Manager and nothing is found.  I search under "Name" and three packages are found - what is the difference?

Synaptic GNUCash is version 1.8 and I want 2.0 but I try to install anyway.  It runs through and everything seems successful but where is the application?  How do i run it????  It doesn't appear on the application list so I don't know what to do next with it...  I want 2.0 anyway and noticed there is a .deb file for this version on the GNUCash website, but I have no idea what to do with it after downloading it.  I have found info that says use dpkg but this can only be done by a SuperUser (which is disabled in Ubuntu!).

I've also tried running VNC server - I'm not sure if Remote Desktop is VNC server or if I need to install VNC separately.  I need to change the display number to see the Linux box through our router - can't find how to do this in Remote Desktop...

I have found tons of very sparse instructions (easylinux, wiki.ubuntu) on how to install applications but I need something a bit clearer for an advanced Windows user but extreme novice Linux/Ubuntu user.  To me this is where Ubuntu is sadly lacking - there is a lot of info about and for people with a lot of time the answers can be found.  But to convince the many Windows users, even those who want to change, then life must be made easier I'm afraid.  Good, step-by-step documentation would help, with some explanation of why we are doing things.  A command reference would be nice too.

Any help would be appreciated, I am keen to use Linux at work in the future but there is some way to go before i have convinced myself it is practical for ordinary users let alone convincing the management....

---

### Post by gord on 2006-02-14
you need to enable the [extra repositorys](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse) and then look for it again, i can see it fine :)

and to be a superuser in ubuntu you have to prefix the command with 'sudo' for example
```

sudo dpkg -i filename.deb

```

---

### Post by george_apan on 2006-02-14
The easiest way to run a vnc server for the current display that I found was to install the x11vnc package from synaptic and then run it with:
```
x11vnc -forever
```
That way you could be able to see the vnc server with its IP, something like:
```
192.168.1.1:0
```
:0 is the current display. You could use any windows or linux vnc client.

---

### Post by meborc on 2006-02-14
I know that this will come as a surprise, but Ubuntu has a built in help called Yelp... You can access it by clicking on the life-saving-ring icon in one of the menues. :mrgreen: 

I am not saying this because i don't want to help :) but because things are well explained there, and to start looking for answers, users should first try there. 

All the things you must do like adding the repositories mentioned before and configuring your graphic-card are explained there as well... Don't be frightened though to ask questions here as well, as the Yelp is covering the most basic functions and is nothing near complete.

All i can hope is that You stick with Ubuntu and after a while start loving it like i do now... I started using Ubuntu just before Breezy came out, and my home box runs now under Dapper dev. ... ceep up the good faith, loose the windows way of doing things and welcome :mrgreen:

EDIT: almost forgot, look into: [https://wiki.ubuntu.com/InstallingSoftware](https://wiki.ubuntu.com/InstallingSoftware)

---

### Post by BoyOfDestiny on 2006-02-14
[QUOTE=don_c]No problems installing Ubuntu on an old spare PC at work and am able to look at the internet and shared MSoft server files but I can't get my head around installing software.  I am posting here because everyone suggests that Synaptic is simple but i can't get it to work for me.

I want to run GNUCash - I search (under "Provided Packages") in Synaptic Package Manager and nothing is found.  I search under "Name" and three packages are found - what is the difference?

Synaptic GNUCash is version 1.8 and I want 2.0 but I try to install anyway.  It runs through and everything seems successful but where is the application?  How do i run it????  It doesn't appear on the application list so I don't know what to do next with it...  I want 2.0 anyway and noticed there is a .deb file for this version on the GNUCash website, but I have no idea what to do with it after downloading it.  I have found info that says use dpkg but this can only be done by a SuperUser (which is disabled in Ubuntu!).

I've also tried running VNC server - I'm not sure if Remote Desktop is VNC server or if I need to install VNC separately.  I need to change the display number to see the Linux box through our router - can't find how to do this in Remote Desktop...

I have found tons of very sparse instructions (easylinux, wiki.ubuntu) on how to install applications but I need something a bit clearer for an advanced Windows user but extreme novice Linux/Ubuntu user.  To me this is where Ubuntu is sadly lacking - there is a lot of info about and for people with a lot of time the answers can be found.  But to convince the many Windows users, even those who want to change, then life must be made easier I'm afraid.  Good, step-by-step documentation would help, with some explanation of why we are doing things.  A command reference would be nice too.

Any help would be appreciated, I am keen to use Linux at work in the future but there is some way to go before i have convinced myself it is practical for ordinary users let alone convincing the management....[/QUOTE]
 
Yes it is a vnc. I tested it myself just a few days ago. To change the display when using vncviewer ip:#

for example it would be something like vncviewer 192.168.1.100:0

For added security I recommend you lock the screen too.

---

### Post by don_c on 2006-02-14
I will persevere, don't worry.  I have long term plans for using it at work and I won't give up easily.  I think I have been misled a bit by everyone calling Ubuntu "easy".  I'm new to Linux in general and compared to Windows it certainly isn't easy although it may well be streets ahead of previous Linux distributions.

I have checked the Ubuntu help and the other online help areas and not found them much use for a novice.  I did find a general linux intro course which I am starting to work through and I'm finding this ideal to sort out some of the linux concepts.  I'll leave the Ubuntu specifics until later

Still can't get VNC to work properly - I can talk to it using display number 0 but when I run "vncserver :5" I can't communicate to it on this display number.  Have plenty of Windows PCs running VNC on various display numbers so there is not a port forwarding problem.  Is there any way to check the status of vncserver after typing in vncserver :5 ?

---

