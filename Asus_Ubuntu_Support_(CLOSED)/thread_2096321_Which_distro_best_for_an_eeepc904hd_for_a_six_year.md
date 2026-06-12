---
title: "Which distro best for an eeepc904hd for a six year old"
date: 2012-12-19
forum: Asus Ubuntu Support (CLOSED)
---

### Post by salviablue on 2012-12-19
Hi, I have looked around but all discussions regarding this seems to end around 2009.
The eeepc is currently dual booting ubuntu 10.10 and win vista.

vista only boots some of the time, but when it does it works great.

ubuntu runs great except for internet browsing, which is dog dead slow, doesnt  matter the browser, firefox, chrome, etc. and anything to do with graphics.

ive tried numersous things to get the graphics going to see if thats the issue, i.e. not using any drivers but that which came with, installing official ones, non-official ones etc. running metaciy, or the other  ones, or running wiithout any of the fancy visuals. including installing the latest ubuntu flash, from various sources,, the latest non ubuntu specific ones, the  linux make do ones.....nothing seems to help. 

I have forgotten most of what I went through to get averything working from feisty, plus a lot has changfeed since then, and I'm not going through it all again unles there is no other option bar going skint for the first half of next year.

My son want to be able to play the odd windows games/run the odd windows programs through wine or maybe virtual box, (not paying another penny to micro$oft so dual boots or vb images will have to be donated licence keys).
He wants to be  able to play certain browser games, like angry birds, CN games and lego hero factory are deal breakers (else we have to exchange his birthday present for something else that will not last him the expense).

But he also needs to be able to do his school work on it, and learn other computer related stuff, as well as general watching streaming/dl'd vids etc...

We want this to last him until it physically breaks or is no longer capable for him to do school work upon.




So, basically, which is the best os to have on this eeepc that can do what we want it do. Was thinking of  just upgrating to the latest lts 12.xx and fiddling from there, but cant seem to find any info on it for this eeepc.

---

### Post by snowpine on 2012-12-19
The bottleneck is your netbook's Intel Celeron M processor and poor graphics capabilities. Unfortunately this is even slower than the Atom platform, so you can forget about flash videos/games according to Adobe's published hardware requirements for Linux:

[http://www.adobe.com/products/flashplayer/tech-specs.html](http://www.adobe.com/products/flashplayer/tech-specs.html)

My recommendation is to fix the Vista boot loader, since you say Vista runs fine. If you use the Search box at the top right of the screen you will find several existing "vista bootloader" conversations, good luck! :)

---

### Post by Somewhat Newbie on 2012-12-19
Just keep Vista and find ways of cleaning it as best you can without deleting stuff that you don't know what it might be or is. Deleting software is not going to make Vista better or faster. 

If you are new to Linux you must keep Windows of any kind, if you know Linux very well then Zorin 6.1 lite might be the best option for old computers, but I like dual boots with any Windows but that's me.

---

### Post by mysteriousdarren on 2012-12-19
I'd dualboot with Vista and have Lubuntu as the other OS.

---

### Post by chrisbarnes1992 on 2012-12-20
Xubuntu or Lubuntu would work great.

---

### Post by sudodus on 2012-12-20
***Lubuntu 12.04*** with the addition of

```
sudo apt-get install xubuntu-desktop
```

or a persistent installation of ***Knoppix***.

---

### Post by Pjotr123 on 2012-12-20
Xubuntu 12.04 LTS, because of the non-PAE kernel support, which you'll probably need:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/Xubuntu](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/Xubuntu)

---

### Post by houseworkshy on 2012-12-20
You have another choice, live disto's.  
You could collect some puppy Linux disto's with a view to running them live.  Puppy is actually designed to be used that way, very low footprint so excellent on older machines.  Worth having around as an emergency disk anyway, it can save files from a system that won't boot.  So small it can be loaded to ram and the medium that was used to boot it from can be removed from the usb or cd/dvd drive so that one can burn or copy your files to something blank. There are many various flavours aimed at many specific interest areas.
[http://www.puppylinux.com](http://www.puppylinux.com)

As the machine has been running vista and Ubuntu it may cope with the full bells and whistles of of a modern Knoppix, which is another 'designed to be run live distro' and could certainly handle the older ones.  Knoppix is packed with software including a full office suit.
[http://www.knoppix.org/](http://www.knoppix.org/).  

One thing I would recommend is that you back up any important stuff so that when the machine breaks it's only the loss of a machine.

As for installations there are many versions of Linux which are good on low spec systems and amazingly fast on modern ones.  If you do switch make sure the new one is supported.  AntiX and Slitaz are among the best for being light and fast, they're towards the other end of the spectrum to Ubuntu with Unity or KDE which are among the most resource demanding of the popular distributions in Linux.  Staying with Ubuntu, using another GUI does lighten things up a bit; Xfce ( Xubuntu ) and Lxde ( Lubuntu ) being the most popular but there are many, open box, enlightenment, razer.  
As the machine was ok with Ubuntu 10.10 it shouldn't have many problems with practically anything.  Debian's a beauty and would look familiar, the early Ubuntu&#8217;s were almost debian made easy with a dash of sudo.  Well debian's fairly easy now, live distro and all, so you could consider that, it may have the biggest software collection and best hardware compatibility of all linuxes.  There is still some fiddling around to be done so Mepris, which is also based on debian but less divergently would be better if you want everything out of the box.  Either require less ram than the standard Ubuntu.  There are also many many other choices.

The thing about the live distro idea is that they are set in time like hardware one isn't upgrading, if they worked on something once they always will work on it until it breaks.  The other nice thing is they don't alter your system like a borked install might. Get some anyway, if ever the installed systems won't boot due you may be glad they're in the rack.  It was actually using Knoppix, (which I only had almost by chance because it was the cover disk on a computer magazine) to rescue files and carry on working when Vista had it's wobble fits that got me into Linux.

---

