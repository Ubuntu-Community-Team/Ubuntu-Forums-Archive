---
title: "What open source DVD rippers can I get?"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by jkbritt on 2006-05-06
I was just wondering what some free, EASY TO USE, dvd rip/burn software was, and where I could get it. Thanks.

---

### Post by JoshHendo on 2006-05-06
dvd::rip may be what you are looking for.

I can't remember if it is open source or not, though it probably is :P

---

### Post by ds[de] on 2006-05-06
From the official dvd::rip homepage:
"dvd::rip itself is licensed under GPL", so yes, it's open source.

---

### Post by jkbritt on 2006-05-06
ok, i downloaded it... but how do I install it?

---

### Post by TheFourElements on 2006-05-06
just get it off synaptic

---

### Post by jkbritt on 2006-05-06
what is synaptic? This is only my second day ever using linux.

---

### Post by openmind on 2006-05-06
Just to get an exact iso from the whole disc I use;

```
dd if=/dev/dvd of=~/dvd.iso
``` 
Quick and easy.:D

Edit: Sorry I just got your post about being new to Linux. Just to explain a little Synaptic is your main way of installing Apps, you should find it under *System>admin*. Do a search for, say "DVD" and check the box of any that interest you, Then hit "apply" and it will install your app.

My way of getting an image from a disc is done in the terminal, but baby steps for now, ...................baby steps:D

---

### Post by TheFourElements on 2006-05-06
synaptic is the package manager for debian/ubuntu.

from a terminal type

1) sudo su
2)[enter password]
3)synaptic

synaptic itself is pretty straightforward

---

### Post by eddie303 on 2006-05-06
Click the Applications menu, then Add/remove programs, then go to advanced mode, and that is Synaptic. There you can search for the package, it will download and install it for you.

---

### Post by nanotube on 2006-05-06
[QUOTE=TheFourElements]synaptic is the package manager for debian/ubuntu.

from a terminal type

1) sudo su
2)[enter password]
3)synaptic

synaptic itself is pretty straightforward[/QUOTE]
ehrm, sorry, but that is really not the way to do that. instead, you should simply
```
gksudo synaptic
```
see [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) for more info about the sudo model in ubuntu.
or, of course, you can just select the synaptic package manager from System>Administration>Synaptic menu - which launches synaptic with sudo.

oh and by the way, **jkbritt,** for a nice tutorial on using synaptic (as well as other ways to install software), check out the second link in my sig.

---

### Post by TheFourElements on 2006-05-06
my way works too!

---

### Post by jkbritt on 2006-05-07
Alright, once synaptic finishes, where do I go to open these programs? I remember getting WINE like this somehow, and I cant find where it is either.

---

### Post by manicka on 2006-05-07
Wine isn't a program you open and look at. you use it to run other programs. You can however look at its settings by running the command winecfg

---

### Post by manicka on 2006-05-07
DVD::RIP should be in Application --> Sound and Video


K9copy is a program that may interest you as well. You'll probably need extra repositories to install it though
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

---

### Post by richbarna on 2006-05-07
Hi jkbrit, 
There is a small program that will search for programs for you, and put them on a Debian link on the start menu.
You need to open the console ant type :-
> sudo apt-get install kappfinder
Once it is installed, follow these instructions :-
> Press Alt + F2, The "run" dialogue box will appear. Type kappfinder and the program will open.

---

### Post by TheFourElements on 2006-05-07
[QUOTE=jkbritt]Alright, once synaptic finishes, where do I go to open these programs? I remember getting WINE like this somehow, and I cant find where it is either.[/QUOTE]

from the command line type "dvdrip" or just type "dvd" and use tab completion. (I'm sorry if all my advice is for the command line. I use windowmaker and completely gutted the F12 menu)

---

### Post by nanotube on 2006-05-07
[QUOTE=TheFourElements]my way works too![/QUOTE]
well, yes, it works, true. :) but what it also does is leave a persistent root shell open even after you are done with synaptic. the whole point behind using sudo is to avoid that, and only have privilege escalation on "as-needed" basis. so while your way is just as functional, it kinda bypasses the whole point of using sudo...

---

### Post by CameronCalver on 2006-05-17
When you get into dvd rip how do you actually rip something can some1 give me some screen shots

---

