---
title: "Wireless"
date: 2005-06-18
forum: Apple PPC Users
---

### Post by slingkid on 2005-06-18
Can anyone recommend me a wireless pcmcia card that will work on my Powerbook G4 running Ubuntu PPC?

I have tried

Netgear WG511 V2 Made in China and it did not recognize it at all.


Anyone with a success story? I am running Ubuntu 5.04.

---

### Post by bosshoff on 2005-06-18
Those uber expensive powerbooks don't come with integrated wireless?  Wow

---

### Post by mikelegurra on 2005-06-19
well... they do.

ubuntu doesn't recognize them, but they're there and they work like a charm, in OS X.

---

### Post by bosshoff on 2005-06-19
oh, well that's heartening.  Too bad there isn't a tool like ndiswrapper for the MAC drivers.  I think that tool is just a marvel.

---

### Post by ssam on 2005-06-23
hmmm. that card worked for me

what messages do you get in if you type
```
dmesg | tail -n 50
```
at a terminal

you could try a cisco aironet 340, they seem to work very easily for me.

sam

---

