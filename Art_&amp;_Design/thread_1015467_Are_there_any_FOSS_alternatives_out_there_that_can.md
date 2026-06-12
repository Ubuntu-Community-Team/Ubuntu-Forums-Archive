---
title: "Are there any FOSS alternatives out there that can read .fla files?"
date: 2008-12-18
forum: Art &amp; Design
---

### Post by AFarris01 on 2008-12-18
I don't know where else to ask this, but i was just wondering.

i was cleaning a bunch of old crap off my hard drive today, and i found an old archive of flash projects i did in my high school digital graphics class... and remembering all the stuff i had been working on at the time, i was wanting to try and resume some of my old projects.  

unfortunately upon searching the repos, i couldn't locate any programs that could read the .fla files.  So basically, i was wondering, are there even any FOSS programs that are capable of doing this? i appreciate any suggestions!

---

### Post by durand on 2008-12-19
I've tried and failed to find any :( I hope someone here proves me wrong!

---

### Post by smartboyathome on 2008-12-19
There's [F4L]("http://f4l.sourceforge.net/"), but I thought it was pretty much abandoned.

---

### Post by AFarris01 on 2008-12-20
Yeah, i actually found F4L on sourceforge, but i'd say the project is most definitely dead (last updated in 2006 if i remember right), but i tried anyway, and was met with the makefile not working... so i converted it to a MonoDevelop project in an attempt to get something working :)

the only other alternatives i found were just for making .swf files, rather than reading .fla files... which isnt really useful to me

i hope somebody else has a better solution... otherwise im going to read up more on c++ and try to repair F4L

---

### Post by Izek on 2008-12-20
> **AFarris01 said:**
> i hope somebody else has a better solution... otherwise im going to read up more on c++ and try to repair F4L

If you repair F4L, please report back here, we seriously need a working free flash editor on linux.

---

### Post by PoHandle on 2008-12-20
I believe Macromedia Flash 8 works under wine.  If you have a copy of that, you may want to try installing and running it with wine.  I'll be attempting to do that soon to keep all of my web development on one OS.

---

### Post by Sand &amp; Mercury on 2008-12-20
> **PoHandle said:**
> I believe Macromedia Flash 8 works under wine.  If you have a copy of that, you may want to try installing and running it with wine.  I'll be attempting to do that soon to keep all of my web development on one OS.
Yeah, it does. I use it myself for web development.

---

### Post by AFarris01 on 2008-12-21
unfortunately, i only have a student copy of flash mx 2004 left from my class, and it does not want to run under wine... already tried. :(

on the plus side, i have begun fiddling with trying to get F4L to compile right, so i can see how well it works in its current state... down to only 230 errors :/

I'll certainly post here if i can actually get the thing working... im also going to contact the original author to see if he cares about the project any more, but unfortunately it may have to wait a while 'cause i'm going to be helping my dad rebuild their living room over christmas...

Ill keep everybody posted!

---

### Post by AFarris01 on 2009-01-05
Well, i've finally gotten some time to fiddle with the F4L code, and i've trimmed the error count down to 62 :D

maybe ill actually be able to run it one of these days! :popcorn:

just wanted to update... I'll surely post a tarball up here if i actually get it to run

---

### Post by durand on 2009-01-05
Great! I'd like to know the outcome of this. I didn't know that F4L was much of a program rather than just a library.

---

### Post by Izek on 2009-01-05
> **AFarris01 said:**
> just wanted to update... I'll surely post a tarball up here if i actually get it to run

Maybe someone can make a deb and rpm of it too, since I'm no good at compiling from source.

---

