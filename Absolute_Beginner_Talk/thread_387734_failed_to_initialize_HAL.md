---
title: "failed to initialize HAL"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Ubukanuba on 2007-03-18
when i sign in to the ubuntu 6.10 I immediately get an error: Failed to initialize HAL

what is this and how do I fix it??

---

### Post by HereInOz on 2007-03-18
The HAL is the Hardware Abstraction Layer, which sits somewhere between the kernel and the actual hardware, if I remember my theory correctly.  I seem to remember it has to do with allowing the system to run on various and different hardware patforms.

Thus a failure of the HAL is a fairly serious thing.  Did this happen immediately when you installed the system, or was the system working OK and then this problems cropped up at a later time?

---

### Post by Ubukanuba on 2007-03-18
definately happend after I installed extra software but not sure as I updated alot of stuff and added numerous software.  How do I reinstall clean?

---

### Post by HereInOz on 2007-03-18
Just boot from the CD in and run the install, slecting the option to erase the entire hard disk when you do so.

---

### Post by SactoBob on 2007-03-18
The only HAL that I am familiar with is that which works with madwifi drivers for Atheros based wireless cards.  you can check that out with madwifi.org.

I think that the HAL is in the restricted modules package which is in the repository if you have all sources activated.  The HAL is not open source.

---

### Post by Jaak on 2007-03-19
Try turning autologin off, reboot, login manually, if the error is gone you can turn autologin on again.

Otherwise reinstall HAL in synaptic.


Got this from: [http://ubuntuforums.org/showthread.php?p=2322992&posted=1#post2322992](http://ubuntuforums.org/showthread.php?p=2322992&posted=1#post2322992)

---

### Post by jbayone on 2007-03-19
I've gotten this error before after installing some updates.  I'm not sure which one caused it though.  My cd/dvd drives wouldn't open if they were mounted after that.  All I did was reinstall HAL through Synaptec then rebooted, and it seemed to do the trick, it's still working now and has been a month since this started.

---

