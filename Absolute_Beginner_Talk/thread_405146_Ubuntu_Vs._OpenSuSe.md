---
title: "Ubuntu Vs. OpenSuSe"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-04-09
What are the pros/cons of Ubuntu and OpenSuSe? And what is the difference between them?

---

### Post by jem7v on 2007-04-09
[http://www.google.ca/search?q=ubuntu+vs+opensuse](http://www.google.ca/search?q=ubuntu+vs+opensuse) is probably a quicker way to find a wide variety of answers that won't be quite as Ubuntu-biased.

---

### Post by Fidelio on 2007-04-11
Well, presumably Peter has done that, which is what I did, because I'm trying to choose between them. And presumably, like me, he wants to hear the opinions of Ubuntu users on the subject. So go for It Ubuntu zealots!

For me, Suse seems slow (yeah, I know most people say its the oither way round) but it 'just works' more than ubuntu. I got streaming video, p2p and printing working on Suse, and I managed to get my 6 year old son's Gameboy emulator working. And superTux, which just comes up with a garbled screen for me on Ubuntu.

---

### Post by Bachstelze on 2007-04-11
SuSE's package management system is awful. That's a very good opportunity to learn building your stuff from source but I guess that's not what it's userbase wants to do :p

---

### Post by igknighted on 2007-04-11
> **Fidelio said:**
> Well, presumably Peter has done that, which is what I did, because I'm trying to choose between them. And presumably, like me, he wants to hear the opinions of Ubuntu users on the subject. So go for It Ubuntu zealots!

For me, Suse seems slow (yeah, I know most people say its the oither way round) but it 'just works' more than ubuntu. I got streaming video, p2p and printing working on Suse, and I managed to get my 6 year old son's Gameboy emulator working. And superTux, which just comes up with a garbled screen for me on Ubuntu.

When you did the install, did you just click the default?  While this installs a workable system, if you want a quicker, less bloated system click on the option to customize your install, you can remove a LOT of that stuff that you will never use.

---

### Post by igknighted on 2007-04-11
> **HymnToLife said:**
> SuSE's package management system is awful. That's a very good opportunity to learn building your stuff from source but I guess that's not what it's userbase wants to do :p

Yast is bad.  It tries to check dependencies so often that it is terribly slow to do anything, and the gui itself is very clumsy.  I recommend installing apt or smart on there to handle package install... quicker and more efficient.  You can even have synaptic, just like Ubuntu (although it still uses RPM packages, not Debian ones).

---

### Post by Fidelio on 2007-04-11
Suse* is* terribly slow to install. But everything I installed actually works, which is a feature I'd like so see in ubuntu.

---

### Post by igknighted on 2007-04-11
> **Fidelio said:**
> Suse* is* terribly slow to install. But everything I installed actually works, which is a feature I'd like so see in ubuntu.

The Suse installer is more complex than Ubuntu.  You have the option to install much more packages, and also to customize them to which exact ones you want.  In this regard, I would rather do a proper install with exactly what I want then a quick one and tweak it later.  You only install once, so who cares about the difference between 30min and an hour.

---

### Post by Bachstelze on 2007-04-11
Once again, that's something I don't agree with, and that's why I like Gentoo and FBSD so much (offtopic, I know, but not unrelated I guess). For me, an install must be quick - 15 minutes max. - ansd install *only* the most minimal system possible. I install additionnal software afterwards, building it from source to optimize it to my system and to my needs.

---

### Post by igknighted on 2007-04-11
> **HymnToLife said:**
> Once again, that's something I don't agree with, and that's why I like Gentoo and FBSD so much (offtopic, I know, but not unrelated I guess). For me, an install must be quick - 15 minutes max. - ansd install *only* the most minimal system possible. I install additionnal software afterwards, building it from source to optimize it to my system and to my needs.

:) I think now were outside the scope here... but I agree with you... I think every true linux user should keep a gentoo partition and know how to build it.  I try to, but in uni I really don't have time sometimes to worry about which use flags I need or what config file I accidentally overwrote with etc-update.  I stick with Fedora because I find it gives me a good mix of control and optimization of my system, up to date software, and maximum uptime without stuff breaking.  But in a perfect world it would be Gentoo FTW.

---

### Post by Bachstelze on 2007-04-11
(Sorry for the offtopic, guys)

This does not bother me as setting a USE flag on or off is just a matter of one command... Anyway, have you tried FBSD ?It's ports system is very similar to Gentoo's but it does not use USE flags. Instead, when you build a port for the firs time, you have a nice and pretty ncurses menu letting you choose the compilation options very easily without the need to edit anything.

---

### Post by bcmiller on 2007-04-11
I would recommend downloading and installing Ubuntu Ultimate Gamers Edition.

It has every game and emulator you could want pre installed and just about everything else you could want as well.

it's a DVD download just like openSUSE

[http://ubuntusoftware.info/ubuntu_ultimate_gamers/](http://ubuntusoftware.info/ubuntu_ultimate_gamers/)

I downloaded and installed that and I couldn't be happier.

---

### Post by igknighted on 2007-04-11
> **HymnToLife said:**
> (Sorry for the offtopic, guys)

This does not bother me as setting a USE flag on or off is just a matter of one command... Anyway, have you tried FBSD ?It's ports system is very similar to Gentoo's but it does not use USE flags. Instead, when you build a port for the firs time, you have a nice and pretty ncurses menu letting you choose the compilation options very easily without the need to edit anything.

I tried PC-BSD once, but that was on my old PC which used ATI, and there are no ATI drivers for BSD.  The xorg ones hated that card, so I was stuck with vesa so it didn't last.  Now that I am using nvidia graphics I think I'll give BSD another shot.

---

### Post by icechen1 on 2007-04-14
> **HymnToLife said:**
> SuSE's package management system is awful. That's a very good opportunity to learn building your stuff from source but I guess that's not what it's userbase wants to do :p

you can swich to SMART package management(is fast as synaptic).Actually,YAST package app is slow because of a bug in the system.

---

### Post by igknighted on 2007-04-14
> **HymnToLife said:**
> (Sorry for the offtopic, guys)

This does not bother me as setting a USE flag on or off is just a matter of one command... Anyway, have you tried FBSD ?It's ports system is very similar to Gentoo's but it does not use USE flags. Instead, when you build a port for the firs time, you have a nice and pretty ncurses menu letting you choose the compilation options very easily without the need to edit anything.

Ironically I installed DesktopBSD last night and then this thread gets dug up... I am loving DesktopBSD as well.  It really is like Gentoo, but much easier and way more user friendly.

---

### Post by alexlex on 2007-04-14
unfortunately no one can really tell you what is best they can only give you an opinion 

based on their system. It's nice to have someone tell what is best but it is just what works for them. i have tried openSUSE. fedora. freespire. xandros, but ubuntu ended up working for me best for what i needed it for. I could give you pros and cons but they simply would not apply to your system.

key things to remember when trying diff. distros

do not form a opinion based on other peoples opinions. find out for yourself
do not save any information that is terribly important to you on your new linux just incase it does not work out.
do not get to used to one way of doing things with a distro as they will change distro to distro.
Dont give up to soon...If you have a problem that you cant figure out dont just give up. look in forums or google it. most of the time you will find a way that will work for you.

---

### Post by AndyCooll on 2007-04-14
Did you have a look here at comments about OpenSuse by members of this forum?
[Other OS Talk > OpenSuse]("http://ubuntuforums.org/forumdisplay.php?f=164")

Indeed, there's even a thread covering the same ground as this one:   [ SuSE vs. Ubuntu]("http://ubuntuforums.org/showthread.php?t=229731")

:cool:

---

