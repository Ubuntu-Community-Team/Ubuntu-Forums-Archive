---
title: "Can't get Flash to work in Firefox"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Armor on 2007-02-01
Can't get Flash player to work. When I try to open something that uses it, it just says in middle of page where Flash should be 
"This SWF file is known is known to trigger bugs in swfdec decoder. Playback is cancelled"

Any advise?

---

### Post by mjm115 on 2007-02-01
Have you installed flashplayer-nonfree from the multiverse repositories, or just flashplayer-mozilla?  It looks like, from the error message, that just libflash-mozplugin is installed.  In firefox, if you type in

> about: plugins No space between the ':' and 'p'

what version of flash player are you running?  You may have to do a

> 
sudo apt-get install flashplugin-nonfree
sudo update-flashplugin


in a terminal to get the latest version.  Try that and see if it helps?

---

### Post by Armor on 2007-02-01
> leigh@leigh-desktop:~$ sudo update-flashplugin
Downloading...  done.
automatic installation failed due to network problems or upstream changes
 ?!

---

### Post by Armor on 2007-02-01
No it hasn't done a thing.

---

### Post by NAT2007 on 2007-07-08
I had the same problem, checked Synaptic Package Manager, found I had flashplugin-nonfree installed but was missing libflash-mozplugin, installed this latter one and now everything works fine.

---

### Post by ankitb4u on 2007-12-15
> **NAT2007 said:**
> I had the same problem, checked Synaptic Package Manager, found I had flashplugin-nonfree installed but was missing libflash-mozplugin, installed this latter one and now everything works fine.
This helped me the last post did thanks a lot

---

