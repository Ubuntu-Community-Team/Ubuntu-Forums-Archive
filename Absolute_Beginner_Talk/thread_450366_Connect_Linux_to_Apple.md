---
title: "Connect Linux to Apple"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-05-21
OK, got this Linux machine running really. Now, I'd like to connect to OSX & vice versa through my Linksys wrt54g router.

---

### Post by cknoblock on 2007-05-21
Hello,

1. Connect Linux machine and Apple machine to network.
2. ???
3. Profit!

Seriously, is your Linux machine on the network already? Or do you need to know how to connect to a wireless network?

-ck

---

### Post by Atomic Dog on 2007-05-21
I think he's talking about setting up some shares.  I have never done it, but I suppose it would be a cool thing to have a shared folder on both mechines to transfer files between the two.

---

### Post by Najand on 2007-05-21
Use "netatalk" in the repositories. All you have to do is install it through repositories (apt-get), then kick it off if it&#8217;s not running already (/etc/init.d/netatalk start) and you can mount your home directory immediately from Mac OS X.

---

### Post by ruy_lopez on 2007-05-21
Better to use ssh, just set up remote login on the OS X sharing preferences, then you can mount any folder from the mac box onto your Ubuntu desktop, using -->Places-->Connect to server-->SSH. Then from the dialogue enter the Mac's hostname, folder you want, username, password.

---

### Post by Atomic Dog on 2007-05-25
> **ruy_lopez said:**
> Better to use ssh, just set up remote login on the OS X sharing preferences, then you can mount any folder from the mac box onto your Ubuntu desktop, using -->Places-->Connect to server-->SSH. Then from the dialogue enter the Mac's hostname, folder you want, username, password.

Actually duh!  I feel stoopid for not thinking about this.

---

