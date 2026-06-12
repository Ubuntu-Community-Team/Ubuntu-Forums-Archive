---
title: "wlan connection lost (after suspending)"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by winterg on 2008-04-21
Hello, I installed Ubuntu "Gutsy Gibbon" on my notebook this weekend. I got Wlan (with wpa) working but when I suspend my notebook and wake it up, my connection is gone. When this happens and I open 'network tools', all of a sudden there's this wireless interface named (wlan0:avahi) :confused: i.e. besides the regular (wlan0).

It seems that [erasing my wpa key -> pressing OK -> filling in wpa key -> pressing OK], is enough to get it up again (wlan0) and to get rid of (wlan0:avahi), which is a bit annoying :D

---

### Post by sillyxone on 2008-04-21
if you're using networkmanager, perhaps give Wicd a try, I found it's much better and easier to use.

---

### Post by jnorthr on 2008-04-21
this situation happens to most of us. It's better not to let your system suspend or sleep until ubuntu fixes the wakeup logic after a suspend.

---

### Post by sillyxone on 2008-04-21
> **jnorthr said:**
> this situation happens to most of us. It's better not to let your system suspend or sleep until ubuntu fixes the wakeup logic after a suspend.

since using Wicd, I don't have the problem of loosing wireless after suspending anymore but Wicd sometimes stopped the laptop from sleeping. I have to add a command to kill Wicd into suspend script, the new version of Wicd (not the one in Synaptic) has fixed it.

---

### Post by winterg on 2008-04-22
I just found out that when powering Off and On, the same problem occurs...

---

### Post by winterg on 2008-04-22
Can this be some wlan driver issue? 
Which other drivers can I try? if there are any :)

Device manager info:
RT2561/RT61 802.11g

---

### Post by winterg on 2008-04-26
> **sillyxone said:**
> since using Wicd, I don't have the problem of loosing wireless after suspending anymore but Wicd sometimes stopped the laptop from sleeping. I have to add a command to kill Wicd into suspend script, the new version of Wicd (not the one in Synaptic) has fixed it.

I'm trying Wicd now and the problem of loosing wlan after suspending (and powering off/on) seems to be solved...
_BUT_ now it looses wlan connection after just being online for a while :(

**So some other CLUES NEEDED!!** please :)

---

