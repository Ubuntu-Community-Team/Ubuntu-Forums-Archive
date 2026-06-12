---
title: "PowerMac G5 Sound Issues - Ubuntu 11.04"
date: 2011-11-13
forum: Apple Hardware Users
---

### Post by kgllewellyn on 2011-11-13
Hi there,

First off, I'll like to shout a 'Hello' to everyone on this forum as this is my first post. 

I've been having a bit of a problem getting sound working on my PowerMac G5 (1.6Ghz Single Processor) running Ubuntu 11.04. I've inserted snd-powermac and snd-aoa into /etc/modules with no luck. 

The sound card is detected by the system as  'K2 KeyLargo Mac/IO'. I'd be really grateful for any help on this. 

Cheers,

-Kai

---

### Post by kgllewellyn on 2011-12-01
Does anybody have any suggestions?

---

### Post by linuxopjemac on 2011-12-01
I own an iMac G5 onto which I installed MintPPC 11, which has a 3.1 kernel. I did not have sound either out of the box. I added the following kernel modules to /etc/modules. Maybe it is of help. I am not sure whether these two machines use the same audio card.

```
snd_aoa_i2sbus
snd_aoa_fabric_layout
snd_aoa_codec_tas
snd_aoa_codec_onyx
```

[http://alsa.opensrc.org/Aoa](http://alsa.opensrc.org/Aoa)

---

### Post by rsavage on 2011-12-01
You beat me to it linuxopjemac!  It's nice to see you active again on the ubuntu forum!
 
EDIT: I've now included a sound problem solving section into the instructions here [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1) .

---

### Post by linuxopjemac on 2011-12-01
> It's nice to see you active again on the ubuntu forum! 
Thank you. I will help if I can.

---

