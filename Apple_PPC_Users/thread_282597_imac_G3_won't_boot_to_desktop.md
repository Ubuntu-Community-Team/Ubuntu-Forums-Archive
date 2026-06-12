---
title: "imac G3 won't boot to desktop"
date: 2006-10-23
forum: Apple PPC Users
---

### Post by Atrio05 on 2006-10-23
ok well first of all i am using kubuntu breezy and all is well execpt the fact that when i start up it does ok until it trys to start the xserver it trys too but then it either goes to a screen asking for username or it goes to a list of things that it loaded and then hangs their so i push ctrl alit f1 and then log in and then i can start x i just want to know how i would go about fixing it so it loads right to the gui login screen or the desktop itself. any help would be greatly appreciated.

thank you!

---

### Post by bodycoach2 on 2006-10-23
Can you give us some more details about the hardware you have on the iMac? Memory? What speed is the processor?

In my experience, Xubuntu is a better choice for older iMacs. Ubuntu and Kubuntu were just too slow to really be 'useable'.

> **Atrio05 said:**
> ok well first of all i am using kubuntu breezy and all is well execpt the fact that when i start up it does ok until it trys to start the xserver it trys too but then it either goes to a screen asking for username or it goes to a list of things that it loaded and then hangs their so i push ctrl alit f1 and then log in and then i can start x i just want to know how i would go about fixing it so it loads right to the gui login screen or the desktop itself. any help would be greatly appreciated.

thank you!

---

### Post by madmetal on 2006-10-23
i agree that xubuntu runs better(and smoother) on G3.
will this thread give you a hint?
[http://www.ubuntuforums.org/showthread.php?t=75604](http://www.ubuntuforums.org/showthread.php?t=75604)
:-k

---

### Post by DirtDawg on 2006-10-24
Not to gang up on atrio05, but I agree. Try Xubuntu.

---

### Post by Atrio05 on 2006-10-24
problem is fellas is that i tryed xubuntu because i thought the same thing you did, that it would run smoother and faster but the fact is at first the live cd wouldn't load then when i got it to boot up the live installer would never load to install xubuntu so i gave up on it.

---

### Post by Atrio05 on 2006-10-24
oh and the link given further up doesn't really help me because my x server works after i drop to a terminal and login and type startx

it just won't load x when booting up.

specs: 

memory - 128mb
video memory - 16mb
video card - ati 128 rage i think
processor - 400Mhz
HDD - 10Gb

well thats all i can remember right now i hope this helps you out so you can help me! ;)

---

### Post by DirtDawg on 2006-10-24
> **Atrio05 said:**
> problem is fellas is that i tryed xubuntu because i thought the same thing you did, that it would run smoother and faster but the fact is at first the live cd wouldn't load then when i got it to boot up the live installer would never load to install xubuntu so i gave up on it.

The live cd/live installer probably didn't work too well because of insufficiant RAM. The alternate install CD would've been a much better bet. 

Anyways, I'm not sure how to fix the X problem. Maybe you could have it start on bootup through the setup>sessions>'startup programs' menu?  It's a hell of a hack, but it might work. I hope someone else has a better idea.

---

### Post by hulleye on 2006-10-28
Quick question before you try out the other stuff. What's your system clock set at? One thing I discovered was that on my iBook G3, the CMOS battery is dead, so whenever my main battery runs out, the system resets the clock to Jan 1903 or something like that. Nautilus for some reason doesn't like this and refuses to load up. I would get till the login screen, but just a blank screen for a desktop.


A simple solution was to plug in the main power, plug into an internet connection via ethernet (updates the system clock using a network server) and boot it up again. Worked fine as long as my battery retained its charge.

---

### Post by daWabbit on 2006-10-28
This is probably 'way off the mark, but I thought I should tell you about it, just in case it helps. Please excuse me if I am wasting your time.

I have had this problem with G4 iMac and various G3, G4 and G5 desktops and notebooks. One thing I found is that at times a machine will not boot to X unless it has completed the time synch with the Ubuntu time server. I have not been able to find the exact cause, but to fix it temporarily all I need to do is boot to a live internet connection on a LAN, either wireless or wired.

I have no idea why this happens, but I get the same thing you get and this booting when the machine can access the time server really does fix a lot of Breezy and Dapper problems. I also had this happen once with XUbuntu on a laptop.

---

