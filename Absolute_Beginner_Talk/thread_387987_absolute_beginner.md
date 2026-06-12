---
title: "absolute beginner"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by mig96 on 2007-03-18
I recently tried to start up the ubuntu live cd and kubuntu.

I am using windows vista & xp dual boot right now and abslute noob at ubuntu...

so ubuntu gives me an error that the "x server" won't start up and kubuntu gives me a console,cant's switch to advertised gui.

help :lolflag:

---

### Post by BarfBag on 2007-03-18
Is this a fresh install, or have you had it for a while?

---

### Post by zvacet on 2007-03-19
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by mig96 on 2007-03-19
That says "install".

When I mounted the iso that I downloaded and expected a "live" Linux distribution, started "start.exe" and it said that I had to boot from the CD.

So when the CD started I just pressed enter on option "Start or install Kubuntu" and then it showed the rest of it...

and I got 

ubuntu@ubuntu:~$

instead of 

username@ubuntu:~$

If it confuses you, I'll say it more clearly:

I was not trying to install, only to test out the dist.  It said that it didn't affect my copy of Windows.

[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox) shows a package installer.  From my limited knowledge of Linux, I gather that it was not supposed to be installing when it was my trial.

Yes, I got the desktop version.

I'll try 

sudo /etc/init.d/kdm start though...

---

### Post by mig96 on 2007-03-22
ummm someone PLEASE respond :confused:

---

### Post by Kamu on 2007-03-22
x server errors like that mean the graphical interface cannot be started because of a problem with the video card or driver or the display.  I am not sure I can help you much since I am not very knowledgeable on video problems.  What you can do to get more help is to tell us what video card you are trying to use.

You can also search the forums for threads that feature problems with that video card.  You are probably not the first one with compatibility problems related to that piece of hardware.  If htat iis indeed the problem.

---

### Post by mouseboyx on 2007-03-22
If you resize the parti with Vi$ta on it with g part you will not be able to boot vista anymore so be careful.

---

### Post by mig96 on 2007-04-19
intel 945gm.

---

### Post by mig96 on 2007-06-13
The problem was fixed using nano like
sudo nano /etc/X11/xorg.conf
and editing x-org.
Then using 915resolution package.

---

