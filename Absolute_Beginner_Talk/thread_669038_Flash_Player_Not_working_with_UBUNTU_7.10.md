---
title: "Flash Player Not working with UBUNTU 7.10"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by eleaguers on 2008-01-16
I've tried a lot of things that are listed here in the forum and unfortunately I can't make the flash player work. I need a lot of help. Just my first day using UBuntu!!! THanks

---

### Post by RomeReactor on 2008-01-16
Hi. The flashplugin-nonfree package in the repositories is broken at the moment; download[ this fixed package]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466"), close Firefox, and double click on it to install. Then yo can open Firefox again. More information on the [problem here]("http://ubuntuforums.org/showthread.php?t=636397").

---

### Post by mikewhatever on 2008-01-16
> **eleaguers said:**
> I've tried a lot of things that are listed here in the forum and unfortunately I can't make the flash player work. I need a lot of help. Just my first day using UBuntu!!! THanks

A lot of things? Can you be more specific? Do you get errors? [http://psychocats.net/ubuntu/flash](http://psychocats.net/ubuntu/flash)

---

### Post by jerrykenny on 2008-01-16
Also you'll probably need gnash

sudo apt-get install gnash

---

### Post by Sef on 2008-01-16
> Also you'll probably need gnash

sudo apt-get install gnash

Don't get gnash.  Gnash is an open source alternative to Macromedia flash.  Gnash is still in an alpha state, so it is quite buggy and many sites do not work with it.

---

### Post by Joeb454 on 2008-01-16
The adobe site for flash contains the most up-to date version, and also the instructions aren't too bad to follow, even if you are new :)

If there's a fixed .deb package, then use that, it'll be much easier :)

And I've never had to use gnash for more than 10 minutes ;)

---

### Post by Distro Jockey on 2008-01-16
Thanks for the link to the fixed package RomeReactor, works for me.

---

### Post by eleaguers on 2008-01-19
thanks for your help guys. I was able to install the flash plugin. I did reinstall ubuntu first then installed the flash plugin. 

OT: Got another old box here. AMD K5 32MB ram 2 gig HD. Do you know any linux that will work for this?

---

### Post by RomeReactor on 2008-01-19
> **eleaguers said:**
> Got another old box here. AMD K5 32MB ram 2 gig HD. Do you know any linux that will work for this?

Probably [Puppy]("http://www.puppylinux.org/") (installed) or [DSL]("http://damnsmalllinux.org/"), or most distros without the X server.

---

### Post by quinnten83 on 2008-01-19
> **RomeReactor said:**
> Probably [Puppy]("http://www.puppylinux.org/") (installed) or [DSL]("http://damnsmalllinux.org/"), or most distros without the X server.

DSL & Puppy +1

---

### Post by anxean on 2008-01-19
anyone got this working in 64bit ubuntu?

---

### Post by RomeReactor on 2008-01-19
Hi. If you're referring to the problem with Flash, [here's the 64-bit package for Gutsy]("http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466"); download it, close Firefox, double click the downloaded package to install it, then open Firefox. Flash should work then.

For information on the problem, and packages for previous versions, [see this thread]("http://ubuntuforums.org/showthread.php?t=636397").

---

### Post by zipperback on 2008-01-19
> **jerrykenny said:**
> Also you'll probably need gnash

sudo apt-get install gnash


You DO NOT want to install both Flash and Gnash. That will cause problems.

- zipperback
:popcorn:

---

### Post by IceDragonkin on 2008-04-14
> **RomeReactor said:**
> Hi. The flashplugin-nonfree package in the repositories is broken at the moment; download[ this fixed package]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466"), close Firefox, and double click on it to install. Then yo can open Firefox again. More information on the [problem here]("http://ubuntuforums.org/showthread.php?t=636397").

I guess im running a different architecture that isn't 'i386' so would this pack be around for whatever kind im running and how would i figure out what that is?

---

### Post by tiktaalink on 2008-05-09
Has anyone made flash work on a 64 bit system with 8.0.4?  I guess I'll just start clicking like a monkey and see if any of the recommendations above will work.

---

