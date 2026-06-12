---
title: "Powermac G4 + Radeon 9700 Pro issue"
date: 2010-08-11
forum: Apple Hardware Users
---

### Post by Thingi on 2010-08-11
Hi, I've got a Powermac G4 with a 9700 Pro card.

I can enable DRI and AIGLX in Lucid on a fresh install with no xconfig at all after I've disabled KMS by adding 'options radeon modeset=0' to '/etc/modprobe.d/radeon-kms.conf'.

The problem is that if I run an auto update I get the dreaded blank screen of death when X tries to start. If I then remove 'options radeon modeset=0' I can get X working again but obviously I'm stuck with the frame-buffer driver and no compiz shinyness. 

I've created my own xorg configs with various different options but it doesn't make any difference :-(

So the question is this - how do I 'blacklist' any xorg and ati driver updates because I'm sick and tired of messing with X.

thingi

---

### Post by linuxopjemac on 2010-08-11
Maybe this helps:
[http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx](http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx)

---

### Post by Thingi on 2010-08-11
> **linuxopjemac said:**
> Maybe this helps:
[http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx](http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx)

That's a darn good xorg config file.... Mine is almost identical already :-) 

The only differences between ours config files is that mine is set to AGP x2 (max sawwtooth mobo supports), AGP fast writes disabled (they definitely lead to instability) + I haven't got DRI explicitly set because ubuntu's automagical xconfig logs were indicating that it was being set by default (well it is was on a non updated install). 

I'll give the DRI setting a try but I don't hold out much hope - The latest ati-free driver that I've got working was from April ish, all the later ones fail.

Thinking about it I did do one more thing - I added 'modprobe radeon' near the very bottom of my gdm init script to fix a race condition so I might try taking that out again. 

There is also one more odd thing I'm getting and that my card seems to think that my VGA port is a S-Video port in my Xorg logs - but on a fresh lucid it didn't seem to matter and I still had accelerated 3D working. 

Will try again and post the logs. 

many thanks for your linky :-)


thingi

---

