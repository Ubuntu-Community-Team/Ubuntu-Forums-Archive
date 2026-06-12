---
title: "peer gaurdian for amd 64 ubuntu gutsy?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by d00by on 2007-11-04
I have heard about moblock.

http://moblock-deb.sourceforge.net/

But, as I have AMD 64 bit ubuntu gutsy it may complicate things a bit. 

How do I go on about installing for 64 bit??

IS there a way to verify if it was installed properly??

I am planning to use it with deluge as bit torrent client.

IS this a good combo??  As I am a Linux virgin, kindly be gentle. :D

---

### Post by bumanie on 2007-11-04
Never had any luck installing moblock myself. In answer to your question about deluge, as it so happens, deluge has a number of plugins available. One of these a choice of getting block lists  from peerguardian, bluetack.co.uk or emule. I would choose the bluetack.co.uk as I have never been able to get peerguardian to load. You will see bluetack as a plugin option. Just paste url into the window.

---

### Post by d00by on 2007-11-04
I am using deluge with bluetack block list.

hopefully I am safe against those anti-p2p nutters! :)

How do I check if I it is blocking those IPs?

Is there a log window??

---

### Post by smartalecks on 2007-11-04
> **d00by said:**
> I am using deluge with bluetack block list.

hopefully I am safe against those anti-p2p nutters! :)

How do I check if I it is blocking those IPs?

Is there a log window??

it doesn't log blocked ips etc as far as I know
moblock for gutsy should come around anytime now, it is pretty high in demand.

if you want to have a log, azureus's safepeer plugin has a log (located in the plugin's folder). safepeer downloads blue tack's list automatically and for the moment I trust it more than deluge's plugin... (which sometimes fails to load the lists). 

to watch safepeer's log in real time you can open a terminal and do
```

tail -f path/to/log.log

```

---

### Post by d00by on 2007-11-04
I am not too hot on azureus. It is a resource hog (from what I have heard. never used it. Have been a utorrent user on my windows boot for like ever.)

---

