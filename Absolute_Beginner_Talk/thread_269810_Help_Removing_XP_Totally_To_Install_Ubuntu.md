---
title: "Help Removing XP Totally To Install Ubuntu"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by hellie on 2006-10-02
Help!!!

The aim to completely get rid of XP and have a Lunix Distro-Ubunto only. My main question is how can I wipe the disc hard clean of XP and start a fresh with Ubunto? 

I have taken expert advice from my IT Dept re XP that has totally crashed. I have no Start menu, Control Panel, Desktop.

Apparently XP is very very sick. Although my IT Dept don't support Lunix they think its good solution for me personally as although I have never used Lunix I am one of 2 very IT literate District Councillor my local Council has. 

I have 2 discs one for Utbantu and one for SUSE (both from different sources neither will load the installers.

I can't get into BIOS to check its booting from the DVD.

One of both of the discs it loads the kernel, a load of writing appears and then you wait and wait and the installer does not load.

Also why can't get into BIOS? I am using alt f2 on my keyboard as it is an interactive one.  What I am looking for in BIOS to make sure it boots from the DVD/CD?

May question is how can I wipe my hard disk clear of XP? I really want to run Ubuntu but tried SUSE in case it was a problem with the disc 

It is by the way a brand new PC so no issues with space, DRR Ram etc

Helen

---

### Post by bluefrog on 2006-10-02
Did you get the linux cd from the internet or with a magasine?

if coming from internet and then you burnt them, buy a linux magasine with a ubuntu cd in it and try again booting, you may have more luck.

or reburn your iso file at a lower speed.

if still have a problem with both solution, you may have hardware problem in the end (even if it's brand new)

James

---

### Post by xpod on 2006-10-02
You`ll know wether it`s booting from cd-rom first just by sticking the cd in and rebooting.
If it goes straight to your dodgy windows then it needs changing in the bios.
If it`s booting you can wipe your disk clean with "gparted" upon the live cd.
In fact once you run the installer when the cd`s running  all you have to do is point it to the hd once its at that stage and it`ll overwrite all thats on the drive anyway.....Or you can wipe it maually beforehand.

Put the cd in and see

EDIT:Sorry,if it`s sticking as the cd loads then mabey you too might need to try the "alternate cd"....quite a few need to even with decent specs

---

### Post by petri on 2006-10-02
Maybe **Delete** lets you in BIOS. 
Or **Alt** and **Esc** gives you a white box 
there you can choose your CD/DVD as bootdevice.

What to look in BIOS? Look after First Bootdevice or something similar. Note: only if you can't use Alt and Esc.

While installing... You get a Live session with a fully funtional desktop :) There you can click icon **Install** and you can browse the internet at the same time as you install Ubuntu. There is a good guide to follow while installing [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Because you are not going to do any partitioning you are going to do just fine with your installation. Just follow the guide above. :D

---

### Post by Ben Sprinkle on 2006-10-02
What uncle xpod said. ^
Otherwise you can use Acronis to totally wipe it out.

---

### Post by bulldog on 2006-10-02
Well if the PC is brandnew it could be you have an option to choose which device you want to boot by start up.

I have to use F11 so there opens a menu and I have the choice.

It's mostly on the bottom of your creen where this is listed when you boot your computer.

Take a look and id it's there,choose to boot from cd and Ubuntu will be loaded.

You can install Ubuntu from the desktop and when you get to the partitioner,select the option use whole drive,or manually partition if you prefer.

By this action you can remove Windows completely and install Ubuntu.

---

### Post by xpod on 2006-10-02
I dont suppose it would have a bios password set would it if it`s a work pc of some sort??
I had to recently figure that out as i too could`nt get into the bios on another sys i have.
Had to eventually remove the mobo battery to reset it

---

### Post by Ben Sprinkle on 2006-10-02
> **xpod said:**
> I dont suppose it would have a bios password set would it if it`s a work pc of some sort??
I had to recently figure that out as i too could`nt get into the bios on another sys i have.
Had to eventually remove the mobo battery to reset it

Got any doofer?

Anyways, just use Acronis. That's what I used.

---

### Post by Drakkor on 2006-10-02
What brand of  machine e.g Dell, Gateway,other ?

---

### Post by Dinerty on 2006-10-02
Your key maybe different to access the bios, usually when the system boots up it will quickly display on screen what to press, so keep a eye out.

Once the CD has loaded (May take several minutes due to it reading and loading everything from CD) all you have to do is click "install" icon which is nicely placed on the desktop.

Once ths process has begun and you have chosen the nessaccery options for your system (username, passwords and so forth) it will then load up the partition tool, if you just want Ubuntu on your system, you can tell Ubuntu to overwirte EVERYTHING on the drive and use the whole hard drive just for Ubuntu.

---

