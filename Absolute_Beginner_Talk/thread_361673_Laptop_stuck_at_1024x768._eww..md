---
title: "Laptop stuck at 1024x768. eww."
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by lunchbox_1973 on 2007-02-14
Hi. I have a Dell Inspiron 1300 with integrated graphics - Intel 915. The native screen resolution for this machine is 1280 x 768 but there is only one option in the Ubuntu display settings - 1024 x 768. The OS seems to be recognizing the hardware ok but obviously something is wrong here.

I'm a little ignorant as far as how Linux and hardware work with each other. Do I need to find a driver that will fix this?

I can't really find anything at either the Intel or Dell websites.

Any advice is appreciated.

---

### Post by annda on 2007-02-14
you might need to install 915resolution package. find it in synaptic.

---

### Post by lunchbox_1973 on 2007-02-14
Thanks but you're going to have to dumb it down just a little bit more. :confused: 

Explain what these two things are a little more. What is synaptic, a web site?

---

### Post by annda on 2007-02-14
synaptic is your friend ;-) it is a program that handles software downloads: it gives you a list of all compatible packages/programs. you can find it your menus: system / administration / synaptic package manager. it's great once you get used to it.

when you hit the search button and type 915 it will show the program/driver/package you need to install. right-click on it and select install. then hit the apply button and it will be installed.

i have a different video driver and never used intel 915 so you might have to search the forums for 915resolution if something doesn't work.

good luck!

---

### Post by veloce on 2007-02-14
Synaptic is a graphical software installation tool. It can be found under system and its full name is Synaptic Package Manager.

With Synaptic package manager you want to install the package (software) called 915resolution.  Simply, this software allows intel graphics cards to work at higher resolutions. 

It will probably work properly after installation - easiest to reboot (or search on this forum for 915resolution to find my other instructions for using it)

---

### Post by veloce on 2007-02-14
Aah, two replies for the price of one, sorry for the overlap.

---

### Post by lunchbox_1973 on 2007-02-14
I searched 915resolution, 915, resolution. Absolutely nothing comes up. Is it because I'm using the live cd? (not installing until I know I can fix this AND my wireless card which is a different story)

---

### Post by pissedoffdude on 2007-02-14
> **lunchbox_1973 said:**
> I searched 915resolution, 915, resolution. Absolutely nothing comes up. Is it because I'm using the live cd? (not installing until I know I can fix this AND my wireless card which is a different story)

Your gonna need to enable the extra repositories.  Go to System>administration>software sources, and make sure u check multiverse and universe.  Then it should ask to reload.  After that try searching for it in synaptic.

---

### Post by rbprogrammer on 2007-02-14
> **lunchbox_1973 said:**
> I searched 915resolution, 915, resolution. Absolutely nothing comes up. Is it because I'm using the live cd? (not installing until I know I can fix this AND my wireless card which is a different story)

i have a dell inspiron e1505 which as far as i know has the same graphics chip from Intel, well i insalled *915resolution* and it definitely works.

---

### Post by veloce on 2007-02-14
> **lunchbox_1973 said:**
> I searched 915resolution, 915, resolution. Absolutely nothing comes up. Is it because I'm using the live cd? (not installing until I know I can fix this AND my wireless card which is a different story)

Oh, the live CD. Sigh.  You're lucky to be getting 1024x768!

You may be setting up a Catch 22.  Won't install without knowing it will work, it won't work unless you install.

I can assure you that with 915resolution installed on your machine, you will get 1280x768 (if you can get that under windows).

my suggestion is to check out hardware compatibility of your wireless card then do a proper install.  (Preferably formatting away windows!) BTW, the wireless card in my dell laptop worked out of the box.

---

### Post by lunchbox_1973 on 2007-02-15
Thanks for all the help you guys. I'm glad I found this community instead of trying out this stuff alone. That's what happened last time I dipped my toe into the Linux water. I eventually got frustrated and gave up.

I think I will do a full install today and get a dual boot going. Since I don't play games on my laptop my goal is to use Linux on it 90% of the time and see if I can do most of my computing on it. I don't really have a strong reason, I'm fine with windows, it's just my inner computer geek calling out to me for a new challenge.

So yeah, I'll install it and try to get the 915resolution deal to work. If I can get that going it will get me over the first hump - can't enjoy your widescreen at 1024x768. Looks like crapola.

Wish me luck.
LB

:guitar:

---

### Post by lunchbox_1973 on 2007-02-15
> **pissedoffdude said:**
> Your gonna need to enable the extra repositories.  Go to System>administration>software sources, and make sure u check multiverse and universe.  Then it should ask to reload.  After that try searching for it in synaptic.

Guys, I still can't find it! Do you see it if you search? What in the $&^# am I doing wrong??

---

