---
title: "Installing linux on an old PC"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by Disposable Arts on 2006-09-20
I have this old PC that I got working again and somehow seem to be running windows98.  I was trying to install ubuntu on it which was going ok, till it halted and said it was out of memory….which I really don’t get since it has windows98…anyways, do I have any more options here to get ubuntu or any linux based OS on the comp?

CPU=6x86l-pr166+
CPU Speed=133MHz
Ram=24576
HD=2411(not 100% certain on that )

---

### Post by nts on 2006-09-20
you would probably be better off with a less resource hungry distro, like DSL or maybe just with a less pretty window manager...

---

### Post by Towncivilian on 2006-09-20
24MB of RAM? Bleh.

DSL would be good. Even Xubuntu is too heavy for 24MB of RAM.

---

### Post by Brunellus on 2006-09-20
[DamnSmallLinux](http://www.damnsmalllinux.org) is pretty much your best hope.

---

### Post by comppsyco on 2006-09-20
If you're feeling really hard core, you could try doing Linux From Scratch, where you build your own distro from scratch. It is, however, very technical.
Just type that into google and you'll find it.

---

### Post by Disposable Arts on 2006-09-20
Wow you guys are fast...but yea, i'll give that DSL a try out...being a noob to linux isn't gonna be a major problem is it? i see command lines:sad:

---

### Post by Brunellus on 2006-09-21
> **Disposable Arts said:**
> Wow you guys are fast...but yea, i'll give that DSL a try out...being a noob to linux isn't gonna be a major problem is it? i see command lines:sad:
Of course you see command lines.  If you had gotten that machine brand new, in 1995, your OS options realistically would have been MS-DOS or Windows 95--both OSes where the shell made more than a cameo appearance.

DSL isn't totally command-line driven, but it is definitely NOT Ubuntu.  The two projects have different aims:  while Ubuntu aims to provide a good, modern, usable desktop on reasonably-current equipment, DSL aims to be the most functional OS that you can fit in 50 MB.  Design like that involves compromises.  You can write either the *Mahabarata* or a haiku, but not both.

---

### Post by anaconda on 2006-09-21
As a matter of fact. DSL is a good distro to learn linux. A bit more difficult than ubuntu, but almost every command you learn will work in all linux distributions..

Puppy-linux is as light as DSL, but easier to use. 
(I like DSL more, but puppy is really much easier.)

And I think installing ubuntu to your computer would be possible. But it would be sloooow. I have read that you can enable swap (=virtual memory) in early phase of the installer...

---

### Post by anaconda on 2006-09-21
And if buing more memory to your computer is an option, I think it can be bought really cheaply..

Example: Just a couple of days ago I was in a secondhand PC-shop, and they had a BIG box full of old memory-chips. 1&#8364; /each...

---

### Post by Brunellus on 2006-09-21
If the goal is not necessarily "learning linux," though.  

Ubuntu's alternate CD could probably be made to work, but a 'standard' ubuntu installation would be unworkable.  You'd have to do a minimal (i.e., "server") install and add packages manually, probably along the lines of [these instructions](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by xyz on 2006-09-21
Also PuppyLinux:
[http://www.puppylinux.com/download/downpage.htm](http://www.puppylinux.com/download/downpage.htm)

---

### Post by deadgobby on 2006-09-21
There is one that can run a 486 with 16 megs of ram
[http://www.delilinux.de/](http://www.delilinux.de/)

---

### Post by K.Mandla on 2006-09-21
I'm afraid with only 24Mb of RAM, you're more or less confined to minidistros like DSL or Puppy linux. 

It's the installer that's the limiting factor for you. Ubuntu's installer goes berzerk if you try to run it on less than 36Mb. (I've [tried]("http://www.ubuntuforums.org/showthread.php?t=259901").) If you can put more memory into it, you could get it to work ... but to be honest, the results aren't really worth the time and effort.

There's nothing wrong with DSL or Puppy, though. Both of those distros are intended for lightweight machines, and they do an excellent job. Give them a try. :D

> **deadgobby said:**
> There is one that can run a 486 with 16 megs of ram
[http://www.delilinux.de/](http://www.delilinux.de/)
Hey wow, with Xorg 7.1 ... :-k

---

### Post by bobpur on 2006-09-21
I agree with Anaconda. Upgrades for a computer this old should be plentiful and cheap or free. 
Find out how big of a CPU your motherboard supports and keep a lookout for one. Also memory and harddrives.
I've found old computers at yard sales or just sitting around being used as doorstops. Don't be afraid to ask about them. once stripped they can be worth more as parts than what they were whole.
Also,you may be short on memory or CPU speed for Dapper, but what about Breezy (v 5.10) or Hoary (v 5.04). Both use less system resources than Dapper (v 6.06).

---

### Post by sefs on 2006-10-02
which of these two (puppy or damnsmall) will allow installation like ubuntu.   That is ... download a deb file manually or via "apt-get?"

I am in need of something that can boot from a USB key drive and that I can install BIND into.

---

### Post by K.Mandla on 2006-10-02
I seem to remember DSL sporting a tweak that allows it to use Debian (or at least Debian-style) archives. ... It's been a very long time since I used it though, so I'm not really sure how it works -- or for that matter, how to get it working. ;)

---

