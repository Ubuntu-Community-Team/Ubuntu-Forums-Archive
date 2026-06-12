---
title: "Can it do what I want?"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by cyanide taco on 2007-08-23
I'm a student in high school entering a programming class (c++) and I was wondering if Ubuntu would be a good enviroment for programming. Also, what is a decent system to run it on and program efficently?

---

### Post by st33med on 2007-08-23
Basically, yes. It is good for programming. You just need to download the proper things to edit C++, and I'm not sure what that would be.

The best system is pretty much anything with memory above 192 MB, and you might want to avoid downloading the 64-bit version because not much works with it, e.g., Flash.

---

### Post by K.Mandla on 2007-08-23
Just about any computer is a decent machine, depending on how you build your system. 

If you use the default Ubuntu system, I'd probably recommend something faster than 1.6Ghz, with an Nvidia card. Of course, it's possible to do the same job with less, but that's up to you. I use a 1Ghz machine, but I strip out a lot that slows things down. Plenty of people use even slower machines than that.

---

### Post by tetrahedr0n on 2007-08-23
Yes it can!

The gcc/g++ compilers are actually a standard in the computer science world. (My university classes only use these compilers actually, and this is a university with one of the best cs departments in the world).

Your ubuntu install will have the compilers preinstalled. To try something simple, you only need the command line

g++ helloworld.cpp -o helloworld

and you'll have your app.

Of course, you're going to want to pick an editor. The default gnome editor, gedit, is OK for programming. It includes C and C++ highliting whihc is about all you need. When you get better, you'll probably pick between the more advanced editors, vi and emacs, which really are superior but a bit more complex.

---

### Post by cyanide taco on 2007-08-23
Ok cool, so my computer will run it, but one problem comes up. My graphics card is an ATI Radeon chipset. Anyone know of any problems with an Asus EAX1600 Pro 512mb DDR2?

---

### Post by K.Mandla on 2007-08-23
[geany]("http://packages.ubuntu.com/feisty/devel/geany") is a pretty good editor, and is aimed at programming and such. Has syntax coloring, can nested code, has embedded pseudoterminals and so forth. You might take a look at that one, after you get your system up and running.

---

### Post by Aishiko on 2007-08-23
> **cyanide taco said:**
> Ok cool, so my computer will run it, but one problem comes up. My graphics card is an ATI Radeon chipset. Anyone know of any problems with an Asus EAX1600 Pro 512mb DDR2?
check out the ATI sticky in the beginner talk section and see if it's listed also doing a forum serach for your video card will get yoyu the answers much faster.

---

### Post by K.Mandla on 2007-08-23
> **cyanide taco said:**
> Ok cool, so my computer will run it, but one problem comes up. My graphics card is an ATI Radeon chipset. Anyone know of any problems with an Asus EAX1600 Pro 512mb DDR2?
Chances are it will work; whether or not you need accelerated video is a different question. Your best bet is to search the forums and see if there are any posts that mention it, and if anyone had problems or how they worked around them.

But if you're only looking for a straightforward desktop environment for coding, and you don't need high-speed video acceleration for the newest games and so forth, then you're most definitely okay.

---

### Post by cyanide taco on 2007-08-23
Okay i was just wonderng if it would have any huge issues or something. I wont be using any heavy graphical programs (save that for winxp and oblivion:))

---

### Post by asmoore82 on 2007-08-23
> **tetrahedr0n said:**
> Yes it can!

The gcc/g++ compilers are actually a standard in the computer science world. (My university classes only use these compilers actually, and this is a university with one of the best cs departments in the world).

**Your ubuntu install will have the compilers preinstalled**. To try something simple, you only need the command line

g++ helloworld.cpp -o helloworld

and you'll have your app.

Of course, you're going to want to pick an editor. The default gnome editor, gedit, is OK for programming. It includes C and C++ highliting whihc is about all you need. When you get better, you'll probably pick between the more advanced editors, vi and emacs, which really are superior but a bit more complex.

everything is correct except the bold part ...
from a fresh Ubuntu desktop install you will need to add these packages ...

gcc, g++, and likely build-essential

---

### Post by zeehat on 2007-08-23
I have an ATI X800, and Ubuntu picked it up, and runs it well.

---

