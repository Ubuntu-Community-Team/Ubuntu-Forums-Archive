---
title: "Straight up - How is Fiesty?"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-05-24
I'm on the verge of reinstalling and getting Fiesty in here. I already have all of my stuff backed up on other hard drives and/or DVDs, have the DVD ISO Image of 7.04 burned and ready to go, etc.

But I'm hesitant to do so. I'm fearful that certain stuff won't work... just a thing with me and trying new software out. But anyway, how is it? Pretty solid? 

Random side question - What's the command to view all of the hard disks plugged into the system? I remember a command I could type in where I could see at the terminal all of my disk drives, something like...

/dev/sda1
/devsdb2
/dev/hdd

edit  - another question. I made a script located in my /usr/bin/local folder for running rsync from drive A to drive B. How do I open it from command line? If I simply type in the file name the script just runs. I'm just trying to get more acquianted with aspects of linux I never really dabbled with before due to me being spoiled with a GUI. So how would I open the script in a text editor from command line?

---

### Post by Dzenhax on 2007-05-24
To open the script try: nano scriptname

As for feisty, I went straight from dapper to fiesty.  I'm having probs with the wireless loosin config that I neve had w fiesty, and sometimes have to reboot to get at my root account.  Weird.

---

### Post by eapache on 2007-05-24
Feisty still has some problems detecting various pieces of hardware, but no more so than dapper or edgy. If it gets all of your hardware, then it's really great.

---

### Post by iceportal on 2007-05-24
Feisty is great! I'm loving it so far. I'm even making a website dedicated to installing/using it.

[http://ubuntu.gridrunners.com](http://ubuntu.gridrunners.com)

---

### Post by Roasted on 2007-05-24
Thanks. As I read this, I was also reminded of gksu gedit. Duuur.

Is nano an ubuntu only command? I don't see it on the "linux command directory" web page I'm looking at.

---

### Post by Happy_Man on 2007-05-24
I believe that's because nano's a program, not a bash command.

---

### Post by eapache on 2007-05-24
I"m not sure if nano is for ubuntu, debian, or linux in general, but it is actually a cmd text-editor (like notepad or gedit in cmd)

---

### Post by jonom on 2007-05-24
> **Roasted said:**
> But I'm hesitant to do so. I'm fearful that certain stuff won't work... just a thing with me and trying new software out. But anyway, how is it? Pretty solid? 

I'm loving it! I've had very little problems.

> Random side question - What's the command to view all of the hard disks plugged into the system? I remember a command I could type in where I could see at the terminal all of my disk drives, something like...

I think "sudo fdisk -l" will do the trick.

---

### Post by Deguello on 2007-05-24
You will wonder why you didn't become less dependent on Windeeeeers sooner. 

You will also find that this community in particular will do everything in their power to help you out.

Welcome to the fold.

---

### Post by ICUR2Ys on 2007-05-24
I started with Edgy and I find that I like it better.

dace

---

### Post by theicyj on 2007-05-24
> edit - another question. I made a script located in my /usr/bin/local folder for running rsync from drive A to drive B. How do I open it from command line? If I simply type in the file name the script just runs. I'm just trying to get more acquianted with aspects of linux I never really dabbled with before due to me being spoiled with a GUI. So how would I open the script in a text editor from command line?

Have you tried Grsync? Grsync is just a GUI front end to rsync. If you prefer a GUI over a CLI, you might enjoy that application.

---

### Post by kevdog on 2007-05-24
I started with Edgy and really dont see any difference good or bad.  

As far as the rsync -- have you tried unison??  Its a program that uses rsync at the core, but does some preprocessing to make the transfer more efficient.  It is command line based, but has a GUI if you want it.  Its well supported and has a fairly good support forum.

---

### Post by Wight_Rhino on 2007-05-24
I went back to Edgy after installing it. Feisty didn't want to mount some of my drives, it's a registered bug, (medium priority)  but no solution as yet:(

No big deal, because (for me) so far Edgy is the Zenith of Ubuntu!

---

### Post by Dzenhax on 2007-05-24
> **Roasted said:**
> Thanks. As I read this, I was also reminded of gksu gedit. Duuur.

Is nano an ubuntu only command? I don't see it on the "linux command directory" web page I'm looking at.

Do you remember PICO?  I like it better than vi.  Anyway, nano is the Ubuntu replacement for PICO.  Maybe in Debian too, I don't know.

---

### Post by ramjet_1953 on 2007-05-24
There are still a few outstanding issues with Feisty.

Whether you want to install it depends upon whether these issues affect you.

Things that I have noticed on these forums are:

1. The new system of recognising all HDD's as scusi has problems with mounting and un-mounting USB devices.

2. There is a problem with VCD disks causing hard lock-ups when you mount them. (Not good for the Asian market)

3. Lots of people are having random lock-ups.

4. People are having problems with installing printers, even HP, where there were no problems in previous versions.

This is not an exhaustive list, but just a few that I have noticed and experienced personally. There are some workarounds for the mounting and unmounting issue, I believe.

However, as Edgy is working fine for me, except for my Logitech QuickCam for notebooks Pro,(which works fine in Dapper and Feisty) I'll stick with it until Feisty is a bit more refined.

Regards,
Roger 8-)

---

