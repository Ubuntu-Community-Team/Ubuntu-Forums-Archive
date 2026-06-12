---
title: "Couldn't find package sun-j2re1.5 ???"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by ronlondre on 2005-09-07
Is there an updated version of this plug in that I sould be attempting to apt-get? Is that why the sun-j2re1.5 package cannot be found?

---

### Post by Kapre on 2005-09-07
[QUOTE=ronlondre]Is there an updated version of this plug in that I sould be attempting to apt-get? Is that why the sun-j2re1.5 package cannot be found?[/QUOTE]

Ronlondre - please update your sources.list to [this](http://www.ubuntuguide.org/#repositories) . I just installed this package 2 days ago.

K

---

### Post by ronlondre on 2005-09-07
> Ronlondre - please update your sources.list to this . I just installed this package 2 days ago.
I just updated it this morning.  I have been able to apt-get install gparted and gdesklets from the repository this morning. However I have not been able to aquire a number of updates for firefox from the repository; including: J2SE Runtime Environment, macromedia flash player, or PDF reader.  I recieve the message "couldn't find the package...." for each of the plugins.    What's going wrong?

---

### Post by ronlondre on 2005-09-07
I have the 64 bit ubuntu OS installed on my system, which has a AMD64 cpu.  I see that in the AMD64 starter guide there are no instructions for installing the varoius firefox packages. Are the "couldn't find package" results be because I cannot install them due to the 64 bit ubuntu OS I have?

However I do see that there is a AMD64 repository.  How and where do I enter the code (and what is the code) to gain access to the AMD64 repository for the apt-get install command?

---

### Post by Kapre on 2005-09-07
[QUOTE=ronlondre]I have the 64 bit ubuntu OS installed on my system, which has a AMD64 cpu.  I see that in the AMD64 starter guide there are no instructions for installing the varoius firefox packages. Are the "couldn't find package" results be because I cannot install them due to the 64 bit ubuntu OS I have?

However I do see that there is a AMD64 repository.  How and where do I enter the code (and what is the code) to gain access to the AMD64 repository for the apt-get install command?[/QUOTE]

ronlondre - I cannot tell you much about the 64-bit because I'm using the default (386 i think). But I think you can just copy the repos from the list in the ubuntu guide and you'll get the java pkg.

My suggestion is to copy the universe/multiverse repos and add it to your list and then after getting the pkg that you need, go back and comment the lines again so you'll end up using the AMD repos again.

K

---

### Post by Nequeo on 2005-09-07
[QUOTE=Kapre]ronlondre - I cannot tell you much about the 64-bit because I'm using the default (386 i think). But I think you can just copy the repos from the list in the ubuntu guide and you'll get the java pkg.

My suggestion is to copy the universe/multiverse repos and add it to your list and then after getting the pkg that you need, go back and comment the lines again so you'll end up using the AMD repos again.

K[/QUOTE]
 If you're new to Linux, and things like Java, Flash,Adobe Acrobat Reader, Windows games, Open Office 2, etc. are important to you, I would really reccomend installing the i386 version. I started off like you did, with AMD64, and just had problem after problem after problem. 

I resisted for a long time, but it got to the point I was almost tempted to switch back to Windows. Instead, I simply switched to Ubunu i386. Primarly because tweaking a Linux installation is less effort than tweaking a Windows installation, and I'd accidentally wiped my system installing Ubuntu in the first place. Mind you, I grew up on a Unix command-line - so I get things done faster that way. 

In any case, not only did all my problems just melt away, but I actually found the i386 version used less memory too, for some reason. 

In fact, I'd stick with i386 until at least version 6.04 of Ubuntu. You'll just have too many problems before that.

Cheers,

---

