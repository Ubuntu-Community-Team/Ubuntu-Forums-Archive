---
title: "It's a very good place to start..."
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by NoNoNoMeBusy on 2008-04-21
Hello All,

I am new to these forums and to Linux in general. Bare with me while I explain my situation (I no doubt you have heard this before).

Recently (well a year ago) I upgraded to Windows Vista. I instantly disliked it but I wanted to give it a try so I tried it for 6 months. I found it frustrating, slow and a general pain in the neck. So I downgraded back to XP. However, in that brief time as a Vista user, Microsoft's operating system flaws became somehow a lot less bareable.

One thing I like about Mozilla's firefox as a web browser is complete customisation. I have it set up exactly how I like it. One of my friends said I should try linux, particularly ubuntu as it is to operating systems what firefox and opera are to net browsers.

That I guess is what I am looking for, however I wanted to get some advice before I even started to install ubuntu. The following is what I do with my PC on a regular basis (the list is from high priority to low):

Listen to music
World of Warcraft
Football Manager 2008
Internet Browsing
Email Checking
Some Minor Programming - generally windows based platforms in C#
I play some older games that aren't compatible with vista

the following is my spec:

AMD Athlon 64 6000+
2gb DDR2 Ram
GeForce 8800GTX Graphics Card
Soundblaster Audigy Card with 7.1 Speakers
3 750gb Hard Drives
DVD Write/Player

Now I know that from what I have read that Ubuntu is far from perfect, but if you have the know how and patience it can be close. I also don't expect you experts to spoon feed me information, half the fun will be discovering this out for myself but what I would like to know is if it is possible to do all the following and run ubuntu with the setup above? also if it is possible to dual boot with XP for a little while until I get used to Ubuntu and evaluate it's use to me. I am already a fan of clever open source applications that make my life easier I am quietly optimistic when thinking about Ubuntu. I plan to make it my project over the next few months.

I hope that you guys can help!

---

### Post by tzulberti on 2008-04-21
> 
Listen to music
World of Warcraft

Internet Browsing
Email Checking
Some Minor Programming - generally windows based platforms in C#
I play some older games that aren't compatible with vista


Listening music = Amarok, xmms, lots of options
Internet Browsing = Firefox, Opera, etc...
Email Checking = Evolution, Thunderbird, 
C# programing = not sure...
World Of Warcraft, Football Manager 2008, windows games: check wine site.([http://appdb.winehq.org/](http://appdb.winehq.org/))

Nevertheless, you would be able to choose ubuntu or Windows when you reinstall the PC

---

### Post by bartcramer on 2008-04-21
> Some Minor Programming - generally windows based platforms in C#

Well, on Ubuntu, your own-written Windows-based programs are obviously not going to work. Depends on what purpose it has, you might just as well turn to Linux programming (C, C++, etc). 

To me, it sounds that it is better for you to start out with a dual-boot, or try the Wubi installer that comes with Ubuntu 8.04, with which you can install Ubuntu as a program within Windows. 

Good luck!

---

### Post by lizzard on 2008-04-21
Football Manager 2008 works well with WINE.  You should follow the instructions [ here ](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5883)

---

### Post by ByteJuggler on 2008-04-21
> **NoNoNoMeBusy said:**
> 
Listen to music

Looots of options here, Amarok for example
> **NoNoNoMeBusy said:**
> 
World of Warcraft

I believe WoW [works under WINE]("http://appdb.winehq.org/appview.php?iAppId=1922") (a translation layer that allows you to run some Windows apps natively on Linux.) 
> **NoNoNoMeBusy said:**
> 
Football Manager 2008

This appears to [work as well]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=5883"), at least partially, under WINE.
> **NoNoNoMeBusy said:**
> 
Internet Browsing

Firefox, Opera, Konqueror, etc. etc.
> **NoNoNoMeBusy said:**
> 
Email Checking

Evolution, Thunderbird and several others...
> **NoNoNoMeBusy said:**
> 
Some Minor Programming - generally windows based platforms in C#

There's the ["mono" project]("http://www.mono-project.com/Main_Page") on Linux that has implemented a ECMA standards compliant C# compiler and .Net runtime, so you should still be able to do some C# development if you want.  If you need an IDE, there's ["SharpDevelop"]("http://www.icsharpcode.net/OpenSource/SD/Default.aspx"), which is itself a .Net app that runs on .Net framework or Mono. 
> **NoNoNoMeBusy said:**
> 
I play some older games that aren't compatible with vista

You'll have to check in the Wine AppDB to see which is supported.  If they are realy old/simple, you might be able to run them under QEmu (DOS emulation) possibly.

---

