---
title: "Lost wireless connections"
date: 2008-05-09
forum: Arch and derivatives
---

### Post by K.Mandla on 2008-05-09
Was there an update that would have affected wireless connections? I lost two machines that were otherwise working after a recent update. In both cases they boot but can't reach the router (no encryption key) and are assigned dummy IPs. 

After a while it seems they connect, then fall again, this time losing their wireless extensions to the device name (in other words, on both machines iwconfig says they have no wireless capability).

Rather bizarre. I'd love to chalk it up to one particularly fruity installation, but the fact is it's happened on two machines running distinctly different hardware, so I think it's something else.

Anybody seen anything that might explain this? Did I overlook a configuration change or something?

Thanks in advance.

---

### Post by DrOlaf on 2008-05-09
I ran my usual pacman -Syu last night, and my notebook's wireless connection is still fine.

---

### Post by Dr Small on 2008-05-09
I upgraded my system 2 days ago, and noticed there was some new wifi packages, yet my dlink wireless still works.

Edit,
Have you just tried dhcp so you could get a connection, to see if it will stick?

---

### Post by K.Mandla on 2008-05-09
Hmm. Odd. Each machine would boot, but not connect to the router. Each got dummy IPs, as is normal in that situation. 

After a minute or two (or perhaps longer) they would be reassigned IPs, I assumed when the dhcpcd daemon reattempted a connection. Usually they would connect that time. Then they would fall again, usually only after a few minutes.

Then ifconfig would drop the connection from its active list, and iwconfig would list the interface, but say it had no wireless extensions. I tried restarting networking, downing the connections and reupping them. I also tried manhandling them with iwconfig, but it wouldn't do anything since the interfaces supposedly had no wireless extensions.

Again, this is on two different machines, each with distinctly different hardware. I'm mystified, personally, although it won't matter after about 12 hours, since I'm returning my wireless router to the store. It's still terribly strange though. :-k

---

### Post by Dr Small on 2008-05-09
Maybe the router died then. Things like that do happen, I guess.

---

### Post by K.Mandla on 2008-05-09
I had thought about that too, but I reinstalled Debian on one machine, and it worked fine. I don't know. Perhaps something I had set on both machines was wacky. I've been known to create wacky systems. :roll:

---

