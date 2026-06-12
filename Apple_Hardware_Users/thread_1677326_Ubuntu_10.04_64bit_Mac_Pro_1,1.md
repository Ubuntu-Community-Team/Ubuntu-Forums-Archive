---
title: "Ubuntu 10.04 64bit Mac Pro 1,1"
date: 2011-01-28
forum: Apple Hardware Users
---

### Post by Odin Overland on 2011-01-28
I did some searching and could not find much to help me with my issue.  I am trying to install Ubuntu 10.04 64 bit on its own hard drive in a separate bay on a Mac Pro 1,1.  I have Mac OS installed on the first drive right now (mainly because I can't successfully load any other OS on this particular machine).

I have tried doing booting with and without rEFIt, result is the same.  After installing Ubuntu, I cannot boot up - just get the flashing underscore.

I found this [https://help.ubuntu.com/community/MacPro]("https://help.ubuntu.com/community/MacPro") - but it isn't as well documented as some other community pages - found no help here.

If anyone could help me out I would appreciate it.  But definitely need 64 bit because I have a lot of RAM in here.

---

### Post by gordintoronto on 2011-01-28
Look at bootoptions in the community docs.

---

### Post by Odin Overland on 2011-01-31
Never mind - boneheaded mistake on my part.  I ignored the setup of GRUB thinking that since it had its own hard drive it would not need GRUB.  Instead it was automatically installing it to my Mac OS hard drive and could not load its own hard drive.

Der...

Anyway, it is installed now.  Hopefully soon I won't need that Mac OS hard drive at all.

---

### Post by pafufta503 on 2011-02-01
you will want to keep, and continue to upgrade, OS X.  this is because all firmware updates are done this way.

---

### Post by sdholbs on 2011-08-26
I had this same issue with a new macbook air got it to work by pressing f6 and enabling "nomodeset".  More details are available here:

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

Have some patience (but don't wait any more than ~5 min for any one screen to load), the startup was very slow for me booting from the cd (clicking "Try ubuntu").

Also, once booted up from the CD, I used these instructions to prepare for ubuntu's installation:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

