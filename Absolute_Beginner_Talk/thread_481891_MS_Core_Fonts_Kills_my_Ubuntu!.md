---
title: "MS Core Fonts Kills my Ubuntu!"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Rabidmonkey1 on 2007-06-23
Okay guys, I am having a real terrible time with this now...

Let me describe my problem.  I'm running the Ubuntu Studio version of Feisty Fawn, and when I download the MS Core Fonts using Sudo, pretty soon, my system starts crashing.  The only way I can describe it is that it looks like pieces of my Desktop are slowly being erased...one icon disappears, then another, you click on something and suddenly the command isn't there or the system can't find a the file.  Pretty soon all icons are gone, all programs stop functioning....

I log out and get a disk boot failure...it's almost like the fonts are eating my system!

This is the second time this has happened to me (this being the first time I realized what was really causing it...)

Anyone have any idea what is going on?  I'm tired of reinstalling my system!

--Update--

Alright, might have overreacted a bit...  For whatever reason, when I install these fonts, it freaks my computer out (are configuration files being changed when this installation occurs?)

Anyways, I took an old hard drive with an old Windows Server x64 2003 image on it, booted it up and exited.  That got my computer reading my hard drives again.  Reconnected my linux drive and my windows drive - grub loaded up and I was able to get back into the system just fine...

But I am noticing something now...

I'm looking at my filesystem properties and it says that the Size of the disk is unknown (around 460 gb in actuality)

Also, all permissions are changed to Read-Only.

Is this the way it normally is, or is there any way to change this?

Thanks to anyone who can help me with this confusing mess :D

---

### Post by swoll1980 on 2007-06-23
Welcome to my nightmare. You have to
sudo dpkg reconfigure -a

---

### Post by Rabidmonkey1 on 2007-06-26
hmm...I'm fairly new to linux...what will that do?

I mean, I have the system running fine and I don't expect to encounter the problem again, so how would this benefit me?

Thanks for the reply!

---

