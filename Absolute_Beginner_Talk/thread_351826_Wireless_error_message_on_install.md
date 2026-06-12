---
title: "Wireless error message on install"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Strider42 on 2007-02-02
Hi,

After spending several weeks trying to resolve my installation not being able to run wireless I decided to have a go with Kubuntu Edgy.

On install I noticed the following error message:

bcm43xx: Error: Microcode "bcm43xx_microcode.fw" not available or load failed

This error message displayed twice.

Now once the OS is loaded and I run iwconfig I see the wireless card on eth1, but just cannot get it to pick up the router.  I have been through all the How To's and read practically every thread on wireless problems, but still no luck.

I'm guessing the problem might be with the initial installation and the error messages above.

System is Dell 8600 Inspiron with 1.7 Ghz Pentium M.  Everything else seems to run fine and I can connect to the router via wires.

Any ideas more than welcome.  I'm banging my head off a wall right now.

Thanks

---

### Post by dstew on 2007-02-02
Have you tried ndiswrapper?

---

### Post by Strider42 on 2007-02-02
To be honest, I haven't.  After trawling the posts in the Network forum I came to the conclusion it was a sloppy fix, and unreliable.  Is that a fair assumption?

I'll give it a go though, anything to get this dammed laptop to connect via wireless.

I'm still a little concerned over the error message though.  If someone has an answer and fix for that I would be grateful.

---

### Post by dstew on 2007-02-02
Yes, try ndiswrapper. The main problem is the "native" linux broadcomm module doesn't work with a lot of cards, probably because of variations in systems that have not been taken into account. This is because Broadcomm has not revealed to the world how the chips really work, so the people making the modules have to guess at certain things. Until the native module is fixed, ndiswrapper is the way to go. You have to remember to blacklist the native linux module, or else it will load with the kernel and interfere with ndiswrapper.

---

### Post by Strider42 on 2007-02-02
Thanks for that.  I'll unload Kubuntu and go back to Ubuntu and give ndis a go.  I was running Edgy originally, would you suggest going backwards to Dapper as a starting point?

---

### Post by teaker1s on 2007-02-02
stay with edgy,good link for ndiswrapper in my signature

---

### Post by dstew on 2007-02-02
I agree with teaker1s.

---

### Post by Strider42 on 2007-02-02
Edgy it is.

teaker I'm working my way through the link in your signature and there is a section that says comment out any line that assigns a MAC address to wlan0 in iftab.  From all my previous attempts to get this working my wireless card always showed up as eth1, without exception.

In the iftab on this install there is an entry for eth1 with a MAC address.  Would I comment that out and assume all references to wlan0 actually relate to eth1?  eth0 is my Broadcomm 4411 Ethernet card.

Thanks

---

