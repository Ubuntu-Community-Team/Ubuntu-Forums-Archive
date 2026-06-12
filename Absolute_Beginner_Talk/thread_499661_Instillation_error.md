---
title: "Instillation error"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by ender8282 on 2007-07-12
Ok I have been trying to get fiesty up and running for a while now and it keeps failing to install.  
I just updated the bios on my mobo (asus m2n-mx) in the hope that it would help things, but I still get error messages when trying to install the system (after partitioning).  The error that I get (on VC4) is:

```

apt-get[27341]: segfault at 000000002063854a rip 00002b7fe885cc51 rsp 00007fffc24b2010 error 6
base-installer: error: exiting on error base-installer/kernel/failed-package-install

```

If anyone has any suggestions I would really appreciate any help.  I have tried 2 different Kubuntu DVDs and one Ubuntu DVD.  Tried both graphical and text install.  As we speak I am trying to install a command line system.  If I get any more information I will add to the post.  

Thanks

---

### Post by ender8282 on 2007-08-09
Ok I never got any help but I was able to get kubuntu up and running.  In the end I picked up a graphics card and stopped trying to use the onboard graphics.  I read a couple of other posts about people having problems with integrated graphics that use sys memory.  
Again I dont know if this was what really fixed things or not.  I still had to install a command line system and then did a sudo apt-get install kubuntu desktop.  It still hung during regular installs.

---

