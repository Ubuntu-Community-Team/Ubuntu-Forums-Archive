---
title: "Compiz"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by cdodger55 on 2007-11-10
I'm really green to linux but hate windows with a passion so i'm going to finally give it my all. I received a 64 bit 7.10 install of ubuntu. In stalled the os. Now would like to start to customize my comp to fit me. I need some help getting  going. I have a Asus A8N-SLI Deluxe, AMD 3800 X2, nvidia 6200 turbo video card, 2, 1 gig kingston sticks. I have a lot of things that i would like to solve. Compiz, g15 keyboard g keys, g5 mouse, and how to install ETQW, so I have something to do while i'm not playing with ubuntu. any help would be great. thanks. p.s

---

### Post by deep.tinker77 on 2007-11-10
Here are the official instructions for Quake Wars. I don't know much about the other things though.

[http://zerowing.idsoftware.com/linux/etqw/](http://zerowing.idsoftware.com/linux/etqw/)

Good luck.

---

### Post by Maestro23 on 2007-11-10
To enable you Compiz on Gutsy: [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by cdodger55 on 2007-11-10
Thanks for the replies im gonna start on it right now. thanks

---

### Post by Maestro23 on 2007-11-10
> **cdodger55 said:**
> Thanks for the replies im gonna start on it right now. thanks

Here's as good blog on Compiz as well: [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by Vadi on 2007-11-10
> **Maestro23 said:**
> To enable you Compiz on Gutsy: [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

Do **not** follow those instructions, because they are clearly marked as "Fiesty". Compiz changed a lot in Gutsy, and you might get unexpected results when following that.

Instead, go to system - preferences - appearance - visual effects. That's a very simple settings manager for compiz, if you want a better one, click here to get it ([click]("apt:compizconfig-settings-manager")), and then it'll appear in system - preferences - Advanced Desktop Effects Settings

---

### Post by Maestro23 on 2007-11-10
> **Vadi said:**
> Do **not** follow those instructions, because they are clearly marked as "Fiesty". Compiz changed a lot in Gutsy, and you might get unexpected results when following that.

Instead, go to system - preferences - appearance - visual effects. That's a very simple settings manager for compiz, if you want a better one, click here to get it ([click]("apt:compizconfig-settings-manager")), and then it'll appear in system - preferences - Advanced Desktop Effects Settings

Thanks for that heads-up to the OP.

---

### Post by cdodger55 on 2007-11-10
compiz up and running thanks

---

### Post by Vadi on 2007-11-10
Cool. What about the keyboard and the mouse you mentioned?

---

### Post by Maestro23 on 2007-11-10
> **cdodger55 said:**
> compiz up and running thanks

Found this for you keyboard: [https://help.ubuntu.com/community/LogitechG15?highlight=%28G15%29](https://help.ubuntu.com/community/LogitechG15?highlight=%28G15%29)

---

### Post by cdodger55 on 2007-11-12
Sorry about not posting in the last couple days. I have got the compiz to work but have not got the etqw or the key board to work yet. I tried the whole etqw thing but kept gettting the same error when i tried to do the install. the error was got bad batch file. so i downloaded a different one and had got the same error. Dont know if it was me or the actual down load. As for the keyboard I've tried this before and the problem was with tar files. I can do debs just fine but have know idea about tars. please have some answers for me lol. Thanks

---

### Post by Maestro23 on 2007-11-12
> **cdodger55 said:**
> Sorry about not posting in the last couple days. I have got the compiz to work but have not got the etqw or the key board to work yet. I tried the whole etqw thing but kept gettting the same error when i tried to do the install. the error was got bad batch file. so i downloaded a different one and had got the same error. Dont know if it was me or the actual down load. As for the keyboard I've tried this before and the problem was with tar files. I can do debs just fine but have know idea about tars. please have some answers for me lol. Thanks

.tar files: [http://www.psychocats.net/ubuntu/installingsoftware#source](http://www.psychocats.net/ubuntu/installingsoftware#source)
*After you extract the tarball, there should be a README/INSTALL document w/Instructions.

For the ETQW.run file:

Must be in the directory you downloaded the file to.  If on your Desktop:

> cd ~/Desktop

sudo chmod +x ETQW-demo-client-1.1-full.r5.x86.run

./ETQW-demo-client-1.1-full.r5.x86.run

---

### Post by Mattaus on 2007-11-15
Hi, 

I've recently got Gutsy running on my PC and I am having problems getting compiz to run. I've basically tried every guide/step/suggestion in this thread and none of it works. Any references to the compiz manager dont work (the link is always dead) and for some reason I can't even enable the basic desktop effects. I'm running a Q6600, 4g RAM and a 2900XT which may be the problem....any suggestions as to why it wont work?

I did the whole alt-f2 thing then ran compiz --reload. The screen flashed and that was it. I then went alt-f2 and then tried to run ccsm, but it just says that cannot be found!

So yeah, any suggestions or help would be great. Cheers.

---

### Post by Vadi on 2007-11-15
You need to install ccsm first before you can run it! Do

**sudo apt-get install compizconfig-settings-manager**

To get it.

Also, I think you don't have 3d acceleration enabled in your system - do **compiz --replace** in the terminal, and tell us what it says.

---

### Post by Mattaus on 2007-11-15
Damnit!

Um, I did compiz --replace in the terminal and got this back:

[I]Checking for Xgl: not present.
NO whitelisted driver found
aborting and using fallback: /usr/bin/metacity[/I]

oh, and when I did the apt-get command I got this back:

[I]Reading package lists... Done
Building dependancy tree
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager[/I]

Im having problems installign anything, even through the add/remove programs functionaltiy. I've got another thread about that but somehow I feel it may be related :(

[http://ubuntuforums.org/showthread.php?p=3775479#post3775479](http://ubuntuforums.org/showthread.php?p=3775479#post3775479)

Hope that tells you guys something...thanks for replying so far!

---

### Post by DutyDuty on 2007-11-15
To install Compiz Settings, the code it this: ```
sudo-apt-get install ccsm
```

---

### Post by Mattaus on 2007-11-16
Right, I had to install the 64 bit version of Ubuntu to get anything working but that is now going. I also have the advanced desktop effects setting manager installed, but everything I apply doesn't seem to work. When I go to System -> Preferences -> Appearance -> Visual Effects and then apply the custom effects it just says that they could not be applied. Same for the normal and extra effects.

Could it be my graphics card? Any drivers or something out there I should try and install? I also noticed (maybe related) that I can set a wide screen resolution for my PC. 

If I need to start a new thread I can, I just thought I'd pop this in here as its along the same lines.

Cheers.

---

### Post by Vadi on 2007-11-16
Yes, it Compiz cannot start, it's something wrong with you graphics card drivers (it just falls back to the Metacity theme when it can't start).

What is the make of your card?

---

### Post by Mattaus on 2007-11-16
Its a Radeoan 2900XT...so pretty new. Too new maybe?

---

