---
title: "Ubuntu 64 for AMD Turion laptop (hp pavilion dv8000)?"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by sqlplus on 2006-04-18
Hi all,  

I'm interested in getting started with Ubuntu but I'm not sure whether I need the 64 bit distro. I already downloaded the regular one. My laptop - hp pavilion dv8000 has an AMD Turion processor (AMD Turion(tm) 64 Mobile Technology ML-32).  Can I use either one? If so, which one is likely to be less problematic?

Has anyone had any sucess with Ubuntu on this laptop? 

Also, I tried installing with the non 64 bit version and I had trouble when the installer tried to recognize the network. Usually I am connected via wireless network. Is this a viable option to use during the installation or should a connect via a wired connection and then configure the wireless afterward?

Thanks in advance!

---

### Post by htinn on 2006-04-18
If you do install 32-bit with wireless, you should just tell the install that you will "manually configure" the network later. Then, once you have the system going, you can worry about getting your install updated via wireless if you so desire.

---

### Post by Mime on 2006-04-18
Yeah, the machine will run either one, so you can pick either build.  I've got 64bit Dapper working on my laptop which is also a Turion based HP.  The 64bit build seems a little faster to me, but if you're looking to avoid problematic stuff, then the 32bit build would be the safest choice.  There's really not that much of a good reason for running a 64bit OS on a laptop currently other than just being curious and wanting to check it out.

If your wireless is based on a Broadcom 48xx series controller like mine is, that's probably why you had trouble with it.  Making them happy in linux usually requires a extra little work.

---

