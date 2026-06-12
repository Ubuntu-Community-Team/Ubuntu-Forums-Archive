---
title: "[SOLVED] VMware Player - Ubuntu710Desktop - CA Personal Firewall"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by rh10023 on 2008-01-14
I have VMware Player installed and got the Ubuntu 7.10 Desktop virtual appliance.  This is not so much a Ubuntu question as it is a CA Personal Firewall question as I could not find a solution for this on the CA website anywhere.  

Trying to evaluate whether making the host operating system on my laptop be Ubuntu and then the Guest Operating system be Windows XP.  But I am not able to connect to any websites from the Ubuntu desktop.  I am able to ping to different websites from the Ubuntu desktop.  Ended up disabling CA Personal Firewall on the host OS side.  Now I am able to connect to websites.

Just wondering if someone can give me tips on how to configure CA Personal Firewall to allow my Ubuntu  7.10 Desktop on the VMware Player side to connect to websites from FireFox.

---

### Post by Skivache on 2008-01-14
what do you have your VMware ethernet set to?  Try setting it to Nat, then letting VMware NAT through the firewall.

---

### Post by JoshuaRL on 2008-01-14
Have you tried adding VMware Player to the whitelisted apps list in the firewall preferences?  I have CA Firewall on a relative's XP computer that I'm the tech support for but I haven't tried VMware.

---

### Post by rh10023 on 2008-01-15
> **Skivache said:**
> what do you have your VMware ethernet set to?  Try setting it to Nat, then letting VMware NAT through the firewall.

Yep set to NAT.  Can ping to internet sites that allow ping, but cannot connect to them with firefox.

---

### Post by rh10023 on 2008-01-15
> **JoshuaRL said:**
> Have you tried adding VMware Player to the whitelisted apps list in the firewall preferences?  I have CA Firewall on a relative's XP computer that I'm the tech support for but I haven't tried VMware.

Should I have VMware player set to safe zone or restricted zone?

Tried adding VMware player to application zone list, but for some reason CA Personal Firewall would not take.

---

### Post by JoshuaRL on 2008-01-15
You'll probably have to disable it before you'll be able to add any applications if I remember right.  Probably for security reasons it doesn't let you do that while it's active.

---

### Post by rh10023 on 2008-01-15
> **JoshuaRL said:**
> You'll probably have to disable it before you'll be able to add any applications if I remember right.  Probably for security reasons it doesn't let you do that while it's active.

I gave up trying to tweak.  Won´t say what I did but got things working.

---

### Post by JoshuaRL on 2008-01-15
Are you sure?  If you are able to post what you did it may help others with the same problem.  Plus you get to mark the thread as solved.

---

### Post by rh10023 on 2008-01-16
> **JoshuaRL said:**
> Are you sure?  If you are able to post what you did it may help others with the same problem.  Plus you get to mark the thread as solved.

I had the CA Personal Firewall set at the highest security setting for both the Restricted and Safe Zones.  I ended up bringing both zones down to the medium security setting to get things working.  I could not get things set right to let VMware player to punch through the firewall.

---

