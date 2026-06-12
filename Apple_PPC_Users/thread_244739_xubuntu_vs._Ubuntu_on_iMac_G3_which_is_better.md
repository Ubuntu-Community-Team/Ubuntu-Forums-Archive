---
title: "xubuntu vs. Ubuntu on iMac G3 which is better?"
date: 2006-08-26
forum: Apple PPC Users
---

### Post by Rx7dude on 2006-08-26
should i use xubuntu on my blue and white iMac G3 instead of the regular Ubuntu?:confused:  any helpful reasons to use it or not will be appreciated!! :D =D> 
thanks!

---

### Post by linear on 2006-08-26
How much memory does it have? If < 256 MB, you might be better off with Xubuntu.

---

### Post by Rx7dude on 2006-08-26
i'm not sure! But i'm downloading ubuntu onto it right now so i guess i'll be using that!

---

### Post by Rx7dude on 2006-08-26
is there a way to install xubuntu after Ubuntu has been totally installed?:confused:

---

### Post by exjinn on 2006-08-26
yes. 

in a terminal type:

sudo apt-get install xubuntu-desktop

---

### Post by 3rdalbum on 2006-08-27
Go with Xubuntu. I really can't imagine running Dapper on one of these machines (full Breezy is bad enough... heck, even Enlightenment 16 is sluggish!)

---

### Post by COL on 2006-08-27
Hi,

I've used both desktops and according to my experience, xubuntu is quite a good interface in its own right--ie it's not just an "older machine" alternative. It is snappy and uses less system resources, so I say go with it if you find ubuntu slow.

If you are a "not so techie" like me, you can also install the xubuntu desktop through synaptics.

---

### Post by bodycoach2 on 2006-08-29
I've installed Xubuntu Dapper 6.06.1 on a Strawberry and Blueberry G3 (333 Mhz 8 gig HD. Blueberry has 256mg, Strawberry has 160mg memory, I think.

Xubuntu run faster than OS 9 did, and WAY faster than OS ten. I even followed the instructions for Java on PowerPC, and got it working perfectly.

I recommend Xubuntu on anything under 800 Mhz. I've even loaded Xubuntu on a Gateway PII, 350 Mhz, 64meg! I works. Not the fastest, but with more memory, it would do fine.

If Processor is 800 Mhz or above, use Ubuntu. Under, use Xubuntu.

> **Rx7dude said:**
> should i use xubuntu on my blue and white iMac G3 instead of the regular Ubuntu?:confused:  any helpful reasons to use it or not will be appreciated!! :D =D> 
thanks!

---

### Post by wizarddragon on 2006-08-30
I would go for xubuntu. I've put xubuntu on my ibook g3 400 (overclocked it) with 288mb and a 30gb hd upgraded on it (aka clamshell ibook/toiletseat/das kultbook). In my opinion I find xubuntu al lot snappier en faster than a normal installation of ubuntu.

---

### Post by bodycoach2 on 2006-09-03
How do you overclock the G3 processor? And, what clock speed did you get it up too? Any links for instructions would be GREATLY appreciated.

> **wizarddragon said:**
> I would go for xubuntu. I've put xubuntu on my ibook g3 400 (overclocked it) with 288mb and a 30gb hd upgraded on it (aka clamshell ibook/toiletseat/das kultbook). In my opinion I find xubuntu al lot snappier en faster than a normal installation of ubuntu.

---

### Post by jeremylh on 2006-09-03
> **Rx7dude said:**
> is there a way to install xubuntu after Ubuntu has been totally installed?:confused:
How about the reverse? Uninstall Xubuntu back to Ubuntu?

---

### Post by linear on 2006-09-03
If you started from Ubuntu, and installed xubuntu-desktop with aptitude, you could do:

```
sudo aptitude remove xubuntu-desktop
``` 
(If installed with apt-get or Synaptic, you would need to hunt down and remove individual packages that make up Xubuntu.)

If you mean starting from a system where only Xubuntu was installed, it would be:

```
sudo aptitude install ubuntu-desktop
```

---

