---
title: "Need Free BSD Recomendations."
date: 2005-11-09
forum: BSD
---

### Post by Omnios on 2005-11-09
Im trying to get a os other than win on my old P2-350 and have installed Free BSD and managed to get KDE running rather well on it but am having majore problems as I can not ksdu and am currently running it as logging into root starting KDM and logging into KDE. My majore problem is I can not get the network to work in KDe even though it detects it and the numbers are good on post install.

 Rather than revert to win and Linux Kernal will not run on the ami biosy so I figured id give BSD a try. I tryed Free BSD because I liked the little demon logo but am now looking for something much more easy to config. Does anyone have any recomondations for a BSD that is more Linux like?

---

### Post by -Rick- on 2005-11-09
[QUOTE=Omnios]Im trying to get a os other than win on my old P2-350 and have installed Free BSD and managed to get KDE running rather well on it but am having majore problems as I can not ksdu and am currently running it as logging into root starting KDM and logging into KDE. My majore problem is I can not get the network to work in KDe even though it detects it and the numbers are good on post install.

 Rather than revert to win and Linux Kernal will not run on the ami biosy so I figured id give BSD a try. I tryed Free BSD because I liked the little demon logo but am now looking for something much more easy to config. Does anyone have any recomondations for a BSD that is more Linux like?[/QUOTE]
[http://www.pcbsd.org/](http://www.pcbsd.org/) or [http://www.desktopbsd.net/](http://www.desktopbsd.net/)

I had kdesu not working at a time, recompiling kdebase and/or kdelibs worked.
About the network...what is exactly wrong? You can't browse the internet?

---

### Post by Omnios on 2005-11-09
It seems that the network is set up properly but will not connect to the web. Its like its not setting up properly in KDE.

---

### Post by -Rick- on 2005-11-09
[QUOTE=Omnios]It seems that the network is set up properly but will not connect to the web. Its like its not setting up properly in KDE.[/QUOTE]
hmm...maybe you can add the DNS IP address manually to /etc/resolv.conf and see if that helps?

---

### Post by Omnios on 2005-11-09
Well downloaded PC-BSD and managed to get it burnt but have no mouse in the set up wich does not seem to be a problem. On the first try it booted with a no rom  halting error so im figuing I didnt install the boot loader and must have had to old Free BSD boot loader installed. Not 100% shure on that though hopefully the second try will work then again it an be a bad disk burn as I know free BSD installs and runs on it. 

 Now im going to have to figure out how to get my mouse to com:1 and hopefully the network sets up ok. 

 ANother question I have will free BSD screw up the MDR or do I have to do anything special to get free BSD off of it this may hinder my install attempts of PC-BDS.

 Cool got it loaded but still no mouse on com:1 guess its the same as KDE and Xorg just have to figure out how to get into config from text mode anyone know the hotkeys to go into text?

---

### Post by Omnios on 2005-11-10
Thanks -Rick-

 Got PC-BSD up and running got the mouse sorted out and the network is running out of the box. My old machine is mostly to have net access if the main pc goes down and to fiddle with so now I have a few more new toys. Now I can get back to Linux and have at least one computer m$ free. 

 If your stuck with a ami boisy (linux incomaptible) on one of your boxes you might want to give PC-BSD a try.

---

### Post by az on 2005-11-10
There is always Debian:
[http://www.debian.org/ports/kfreebsd-gnu](http://www.debian.org/ports/kfreebsd-gnu)
Live cd:
[http://glibc-bsd.alioth.debian.org/ging/](http://glibc-bsd.alioth.debian.org/ging/)

---

### Post by -Rick- on 2005-11-10
[QUOTE=Omnios]Thanks -Rick-

 Got PC-BSD up and running got the mouse sorted out and the network is running out of the box. My old machine is mostly to have net access if the main pc goes down and to fiddle with so now I have a few more new toys. Now I can get back to Linux and have at least one computer m$ free. 

 If your stuck with a ami boisy (linux incomaptible) on one of your boxes you might want to give PC-BSD a try.[/QUOTE]
Heh nice :)
I never tried it, but is it as easy as say ubuntu?

> There is always Debian:
[http://www.debian.org/ports/kfreebsd-gnu](http://www.debian.org/ports/kfreebsd-gnu)
Live cd:
[http://glibc-bsd.alioth.debian.org/ging/]](http://glibc-bsd.alioth.debian.org/ging/])
Although I can understand its fun to do something like this, its rather useless IMO. BSD's base system seems much more organized, so why throw that away?

---

### Post by az on 2005-11-10
[QUOTE=-Rick-]Although I can understand its fun to do something like this, its rather useless IMO. BSD's base system seems much more organized, so why throw that away?[/QUOTE]


How about the GPL and the DFSG?

---

### Post by -Rick- on 2005-11-10
[QUOTE=azz]How about the GPL and the DFSG?[/QUOTE]
Well I don't really care about which Open Source license to use...besides BSD license is even more "free" ;) And whats DFSG?

---

### Post by TravisNewman on 2005-11-10
[QUOTE=-Rick-]Well I don't really care about which Open Source license to use...besides BSD license is even more "free" ;) And whats DFSG?[/QUOTE]
free for whom, that's the question.

---

### Post by az on 2005-11-10
[QUOTE=-Rick-]Well I don't really care about which Open Source license to use...besides BSD license is even more "free" ;) And whats DFSG?[/QUOTE]
Debian Free Software Guidelines.

The GPL ensures that the software will *remain* free.  That is a big difference between it and the BSD-type licences.

It is your choice to decide what suits you, of course.  I was just answering your question.

---

### Post by -Rick- on 2005-11-10
[QUOTE=panickedthumb]free for whom, that's the question.[/QUOTE]
For everyone? BSD license lets you do with the code whatever you want. However I agree that 
[quote=azz]The GPL ensures that the software will *remain* free.[/quote]
is more important.

> I was just answering your question.
Yeah, I just like to comment on random things :)

---

