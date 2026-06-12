---
title: "Ubuntu, Server Edition and Xubuntu"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by markop on 2006-10-16
Hi,
Im looking to run a server that uses as little RAM as possible. Should i use Ubuntu, Ubuntu-Server Edition or Xubuntu?

Also how much RAM would these OS's us?

---

### Post by PriceChild on 2006-10-16
i would advise using the server edition off of the alternate install cd.
then
```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

This will install xubuntu for you... unless there's an xubuntu install disc i'm unaware of?

Remember that the server install gives you command line only. Any configurations for net etc. need to be done on the cl before you get the gui.

---

### Post by Sef on 2006-10-16
Recommended ram for ubuntu is 256, and for xubuntu is 128.  Both can run on less though not as well.

---

### Post by stalker145 on 2006-10-16
> **PriceChild said:**
> unless there's an xubuntu install disc i'm unaware of?

Why, actually, there is an [install disk]("http://www.xubuntu.org/")... and it's Live 8)

---

### Post by az on 2006-10-16
> **markop said:**
> Hi,
Im looking to run a server that uses as little RAM as possible. Should i use Ubuntu, Ubuntu-Server Edition or Xubuntu?

Also how much RAM would these OS's us?

You should not use any graphical environment at all if you want to keep ram usage down.

You can run a server on 64 megs of ram.  But you don't really want to do that.  You may not be able to complete the installation if you try to install using a language other than english.

So, use the server cd or the alternate cd (and install using the server option).  If you are going to run this on a pentium one, use the alternate cd, since the kernel you will get from the server cd will only run on a pentium two or better.

---

### Post by PriceChild on 2006-10-16
> **stalker145 said:**
> Why, actually, there is an [install disk]("http://www.xubuntu.org/")... and it's Live 8)I did not know that...

Never saw it on ubuntu.com but following links its there!

Pricey

---

### Post by bodhi.zazen on 2006-10-16
Yikes, look at all these experts :lol:

Consider [[color=darkgreen]Fluxbuntu[/color]](http://fluxbuntu.org/)

“The Lightweight, productive, agile desktop environment.”

Comes as a live CD you can then install to HD. Window manager = Fluxbox. 100% compatible with ubuntu.

The website is down at the moment....

---

### Post by markop on 2006-10-16
By alternate cd u mean...

sry i am a long time windows user](*,)

PS. The comp is a P4 1.7ghz with 512 mb of RAM, i want to use very little because it will be a gameserver:cool:

---

### Post by stalker145 on 2006-10-16
> **bodhi.zazen said:**
> Consider [[color=darkgreen]Fluxbuntu[/color]](http://fluxbuntu.org/)

The website is down at the moment....

That sucks about the site being down. I'm always wanting to tinker with my Ubuntu setup and, knowing me and my memory, by tomorrow when the site is (hopefully) up, i will have... ummm, what was I talking about again??:-? 

But, seriously, I'm a-gonna look into this. With my laptop, I can always use a setup that will go easier on the resources.

---

