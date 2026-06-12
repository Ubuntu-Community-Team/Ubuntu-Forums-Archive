---
title: "How to add WiFi connection on my laptop?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by brownbagel on 2008-02-27
I have a laptop from LG where I'm testing Ubuntu. How do I add a WiFi connection in Ubuntu 7.10 (i'm not able to find any options from network setup)? Haven't yet installed Ubuntu, but running from LiveCD. What should I do to get my network connection working?

Thanks :-)

---

### Post by mwanstall on 2008-02-27
What model laptop is it? You might need to use NDISwrapper depending on the wifi card.

---

### Post by ugm6hr on 2008-02-27
We need to know what wifi card you have.

From the LiveCD, enter the following command and copy and paste the output here:
```
lshw -C network
```

Note the capital C

---

### Post by brownbagel on 2008-02-27
LG E500-GAPHHV

Here's the wifi card information:
       
description: Ethernet controller
product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
vendor: Atheros Communications, Inc.
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0

---

### Post by jonnywombat on 2008-02-27
There is a how at this thread for installing atheros cards

[http://ubuntuforums.org/showthread.php?p=4295874&posted=1#post4295874](http://ubuntuforums.org/showthread.php?p=4295874&posted=1#post4295874)

jonny

edit.. you might need to scroll up a few posts to find the how to

---

### Post by ugm6hr on 2008-02-27
> **brownbagel said:**
> 
product: AR5006EG 802.11 b/g Wireless PCI Express Adapter

Notice there is no driver listed in your output.

Read this first: [http://ubuntuforums.org/showthread.php?p=4259805#post4259805](http://ubuntuforums.org/showthread.php?p=4259805#post4259805)

Then check in Windows what your card is identified as (i.e. is it AR5007EG?)

If so, it can be made to work (with ndiswrapper), but only after installation.

---

