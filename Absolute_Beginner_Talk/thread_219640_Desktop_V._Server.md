---
title: "Desktop V. Server?"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by worstofboston on 2006-07-20
Hello,

I need to learn the LAMP environment, but I am a Linux beginner and do not want my machine to look like a terminal all of the time. I like the way the Ubuntu GUI looks, would like to use it.

There are several things I am unclear on.

1. Is there a distinct server edition and a distinct desktop edition, or are they the same thing with different packages included?

2. Do they really install from only one cd? I just downloaded 5 cds for Fedora. How can it be 1/5th the size?

3. My machine will serve as both a desktop and a server for me to learn on. I will use it as my regular machine AND my little practicing laboratory. Is this a bad idea? Which install route should I take?

Thank you. I decided to go with Ubuntu over Fedora based on the community I see here. Its great.

I work for a nonprofit and have a M$ background. I was a developer once upon a time and am now a Project Manager. I want to completely transform our organization into an open source organization, despite the fact that we get all the M$ we want for nothing. 

Thank you so much.

JD

---

### Post by aeto on 2006-07-20
1. If i recall correctly, yes there is.

2. Ubuntu is a small download (more so because it depends on the internet to get updated very often, hence not needing to be a bulky OS). That is why 1 cd is enough. But there is a larger download, with extras added in. That would b a dvd or 4/5 cds (ard 2 or 3+ GB).

3. Depends on what type of things u'd do more. Networking? Then server would b better.

I too chose Ubuntu over Fedora after trying out the latter for a week :mrgreen:

---

### Post by fadumpt on 2006-07-20
as far as I know (going to try out the server version in a few days) the server version is the same as far as the GUI (although that command line server I did that one time was pretty awesome) and the biggest difference is probably packages included.  The server version also allows you to install a working LAMP enviroment from within the instalation.  

ubuntu only requires one CD because it is giving you everything you need to get started and from there, the package manager is so easy, you don't need to have all the packages on a CD.

Like with gentoo, you could download a 200MB ISO and install almost everything over the internet.  Just makes it easier to get in to the OS easier.  I think Fedora is giving you everything you could ever want and not want with those 5 Discs

You'll get a lot of learning out of using it for both purposes, just back up your data, you'll most likely break stuff while you  are fiddling around with different things :)   

Good luck with the conversion to open source.

---

### Post by A2A on 2006-07-20
worstofboston,
I'm very new to linux aswell.
Here's what I did.  I installed the server off the CD only to realize that it was pretty much terminal based.  At that point I converted to the desktop version using the following command:
> 
sudo apt install ubuntu-desktop
 Now a uname -a command shows me the following:
> 
a2a@A2A-Ubuntu:/etc$ uname -a
Linux A2A-Ubuntu 2.6.15-26-server #1 SMP Mon Jul 17 20:58:01 UTC 2006 i686 GNU/Linux
 
Then I installed Apache2, Samba, Webmin, PHP etc.  There's tons of resources online to guide you through those installs.
Hope this helps.

A2A

---

### Post by az on 2006-07-20
All is revealed here:

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

### Post by worstofboston on 2006-07-20
Wow, that was great.

If only there was this kind of forum for the other stuff I am having trouble figuring out. Like transitioning from M$ to open source. 

Thank you all. Ubuntu seems super cool so far. 

JD

---

