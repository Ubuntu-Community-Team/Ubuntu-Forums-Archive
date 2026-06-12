---
title: "PPC Virtualization?"
date: 2007-04-30
forum: Apple PPC Users
---

### Post by johng4 on 2007-04-30
I've recently fallen in love with VirtualBox ([www.virtualbox.org](www.virtualbox.org)) and qemu.  Now that I finally have my iBook G4, I'm looking to see if I can use a VM at all.  Its not make or break, but it would be nice.

---

### Post by dpny on 2007-04-30
Unfortunately there isn't much in the way of PPC virtualization software. There is Mac-on-Linux, which will allow you to run OS X or OS 9/8 from within PPC Linux. It is in the repositories. I don't know which version is in Feisty's repositories, but when I installed it under Dapper I had to build from source to get it to support the latest version of OS X. I don't think MOL can be used to boot other PPC operating systems, like another instance of Linux, but I could be wrong.

Emulating an x86 machine on a PPC is slow. I wouldn't want to do more than very basic stuff with it,

---

### Post by 3rdalbum on 2007-05-01
I believe MoL might also support Linux as a guest OS; or if not, it's being worked on. Otherwise, you could try User-Mode Linux but unfortunately it's not anywhere near as easy to use as Virtualbox.

---

### Post by johng4 on 2007-05-02
This is actually exactly what I wanted.  My boss (a mac guy) was annoyed that I got this nice G4 iBook, and promptly nuked OS X off it.  I'm sure it'll bug him even more when I run a VM of OS X in linux on an iBook.

---

### Post by stmiller on 2007-05-03
Yes Mac-On-Linux can actually 'boot' the OS X partition inside Linux, if you are dual booting on your machine. It is then running on the actual hardware (not software-emulated) so the speed it very fast, and almost as true to being in OS X.

I had MOL working with Tiger with an iBook G4 I had (sold that machine a little while back). 

And technically qemu CAN emulate x86 on PPC Linux, but it is incredibly slow and buggy. Slow esp on a G4 machine. Unusable, even if you can get it to work.

---

### Post by galvatron1983 on 2007-05-03
Ive never tried to emulate OS X in Linux, but with OS X being my primary OS Ive have done it the other way round using virtual PC, its just super slow! 

The Macintels will probably make this a thing of the past now though, for either OS X on linux or the other way.....

---

### Post by johng4 on 2007-05-03
I'm going to wait a little bit before getting MoL, since I'm planning on a 1gb memory upgrade for my G4.  But its exactly what I'm looking for.. just hope its stable and reasonably quick.

---

### Post by LeSid on 2008-07-11
Hi John
Any experience with Mac on Linux in the meantime?
LeSid

---

