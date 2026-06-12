---
title: "New to this World"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by kgun2k1 on 2007-03-23
I am new to all of this Linux stuff, but I am fed up with Windows.  If I tell everyone what I am hoping to accomplish, can you guys let me know if it is doable, or if I should make adjustments to my setup?

Computer #1:
  Dell Dimension 8250
  2.66 GHx Penitum 4
  525 MB RAM
  60 GB HD (will upgrade to about 250 GB)
  CD-RW disk drive
  Currently running Windows 2000, but can also do XP Pro
  Hardwired to router

Computer #2:
  Gateway CX-Series Tablet PC
  Don't recall the specs, but they are similar to Computer #1
  CD-RW/DVD disc drive
  Running XP Tablet
  Wireless G to router

Computer #3:  (Have not purchased yet, but I will...)
  Apple iMac
  2.0 GHz Intel Dual Core
  1 GB RAM
  160 GB HD
  SuperDrive
  Would be hardwired to router

Belkin Wireless N Router

Xbox 360 hardwired to router

Nintendo Wii wireless to router

That is pretty much what I have (or will have).  I was wanting to turn Computer #1 into a server to hold all my music, videos, pictures, documents, and everything else like that (not programs).  Would there be any issues getting all this connected using Ubuntu Server on Computer #1?  Is it a chore?  I am not at all familiar with Linux, so I don't want to stumble out of the gates here.

Thanks in advance for any advice that might be offered!

Ken

---

### Post by jimbo2150 on 2007-03-23
The easiest way is probably windows shares. You can do that either with Windows or Ubuntu. They both support it.

If you want to set up an ftp or http server it can be a little more involved.

If you use shares, make sure your computers are on a router behind a firewall. You don't want others accessing your shares. :)

---

### Post by kgun2k1 on 2007-03-23
To illustrate my lack lack of knowledge, what is a "windows share"?

---

### Post by afljafa on 2007-03-23
Might I suggest for the server you use SMEServer from contribs.org. It will do file, web, print and mail serving out of the box. No tinkering required.

If this is going to be an all nix environment I would opt for nfs sharing as it`s performance will blow windows file sharing (samba) away.

---

### Post by kgun2k1 on 2007-03-23
> **afljafa said:**
> Might I suggest for the server you use SMEServer from contribs.org. It will do file, web, print and mail serving out of the box. No tinkering required.

If this is going to be an all nix environment I would opt for nfs sharing as it`s performance will blow windows file sharing (samba) away.

I am starting to become afraid of what I am getting into.  "Nix environment" and "nfs sharing" don't mean anything to me.  Would I be better off just installing a minimal version of Windows (2000 or XP) on Computer #1 and just leave it at that?

---

### Post by afljafa on 2007-03-23
> **kgun2k1 said:**
> I am starting to become afraid of what I am getting into.  "Nix environment" and "nfs sharing" don't mean anything to me.  Would I be better off just installing a minimal version of Windows (2000 or XP) on Computer #1 and just leave it at that?

Like I said - take a look at contribs.org - The distro is designed to accomodate those that require a robust server environment with little effort. There are some really great howtos available and the forums are a great source of information and help.

---

### Post by Wardazo on 2007-03-23
Hi

You might want to try looking at Samba ([www.samba.org)](www.samba.org)). Its basically a file server that works on a linux box (ie Ubuntu). Windows machines can upload and download stuff from it easily.

This is a very clear tutorial about setting it up:

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

A word of advice. You mention "Ubuntu server". If you are new to Linux, you are better installing the standard Ubuntu as it is more intuitive coming from windows background - it has a desktop and lots of gui apps. You don't need Ubuntuserver edition to use ubuntu as a server... just some software like samba

good luck

Ward

---

### Post by lyceum on 2007-03-23
As you are new, I would recomend looking at the links in the top line of my signature. Psycocat's page is a must read for any new user. The others are also very helpful. The FOSS world is a little different that Windows, and it is always good to look before you leap ;)

good luck, have fun and yes, everything you mentioned is posible. Sounds like a good set up 

:guitar:

---

