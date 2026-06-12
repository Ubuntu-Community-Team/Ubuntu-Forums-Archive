---
title: "ps/2 mouse not detected by feisty livecd"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by timothy_duncan on 2007-08-06
i'm trying out feisty again on a PIII 866MHz netvista box.  my ps/2 mouse is not working.  any help please..  this mouse was properly working on an older box with dapper drake.

---

### Post by asmoore82 on 2007-08-06
I've heard of this a couple times in the last week but I haven't actually seen it for myself.

I believe that this is caused by the default setup trying to be ready for all situations including
laptops whose touchpads would be PS/2. So I say that if you actually install and then customize
xorg.conf everything will work fine.

EDIT: sorry it's getting late, but there is also no reason why you couldn't tinker with xorg.conf in the
Live environment and get it working to test my theory.

---

### Post by timothy_duncan on 2007-08-06
i've tried installing without a mouse but it proved to be very difficult plus the fact that im a newbie..

---

### Post by timothy_duncan on 2007-08-06
i've seen this link at launchpad and saying:

This bug fix is now available as an official Ubuntu update.

Thanks to everyone who tried the test kernel, and reported their experiences. I'm marking this bug as fixed.


[https://bugs.launchpad.net/baltix/+source/linux-source-2.6.20/+bug/108221]("https://bugs.launchpad.net/baltix/+source/linux-source-2.6.20/+bug/108221")

How could i apply any of this updates if i can not use my mouse to install feisty..  please help

---

### Post by timothy_duncan on 2007-08-07
can someone please help me or point me to any helpful site..  this is really frustrating!

---

### Post by tgalati4 on 2007-08-07
> **timothy_duncan said:**
> can someone please help me or point me to any helpful site..  this is really frustrating!

I had the same problem with Linux Mint on a 1 GHz Celeron system.  I believe they use the same Feisty version as the base.  I tried all sorts of xorg.conf settings but no joy.  No mouse is definitely a pain.  Alt-F2 and xterm is one way to get around.

---

### Post by ugm6hr on 2007-08-07
Not sure if this works... but worth a try:

Alt+F2: **ubiquity**

Then you will have to use the Tab / Enter keys to try and select settings (but this might not be that straightforward).

Other option - use AlternateCD for install.

Once installed:
Alt-F2: **usr/bin/update-manager**
or I think Ctrl-Esc accesses the Menu (it does in Xubuntu) - then arrow keys to select Update Manager.

Hope one of those gets you up and running.

---

### Post by timothy_duncan on 2007-08-07
i've seen this link at launchpad and saying:

This bug fix is now available as an official Ubuntu update.

Thanks to everyone who tried the test kernel, and reported their experiences. I'm marking this bug as fixed.


[https://bugs.launchpad.net/baltix/+source/linux-source-2.6.20/+bug/108221]("https://bugs.launchpad.net/baltix/+source/linux-source-2.6.20/+bug/108221")

How could i apply any of this updates if i can not use my mouse to install feisty..  please help

---

### Post by ugm6hr on 2007-08-08
> **timothy_duncan said:**
> 
How could i apply any of this updates if i can not use my mouse to install feisty..  please help

Errm.... Have you tried my previous suggestions?  Maybe try explaining what happened when you tried them....  **AlternateCD will definitely work without a mouse.**

---

### Post by timothy_duncan on 2007-08-10
finally installed feisty and updated it without any mouse.  after restart, mouse is working well.  it was just a pain installling a software without a mouse..  thanks ugm6hr

---

