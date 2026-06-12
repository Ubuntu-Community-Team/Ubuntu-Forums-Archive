---
title: "Help With Updating LAN Driver"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by william_hunter on 2007-02-23
Hi all. First post, first task on Ubuntu. Not a good track record thus far for me :( 


Here is the problem: I can't access my network because my new build has an unsupported built in ethernet card. I have the new driver on CD, but have absolutely no idea what to do next. Help?

---

### Post by capdog on 2007-02-23
Hi william

The new driver on the CD is probably a windows driver, is it not? Not for linux... :(

What is the model number / make of your LAN card? Is it a wireless card?

---

### Post by william_hunter on 2007-02-23
No, this is from the Linux Source Forge site. I went and downloaded the tarball for the ethernet driver from there, burned to to CD on my Mac, and now I am stuck. It is supposedly a patch to the kernel, but I can't figure out how to get it working.

---

### Post by capdog on 2007-02-23
A kernel patch means that you've got the source code for your driver. In order to use it, you'll need to follow specific instructions on how to recompile your kernel, with the patch tarball... loading the driver as a module...! Is this for you? What is your knowledge of linux like?

Again, what is the model / make of your ethernet card? Maybe there is another way to get it working, without the recompile! :)

---

### Post by william_hunter on 2007-02-23
Knowledge of Linux? HAH! I am learning as I go. I just installed Ubuntu last night, and so far everything has been good, except I cant get online. If there is an easy way to do this, great. If not, I am smart enough to handle a how to. 

The ethernet card is Attansic L1 Gigabit Ethernet (sorry I didn't include this in my reply, I had to go look it up)

---

### Post by william_hunter on 2007-02-23
I think I have it fixed. I found new drivers on this site:

[http://www.hogchain.net/attansic/attansic.html](http://www.hogchain.net/attansic/attansic.html)

then I had to do a little monkeying around to get the sudo make install command work as I was not in the right directory :confused: 

:KS 

But now it is working, so thats a good thing. Not sure if what I did will come back to slit my wrists in a few days, but hey, at least now I can access the internet on the new system, right?

---

### Post by capdog on 2007-02-24
Brilliant, glad you sorted it out.

---

### Post by william_hunter on 2007-02-25
Thanks for the help and for inspiring me to think that there might just be an easier way.

---

