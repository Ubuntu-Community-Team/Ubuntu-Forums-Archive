---
title: "[SOLVED] .ISO Image"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Fraser from Scotland on 2008-01-07
Is there any way of creating a .ISO image of my whole OS (Gutsy) it's because my laptop is going to get fixed and I don't want to have to totally install Gutsy and everything I've put on it. I read somewhere instead of backing up you can just create an .ISO of the whole system. Any ideas?

---

### Post by stalker145 on 2008-01-07
> **Fraser from Scotland said:**
> Is there any way of creating a .ISO image of my whole OS (Gutsy) it's because my laptop is going to get fixed and I don't want to have to totally install Gutsy and everything I've put on it. I read somewhere instead of backing up you can just create an .ISO of the whole system. Any ideas?

I've never tried it, but [this looks promising]("http://ubuntuforums.org/showthread.php?t=35087").

---

### Post by philinux on 2008-01-07
[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)

---

### Post by Fraser from Scotland on 2008-01-07
thnaks for the responses. :)

---

### Post by stalker145 on 2008-01-07
> **philinux said:**
> [http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)

I like that! I'm goint to try that when I get home.

---

### Post by Prospero2006 on 2008-01-07
Let's say your os is on /dev/hda

Then you hook the sucker up to a separate partition somewhere and use dd

dd if=/dev/hda of=/mydirectory/mybackup.iso


Now, if you create an iso file like that you'll need to restore it to a computer with
identical architecture.


Prospero

---

