---
title: "Reinitializing hard drive"
date: 2007-12-19
forum: Apple PPC Users
---

### Post by schuhjm on 2007-12-19
Hi,

Well, I'm not really even a newbie to linux of any flavor, but I have a question.

I just bought an old Mac G4 that came with a Quantum Fireball 30G drive with Ubuntu installed.  It boots to the password prompt, but I have no password, nor knowledge of Linux.

I want to recover this drive so I can use it with my familiar Mac OS, or install it in my old G3 so I can sell, or donate a working machine.

I can't see the drive at all in OSX.  I can't reformat or initialize it or recognize it in any way except when holding the option key during machine boot.  I've tried every permutation of the jumpers on the drive (Master/slave/CS), and have tried booting to two different OS install disks (10.2, and 10.4).

Is there anything with Ubuntu that prevents me from seeing this disk with another OS?
If so, how do I get past that without knowing the login password?

Any help appreciated.

Jeff

---

### Post by raysaunders on 2007-12-20
Presuming that your 10.4 install disk boots to the point where you have already chosen the preferred language for installation and you now have a top menu bar on the screen, you will need to select the drop-down menu item which gives you direct access to Disk Utility which is included on the install CD. Disk Utility can then be used to reinitialise the hard disk to Mac's familiar HFS+ (journaled) format, erasing the entire Linux installation in the process.


Trust this helps.

---

### Post by schuhjm on 2007-12-20
Well, that did do the trick.  In my own defense thought, I had attempted to use Disk Utility in numerous times, when booting from a working HD, booting from maintenance CD's, and the like.  In my other attempts, the disk was visible, but greyed out, and couldn't run any erase, or initialize on it.

Anyway, thanks 

Jeff

---

