---
title: "Firefox crashes on input (but reading is ok). What have I done?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by birkwood on 2008-02-26
I was trying to connect a new ipod nano 3rd gen (still unsuccessful) to my computer (running freebird) by entering a script of a web page into the shell terminal.
I am only just learning what I should and shouldn't attempt.. but whatever this thing was it made a lot of updates to Open Office and also apparently firefox thunderbird. 
It used to run perfectly, but now I can only open it up to read. As soon as try to type anything (usernames, passwords, posts etc) it crashes immediately.

This is what I put into the terminal..

```
sudo -i
cp /etc/apt/sources.list /etc/apt/sources.list.tmp
echo deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse >> /etc/apt/sources.list
apt-get update
aptitude install libgpod3 libgpod-common

aptitude install amarok
```

After this it said something about not being able to find the solution in the alloted time, Retry Y/N.  After retry didn't work I pressed N and quit the terminal.

Have I done something stupid? I'm very new to all this.

Thank you!!

---

### Post by Vadi on 2008-02-26
I think you either used the instructions for the wrong ubuntu version, or you're running the next version of ubuntu (which is still being worked on, and should not be used for everyday things).

In the terminal, do "uname -a", what does it say?

---

### Post by birkwood on 2008-02-27
Thanks for the reply!
It says...Linux Jesus 2.6.20-16-lowlatency #1 SMP PREEMPT Wed Nov 7 10:52:05 PST 2007 i686 GNU/Linux

Is that the info you needed?

---

### Post by Vadi on 2008-02-27
Sorry, no (I was mistaken). Can you you "lsb_release -a" instead? That one will do what we need (ie, tell which version of Ubuntu have you got)

---

### Post by birkwood on 2008-02-27
Here you go..
I just noticed that Youtube videos won't play any more either, even in Konquerer - the web page comes up fine but where the video should be is just a grey box with no buttons.

```
LSB Version:    core-2.0-noarch:core-3.0-noarch:core-3.1-noarch:core-2.0-ia32:core-3.0-ia32:core-3.1-ia32:cxx-2.0-noarch:cxx-3.0-noarch:cxx-3.1-noarch:cxx-2.0-ia32:cxx-3.0-ia32:cxx-3.1-ia32:graphics-2.0-noarch:graphics-3.0-noarch:graphics-3.1-noarch:graphics-2.0-ia32:graphics-3.0-ia32:graphics-3.1-ia32:desktop-3.1-noarch:desktop-3.1-ia32
Distributor ID: Freespire
Description:    Freespire 2.0
Release:        2.0
Codename:       skipjack-feisty
```

---

### Post by Vadi on 2008-02-27
Oh. You aren't on Ubuntu then - you're on Freespire. Try asking for help on their forums, since I think you'll get better results there:

[http://forum.freespire.org/](http://forum.freespire.org/)

(sorry I can't help you!)

---

### Post by birkwood on 2008-02-27
oh no, really? I thought freespire was ubuntu. All these different names are sooo confusing. I'll try the freespire forums.
Thanks for trying to help me out anyway (and for the link), very much appreciated!

---

### Post by Vadi on 2008-02-27
Freespire is Linux, and Ubuntu is Linux. But Freespire isn't Ubuntu - and you can get Ubuntu here: [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

(sorry for the confusion - but things will get cleared up later)

---

### Post by birkwood on 2008-03-08
Just in case anyone else suffers this (I don't think it's necessarily a freespire thing) - I downloaded the latest version of firefox and now it works fine again, no more crashing. I still can't play youtube videos or anything like that however. It says I need to download latest Adobe flash player/flash plugins, but when I try to do that I get a malformed file error.

But installing a new version of firefox repaired the crashing problem anyway.

---

### Post by Vadi on 2008-03-08
See if you can install flash via freespire's repositories, that would be the easiest way (on ubuntu at least).

---

