---
title: "Configuring Wifi-radar for WPA"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by sorryjustme on 2007-02-28
I have recently upgraded to Edgy with much pleasure. I had previously had loads of problems with wifi, but having gained new skills through all this, I am getting there, and things are moving better with Edgy. I have managed to configure my bcm 4306 wifi card using ndiswrapper, with a couple of snags, but now I want to configure it for WPA.

Network Manager seemed the most straight forward, but doesn't seem to be able to connect directly to my network when encrypted. It requests the WPA psk-key, but then fails to connect, so I was thinking of trying wifi-radar. (Could it be kind of incompatibility between the 2? I've just thought of that... Will have to  try it later...).

I understand most of the configs on wifi-radar, inputting my ESSID, the channel (06), type: Managed, key:........., but then on the WPA tag, I get stuck... I think that this is the one that is problematic: i don't know what WPA Driver to use. I have tried wext, but that doesn't seem to get me anywhere....

Any ideas?

Are there some config files I should be changing?

Thanks for reading this. Hope it's clear!

Any help much appreciated.:popcorn: 

Sorryjustme, aka The Judderman

---

### Post by mahy on 2007-02-28
Have you tried any other driver? ndiswrapper, for example? Apart from that, i've got no experience with Broadcom cards.

---

### Post by sorryjustme on 2007-02-28
Not tried that... I'm just not completely sure ofwhat they mean by wpa driver!!!

Sorryjustme

---

### Post by wieman01 on 2007-02-28
> **sorryjustme said:**
> Not tried that... I'm just not completely sure ofwhat they mean by wpa driver!!!

Sorryjustme
Try 'wext' if your are using "ndiswrapper"... That one should do the job for you.

---

