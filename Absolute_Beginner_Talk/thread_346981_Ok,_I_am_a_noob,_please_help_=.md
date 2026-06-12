---
title: "Ok, I am a noob, please help =\"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by chemm on 2007-01-26
I've been having a lot of problems with my laptop, and it tends to for no reason shoot up to 100% usage of my CPU so someone I know told me to try booting with ubuntu, So i downloaded it and i followed the instructions but when it says Burn Image, I don't see what image it is talking about, I dont get what -exactly- i should burn...

---

### Post by meng on 2007-01-26
You burn the .iso file to CD. Look here:
[www.psychocats.net/ubuntu/iso](www.psychocats.net/ubuntu/iso)

---

### Post by Catsworth on 2007-01-26
Ok, are you currently running Windows?  Have you downloaded a file with a .ISO extension?  What software do you use to burn data to CD?

---

### Post by Medieval_Creations on 2007-01-26
If you downloaded the Ubuntu CD Image or "iso" you will have to burn that image to a CD before you can use the live CD or install Ubuntu.

Since I'm not sure what OS you are currently running I really can't advise what stepd you will need to take to burn the iso.

In winblows you can use apps like Nero or Roxio.
in Linux you can use K3b or Baker.

---

### Post by pesach on 2007-01-26
go to
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by chemm on 2007-01-26
> **Catsworth said:**
> Ok, are you currently running Windows?  Have you downloaded a file with a .ISO extension?  What software do you use to burn data to CD?


Windows xp, I used Infra Recorder, but I think I downloaded the wrong file before... So now im redownloadnig the one I believe is correct.

---

### Post by meng on 2007-01-26
What are the specifications of your system: CPU, RAM, graphics card?

---

### Post by Medieval_Creations on 2007-01-26
I haven't user Infra but I'm sure there is an option in there to burn Image to disk.  The file after downloaded should be something like ubuntu-6.10-desktop-i386.iso.

---

### Post by chemm on 2007-01-26
> **meng said:**
> What are the specifications of your system: CPU, RAM, graphics card?

AMD 3200, 1GB Ram, I'm not sure exactly sure what I have for a graphics card, or where to check.

---

### Post by meng on 2007-01-26
If you're running Windows, look in Settings, Control Panel, System, Hardware, Device Manager, Display Adapters. Or for limited information, just right click the Desktop, and then go to Properties, Settings, look under Display. Perhaps there's a better way, but I'm not a Windows guru.

In any case, you ought to be fine downloading and installing from the x86 Live Desktop CD version.

---

### Post by jkeyes0 on 2007-01-26
Just to make sure we're on the right page here, are you wanting to actually install Ubuntu, or are you wanting to diagnose your Windows installation using an Ubuntu cd?

---

### Post by chemm on 2007-01-26
> **jkeyes0 said:**
> Just to make sure we're on the right page here, are you wanting to actually install Ubuntu, or are you wanting to diagnose your Windows installation using an Ubuntu cd?


I want to see if the problem I am having still exists while booting up through ubuntu.

Since the problem I have no one can resolve without "reformat" and I don't have my XP cds any longer and i'm not spending 200$ on new ones...

---

### Post by meng on 2007-01-26
You can run Ubuntu as a Live CD without installing anything, but it will run more slowly than if it were installed to your hard disk. So if it runs nice and quick with low CPU usage, then you know it's not a hardware problem, but if it runs slowly, you can't say for sure it IS a hardware problem (but with your system specs I don't think it will run that slowly).

---

### Post by jkeyes0 on 2007-01-26
> **chemm said:**
> I want to see if the problem I am having still exists while booting up through ubuntu.

Since the problem I have no one can resolve without "reformat" and I don't have my XP cds any longer and i'm not spending 200$ on new ones...

If that's the case, and you're just wondering how to burn a .iso file, you can go to google and search for a program named "burnatonce". One purpose program: to burn .iso files.

Burn the .iso file onto the CD, reboot with it, and see how it runs. 

However, I'd have to say that in about 95% of the cases I've seen, with processor utilization spiking like yours seems to be, it's usually application related. 
Have you opened task manager when it spikes to see what's actually using it? It could be anything from a virus or spyware to a regular program with poor memory/cpu utilization, or even an antivirus program attempting to run in the background or update itself.

---

### Post by chemm on 2007-01-26
> **jkeyes0 said:**
> If that's the case, and you're just wondering how to burn a .iso file, you can go to google and search for a program named "burnatonce". One purpose program: to burn .iso files.

Burn the .iso file onto the CD, reboot with it, and see how it runs. 

However, I'd have to say that in about 95% of the cases I've seen, with processor utilization spiking like yours seems to be, it's usually application related. 
Have you opened task manager when it spikes to see what's actually using it? It could be anything from a virus or spyware to a regular program with poor memory/cpu utilization, or even an antivirus program attempting to run in the background or update itself.


It's weird because for example:
(on windows xp)

I'll have iTunes, Firefox, World of Warcraft open.


My task manager will say World of warcraft is using 100%, ok so I shut it down, then it will say iTunes is using 100% so I shut that down, then Firefox is using 100% and I shut that down and it will go to the system Idle using 100% or somewhere close to it...

It doesn't appear as if 1 program is using anything, and I can hear my laptop get noticeably louder, as if it is burning something, but it doesn't seem to be a heat problem, I just bought a Cooling system for it, that it sits on...

Someone mentioned it could possibly be a memory leak but they were not sure either...


Edit:

Also I booted with Ubuntu and it was idling at 47-50% CPU usage, and when I did anything (ie opened firefox) it jumped up to Mid 80's to low 90's used; Now I don't have it installed yet I just was using the CD so I don't know if that makes a difference.

---

### Post by meng on 2007-01-26
> **meng said:**
> You can run Ubuntu as a Live CD without installing anything, but it will run more slowly than if it were installed to your hard disk. So if it runs nice and quick with low CPU usage, then you know it's not a hardware problem, but if it runs slowly, you can't say for sure it IS a hardware problem (but with your system specs I don't think it will run that slowly).
I think you can rule out a hardware problem. If you want to be sure, boot the CD again but use the memory test option to check out your RAM, rather than booting the desktop.

If you ultimately decide to come over to Ubuntu, then welcome! Back up all your data first though.

---

### Post by chemm on 2007-01-26
> **meng said:**
> I think you can rule out a hardware problem. If you want to be sure, boot the CD again but use the memory test option to check out your RAM, rather than booting the desktop.

If you ultimately decide to come over to Ubuntu, then welcome! Back up all your data first though.

I will have to try that, thank you for your responses.

---

