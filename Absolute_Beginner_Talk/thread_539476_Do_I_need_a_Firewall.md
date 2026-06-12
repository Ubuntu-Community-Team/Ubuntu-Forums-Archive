---
title: "Do I need a Firewall?"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by bill45 on 2007-08-31
While on Dail-up, I take it a firewall (both incoming and outgoing) is recommended.  Anything GUI similar to ZA available?


I can't seem to find the GUI file manager.  I seem to recall it had a weird name in 6.06.  Where is it?

Thanks
Bill

---

### Post by oilchangeguy on 2007-08-31
> **bill45 said:**
> While on Dail-up, I take it a firewall (both incoming and outgoing) is recommended.  Anything GUI similar to ZA available?


I can't seem to find the GUI file manager.  I seem to recall it had a weird name in 6.06.  Where is it?

Thanks
Bill

do you mean dial-up? and ubuntu has a built in firewall. it's called iptables. the gui (firestarter) is not installed by default. as it's not really needed.

---

### Post by orb9220 on 2007-08-31
Ubuntu comes with iptables which is the firewall by default. 

The gui that controls iptables is called firestarter.

For most the default settings in iptables is sufficient for most and does not require you to do anything. I have never installed firestarter or touch the default iptables and have not experience any problems.

But for specific configurations and situations you can install firestarter from synaptic.

---

### Post by dpar on 2007-08-31
[http://ubuntuforums.org/showthread.php?p=3088372](http://ubuntuforums.org/showthread.php?p=3088372)

---

### Post by fastpakr on 2007-08-31
iptables does NOT block anything by default.  At all.  You can ping an Ubuntu machine from another box without opening anything up.

It may be installed, but it is not configured to block.  This is frequently conveyed incorrectly on the forums.  If you want to configure it, you can do it in the CLI or install firestarter, but do NOT convince yourself that you're firewalled out of the box.

---

### Post by Tiekyl on 2007-08-31
I don't know how good this is, but it gave me good results on a fresh install. Does it mean anything?

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by bill45 on 2007-08-31
OK - downloaded Firestarter and installed.  I watched the configure msg during install

Very good, feel better now

thanks
Bill

---

