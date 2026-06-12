---
title: "Running Ubuntu on beige G3"
date: 2005-07-16
forum: Apple PPC Users
---

### Post by darwinboy on 2005-07-16
A friend of mine has an old beige G3 366 tower, which has a 6GB SCSI drive and 256MB RAM and is currently gathering dust. In a phone conversation I had with him a couple of days ago, I suggested that he bring this old machine out of mothballs and press it into service as a server (most likely, a file server) for his small home network. This network consists of two iMacs, a G3 and G5, a networkable Lexmark laser printer, and an Asante ethernet hub. At first I thought of installing OS X on this older machine, but then I thought that it might be better to run a flavour of Linux, such as Yellowdog or Mandrake. Then, someone mentioned Ubuntu as another Linux solution.

Has anyone on this list had any experience installing and running Ubuntu on Old World Macs such as beige G3s? Any feedback, suggestions, and thoughts would be appreciated.

Roland :)

P.S. I am new to the world of Linux.

---

### Post by lubod on 2005-07-16
Not to put you off the idea of Ubuntu or Linux, because they are great in many ways, but on Old World Macs, it isn't always the easiest way to go.

I do believe you can use anything up to Mac OS 10.2 without any sort of software hacking (it is officially a supported OS by Apple's specifications).

With 366 Mhz G3, 6Gb of space on the Hard Disc, 256 Mb RAM, even 10.3 would run quite ok if unspectacular. This can be accomplished with XPostFacto from Ryan Rempel 

[http://eshop.macsales.com/OSXCenter/XPostFacto/Framework.cfm?page=XPostFacto3.html](http://eshop.macsales.com/OSXCenter/XPostFacto/Framework.cfm?page=XPostFacto3.html)

Much easier to run, and administer, and your Mac files will be stored on a Mac so resource forks and metadata will be maintained in tact.

My own use of Linux on Macs (Ubuntu and other distributions you mention) has been pretty dismal, usually failing in some portion of the install. Perhaps because I insist on making use of old/esoteric Macs like a Umax C500. I like it on Intel/AMD PCs

---

### Post by TravisNewman on 2005-07-16
I'm running on a G3 at 450 mhz and it's fantastic. My PC is kinda dead so this is all I have. For the purpose you need it for, it will run fine (in my experience)

By the way, I don't think a G3 is considered old-world, but I could be wrong. This machine came with OSX installed, and it's not that fast at all. Ubuntu runs much smoother than any variant of OSX has.

---

### Post by DJ_Max on 2005-07-17
The beige G3 is an "world mac", since it was made before the first iMac. Anything made after the first iMac (1998) is condsidered a "new world". 

By default, you can run OS 10.2.8. But with [XPostFacto 3](http://eshop.macsales.com/OSXCenter/XPostFacto/) you could run OS 10.4. Condsidering this mac is kinda old, and discontinued, it would make more sense to use a Linux or BSD OS on it, rather then OS X. I know for a fact that NetBSD has good support for old world macs. But it never hurts to try Ubuntu.

I also forgot to mention you may/will have a problem with Yaboot, as it's only supported to run on new world macs. You will probably have to use BootX.

---

