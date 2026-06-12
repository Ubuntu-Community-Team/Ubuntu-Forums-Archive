---
title: "Ten tips for new Ubuntu users"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by newbie2 on 2006-06-22
> Ten tips for new Ubuntu users

Wednesday June 21, 2006 (02:01 PM GMT)

By: Joe 'Zonker' Brockmeier

Ubuntu has become the most popular Linux distribution for new Linux users. It's easy to install, easy to use, and usually "just works." But moving to a different operating system can be confusing, no matter how well-designed it is. Here's a list of tips that might save you some time while you're getting used to Ubuntu. 

[http://www.linux.com/article.pl?sid=06/06/08/1651225](http://www.linux.com/article.pl?sid=06/06/08/1651225)

---

### Post by siccness on 2006-06-22
I saw this posted this morning an IRC channel this morning, although it's pretty useful, I'm not sure I agree with #6. 

[QUOTE=From Link]
To install all of the packages that come with one of the flavors of Ubuntu, such as Kubuntu, run apt-get install kubuntu-desktop 
[/QUOTE]

Wouldn't aptitude be the better way to do it?

---

### Post by aysiu on 2006-06-22
[QUOTE=siccness]I saw this posted this morning an IRC channel this morning, although it's pretty useful, I'm not sure I agree with #6. 



Wouldn't aptitude be the better way to do it?[/QUOTE]
Yes, *aptitude* would be better.

A few more amendments:

1. Makes it sound as if it's only for legal/cost reasons that proprietary codecs are left out. They're also left out because they're... proprietary, and Ubuntu is dedicated to open source software. Many distributions like Blag, PCLinuxOS, and Mepis are cost-free but include these proprietary codecs.

There's also a mention of the Restricted Formats Wiki entry but no mention of Automatix, BUMPS, or Easy Ubuntu.

2. Do new users really care about changing the "default" (where is it the default?) editor from Nano to Vim? I'd say most new users who need this guide would be fine with the default Gedit.

3. You don't need to right-click a .deb to install it. Just double-click it. GDebi is the default application for .deb files.

4. Why mention Adept in #2 and not mention *kdesu*, the KDE equivalent of *gksudo*?

7. Should be *_sudo_ dpkg-reconfigure xserver-xorg*.

9. Wouldn't hurt to mention that *build-essential* is on both the Desktop and Alternate CDs, even though it's not installed by default.

---

### Post by pjot on 2006-06-22
**@#4:** Why would you want to use **sudo su -** to get a root terminal? What's wrong with **sudo -s**?

---

### Post by siccness on 2006-06-22
aysiu:
You raised some good points, especially #2. You'll find most new users won't even know how to use nano, vi, etc. While gedit is GUI, to make life easier.

---

