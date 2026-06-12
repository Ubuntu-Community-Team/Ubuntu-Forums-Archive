---
title: "problems with installing new programs [Resolved]"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by forrestguide on 2007-03-04
Hi,

A new and interesting problem has arisen. I tried to install madwifi and firestarter (through terminal - *ex: sudo aptitude install firestarter*).  In both cases, I found that I was instructed to put the original cd xubuntu 6.10 yada-yada- into the cd and press enter.  
What happened is that in order for the install to take place I had to continue to hold down enter and wait for the intall to end. I finally put a weight on the key and walked away. :popcorn: 

however, the install never completed.  It hung up on 99% done then quit.  what is my solution.  has this ever happened before? I'm slowly installing updates throught a dial-up. Will these help me out?

Thanks in advance,

Greg

---

### Post by aysiu on 2007-03-04
So what exactly is the issue? You don't want to install from the CD... you want to install from the internet instead? If so, press Alt-F2 and type ```
gksudo synaptic
``` Then go to **Settings > Repositories** and uncheck the box next to the CD-ROM source. Then click **Reload**.

---

### Post by forrestguide on 2007-03-05
> **aysiu said:**
> So what exactly is the issue? You don't want to install from the CD... you want to install from the internet instead? If so, press Alt-F2 and type ```
gksudo synaptic
``` Then go to **Settings > Repositories** and uncheck the box next to the CD-ROM source. Then click **Reload**.

I don't know if I need to install from the cd or not.  That was one of the problems, it kept telling me to put in the cd and press enter.  I wasn't sure why I was being told to do the cd thing.

Greg

---

### Post by forrestguide on 2007-03-06
> **aysiu said:**
> So what exactly is the issue? You don't want to install from the CD... you want to install from the internet instead? If so, press Alt-F2 and type ```
gksudo synaptic
``` Then go to **Settings > Repositories** and uncheck the box next to the CD-ROM source. Then click **Reload**.


Thank you so much for the help.  It was such a breeze.

Pax,

Greg

---

