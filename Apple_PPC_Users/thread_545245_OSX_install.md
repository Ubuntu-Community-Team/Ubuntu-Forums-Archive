---
title: "OSX install"
date: 2007-09-07
forum: Apple PPC Users
---

### Post by CodeSamurai on 2007-09-07
Hello! I have a question.  I'm doing a little experiment and it requires that I reinstall OSX on my imac g3.  I would like to completely wipe the ubuntu install and have ONLY OSX on there.  Is there a certain way I would go about doing this besides just inserting the OSX cd and booting up? Thanks in advance!

Specs:
Imac G3
Upgraded to G4 processor 550Mhz
1GB Ram
DVD drive

Trent out

---

### Post by Auria on 2007-09-07
> **CodeSamurai said:**
>  Is there a certain way I would go about doing this besides just inserting the OSX cd and booting up? 

perhaps i missed something, but i just cant see how you expect to insall OSX without using the install disk :-k unless you have it already installed in aaprtition but your message seems to indicate the opposite

---

### Post by Dougie187 on 2007-09-07
Not sure if it works this way or not, but i would think you could potentially use gparted, and delete your ubuntu partition and then resize your OSX partition. Thought that would take alot longer then just reinstalling osx with its install cd.

---

### Post by CodeSamurai on 2007-09-07
Answer to both posts:

I have the install CDs. They are for OSX 10.3

I don't have an OSX partition.  OSX got destroyed and the only way to save some of my things was to install ubuntu, then take off the OSX partition entirely, so right now the only OS on my hard drive is ubuntu 6.10.  All I want to do is take ubuntu off completely, and install OSX on the hard drive.

Trent out

---

### Post by stmiller on 2007-09-07
This can be done with just the OS X install disc. When the install disc boots, but BEFORE starting the installation, choose the disk utility from the top menu bar. There you can erase all existing partitions, and make one HFS+ (OS X native) partition. Then save changes. Proceed with the installation and it will install just fine.

---

