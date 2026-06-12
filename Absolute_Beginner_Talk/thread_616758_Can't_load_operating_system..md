---
title: "Can't load operating system."
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by sykorunner on 2007-11-18
Help! In the middle of re-sizing a partition ubuntu froze! The mouse would move but it would not react to clicking or typing. Now the screen says that it can not load operating system (XP or ubuntu). Am I screwed or is there still hope?

---

### Post by Superdelphinus on 2007-11-18
i had this problem a few days ago and ended up creating a live cd and booted from that. then from in the live cd opened gparted and changed the boot flag to the right drive (it seems to get put on to the linux partition somewhere in the install. everything worked after that. It took me 4 days to work all that out i hope it's quicker for you!!

---

### Post by sykorunner on 2007-11-18
I'll try that. Thanks for your help!

---

### Post by sykorunner on 2007-11-18
It won't let me run gparted from the live cd!

---

### Post by Superdelphinus on 2007-11-18
do you have a usb stick of 2gb or more?

---

### Post by sykorunner on 2007-11-18
Alas, I haven't.

---

### Post by Superdelphinus on 2007-11-18
i had to go and buy one and then install a copy of mint linux live cd on it which then let me use gparted. i only had to this because my dvd drive is broken though so you might want to try and burn the mint live cd and try that

---

### Post by sykorunner on 2007-11-18
Ok. Thank you.

---

### Post by sykorunner on 2007-11-18
Now it's saying that I can't access it because I am not a root user.
Would this be easier if I just installed ubuntu to be the sole operating system (instead of having a dual boot system with XP as well)?

---

### Post by Superdelphinus on 2007-11-18
well if you don't want xp then yes! Someone will know how you do things as a root user if you ask - i'm just a newbie!

---

### Post by sykorunner on 2007-11-18
Haha! Ok, thanks for your help.

---

### Post by Severun on 2007-11-18
If you need to become root, you can type the password you entered when you installed.

Sans that, you can re-install.  Make sure you have the Desktop addition.  Then delete and re-create your Ubuntu partion.

Then re-install.  Be sure to write down any passwords you enter as you will need them later.

Don't give up!  sound like you're getting close.:guitar:

---

### Post by sykorunner on 2007-11-18
During installation it gets halfway and then says that it can't find some hardware or something rather. What does this mean? Will it still be possible to load XP again, because right now the only way I can use my computer is through the live cd.

---

### Post by sykorunner on 2007-11-19
Gar! The installer got 78% complete...and then it crashed...

---

### Post by MegaJim on 2007-11-19
Sounds like you may have some problems with your computer - I would advise running the memtest from the CD and if at all possible make sure that you have adequate cooling for your components - heat can cause hard crashes sometimes, although usually this type of behaviour is down to bad memory.

You should also tell the live CD to scan itself to make sure it hasn't been corrupted somehow (this and the memtest are on the livecd boot menu)

As a general word of advice I wouldn't use the Gparted included in the ubuntu distro's as it is usually out of date, you can either get a GParted LiveCD or Parted Magic (google if you are interested) for this sort of thing in future.

---

### Post by sykorunner on 2007-11-19
How long to memtests usually take? I started it 6 hours ago and it is still going on? Also, will this resolve any issues or will I have to fix them manually?

---

### Post by sykorunner on 2007-11-20
So I guess what I am going to do so I can get back to my life (being a college student and all) I will reinstall windows. After I can use my computer without the ubuntu live cd I can figure out what is wrong and fix it so as to be able to install ubuntu. If I'm not able to do so, then I guess I'll just have to wait until my next computer. Oh well. It'll be worth the wait. Thank you guys for all your help, and, of course, any further assistance is greatly appreciated!

---

