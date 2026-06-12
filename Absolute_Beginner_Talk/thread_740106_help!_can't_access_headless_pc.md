---
title: "help! can't access headless pc"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by randomjohn on 2008-03-30
I have a PC in my basement that has been running Gutsy with about 37 days of uptime, last I checked.  I rebooted because some of the updates required it.  

the PC is called black.  I also have a PC right next to it called white (also headless, also gutsy).  I can no longer access webmin on black, can't vnc into it, can't ssh into it.  in fact, the windows pc i'm on right now can't even find the pc by name.  if i hit it by ip address, the connections are all refused.

the white pc can ping black by name, but also can't ssh or telnet into it.  i normally use ssh, btw, so it was working pre-reboot.

any suggestions on what could be wrong and how i can troubleshoot short of bringing a monitor, keyboard and mouse down there?  I've already hard-rebooted a couple times...

---

### Post by Jose Catre-Vandis on 2008-03-30
I run a similar setup. every now and then I have to make a trip to the servers armed with  ancillaries in order to sort a few things out. Sounds like this is one of those occasions. Usually caused by a power outage or on my older server a kernel update that refused to boot. Sounds like black is not getting past initial boot.

May be worth a trip to ebay for some cheap second - hand peripherals.

---

### Post by randomjohn on 2008-03-30
it's a problem with corrupted inodes.  it had to do a manual fsck (or whatever it was called).  that pisses me off... any way to avoid the need for that or have it work automagically?

---

### Post by Dr Small on 2008-03-30
I have had the same problem, a few times with Mycroft. It is like network drops out on it, and then I have reboot to get back into it :|

---

