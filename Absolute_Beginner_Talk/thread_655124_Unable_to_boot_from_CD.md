---
title: "Unable to boot from CD"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by wierdo on 2007-12-31
I'm trying to install Ubuntu for the first time with a computer with Windows 98 installed.  It has 64MB of RAM, a 500 mhz processor, and a 7.8 gig HD.  When I put the CD in and restart, it goes straight to Windows 98.  I checked the bios, and the CD drive is first to boot.

Could low RAM be a problem here?  Could I install the RAM chip from the computer I'm currently working on (512 MB) and install it, then take it back out?

Thanks

---

### Post by the_darkside_986 on 2007-12-31
Well, you certainly need at least 320 MB of RAM to use the Ubuntu live installer CD. But I doubt you will get very far after installation if you only have 64 MB of RAM. I would recommend something like Xubuntu for a system with low RAM, but then again, I think it even requires at least 128 MB.

I have a system that has 128 MB of RAM and I still couldn't get Xubuntu to show the desktop. So even if you manage to get installed, with that amount of RAM you will have a rough time using a desktop or graphical user interface.

---

### Post by Xavieran on 2007-12-31
Have you verified the CD's integrity?

Yes,with that much RAM you will need to use the alternate cd to install...also I would suggest using xfce (xubuntu) because it will preobably require much less RAM

the_darkside_986  :You beat me to it! xDD

---

### Post by taurus on 2007-12-31
You may even have to try fluxbuntu with that amount of RAM.

---

### Post by wierdo on 2007-12-31
Thanks for your quick responses.  I'll attempt the install with my ram and see where I get.

---

### Post by Sef on 2007-12-31
> You may even have to try fluxbuntu with that amount of RAM.

Check out [Fluxbuntu]("http://fluxbuntu.org").

---

### Post by wierdo on 2008-01-01
I will check it out.  I realized that my ram is also uncompatible.

What are the requirements for Fluxbuntu?

---

### Post by yaknowwat on 2008-01-01
> **wierdo said:**
> I will check it out.  I realized that my ram is also uncompatible.

What are the requirements for Fluxbuntu?


when i ran a system monitor in fluxbuntu it showed at 110 but it has a lot a swappable parts that can be laid to rest.

personally I wouldn't suggest any *buntu distros for that amount of RAM.

Damn Small Linux : [http://damnsmalllinux.org/](http://damnsmalllinux.org/) its 50MB (in download size)
or 
Puppy Linux : [http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1) its a bit under 100 MB (in download size)

Both of these distro's have their ups and downs.

DSL is Debian based (which is good as ubuntu is also debian based)
Though its overall look and feel is bad you may be able to change its window manager i am unsure of this.
Its hardware support is said to be incomplete on somethings

Puppy linux is slackware based. (slackware 12 full compatibility )
Only thing I can say is its basic package manager programs are kind of old.
This may be solvable since you can put Slackwares apt-get on it supposedly.
said to have really decent hardware support for a small distro.

DSL can run nicely in about 16-128MB RAM depending on what you do 128 if you view vids a bit i would suggest.
Puppy linux runs nicely with about 32-128 MB RAM by 128 MB of RAM video should be nice if you have a decent vid card.

My favorite out of the two is puppy linux.

Hope I helped some.

---

