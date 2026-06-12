---
title: "is there an Ubuntu 5.10 starter guide?"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-11-24
I know that there is a ubuntu 5.04 starter guide.  Is there one for 5.10?

I just did a clean install of breezy and was wondering how I could get the latest in my sources.list file?

---

### Post by atoponce on 2005-11-24
[quote=racermike1967]I know that there is a ubuntu 5.04 starter guide.  Is there one for 5.10?

I just did a clean install of breezy and was wondering how I could get the latest in my sources.list file?[/quote] 
Yeah.  [UbuntuGuide]("http://www.ubuntuguide.org") is still tailored after hoary. For the most part, however, most everything will be the same. If you would like to get the latest in your sources.list file, just do:

```
sudo apt-get update
``` 
then

```
sudo apt-get upgrade
``` 
for making sure all the software on your system is the latest and greatest. You should have the Synaptic updater turned on unless you turned it off. Leaving that on will notify you when you have updates that need to be installed.

---

### Post by aysiu on 2005-11-24
[QUOTE=atoponce]Yeah.  [UbuntuGuide]("http://www.ubuntuguide.org") is still tailored after hoary. For the most part, however, most everything will be the same.[/QUOTE] I've found only a few things that no longer apply--the sources.list and a few codecs that are no longer available--w32codecs and libdvdcss2. Other than that the Ubuntu Guide is still usable in Breezy.

P.S. atoponce, I stumbled upon your blog once, and I still read it. I don't know if I agree with you 100% on the hands-free sets, but I still think you generally have a good point.

---

### Post by ubuntu27 on 2005-11-24
[QUOTE=racermike1967]I know that there is a ubuntu 5.04 starter guide.  Is there one for 5.10?

I just did a clean install of breezy and was wondering how I could get the latest in my sources.list file?[/QUOTE]

Here: [http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)

---

### Post by towsonu2003 on 2005-11-24
5.10 guide is under System>Help>Ubuntu 5.10 Starter Guide

for sources list, check out [http://www.ubuntuforums.org/showthread.php?t=76132&highlight=sources.list](http://www.ubuntuforums.org/showthread.php?t=76132&highlight=sources.list) , seems okay...

or [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php) which is more well known...

[edit] wow, 3 more replies while I was writing this... wow :) [/edit]

---

### Post by atoponce on 2005-11-25
> P.S. atoponce, I stumbled upon your blog once, and I still read it. I don't know if I agree with you 100% on the hands-free sets, but I still think you generally have a good point.

Wow!  I thought my faithful readership didn't extend much beyond my family and friends.  Thanks for reading!

---

