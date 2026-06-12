---
title: "Ventrilo no sound"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by oak_one on 2008-03-10
Im pretty new to linux but iv got the install to work fine and it connects to the server fine, but when i connect it comes up with this error

Failed to get encoder for specified Codec.

Unable to initialize outbound codec (GSM 6.10 - 22 KHz, 16 bit): Unable to find the specified codec.


The sound on everything else with wow, other games, everything works fine except ventrilo
im running a Dell XPS m1710

---

### Post by Oldsoldier2003 on 2008-03-12
> **oak_one said:**
> Im pretty new to linux but iv got the install to work fine and it connects to the server fine, but when i connect it comes up with this error

Failed to get encoder for specified Codec.

Unable to initialize outbound codec (GSM 6.10 - 22 KHz, 16 bit): Unable to find the specified codec.


The sound on everything else with wow, other games, everything works fine except ventrilo
im running a Dell XPS m1710

You need to install the codecs in your ventrillo/wine installation.

Google for the codec, then install it under wine and follow the windows FAQ at the ventrilo website and all should be well

---

### Post by jprophet420 on 2008-03-17
Hmm, the problem seems to be finding the codec. I find it in a codec pack called 'ace codec pack 6.03' but that wont install properly (via wine of course). I would like to find the vent codecs packaged somewhere but i cant seem to do that.

the vent faq tells me to install them thru control panel but i dont think that will work, as a matter of fact im pretty sure about that. does anyone know whaere i can find the codecs, or tell me what codec pack they used? thanks.

---

### Post by jprophet420 on 2008-03-17
got it.
here is the walkthru:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3936&iTestingId=5557](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3936&iTestingId=5557)

here is the codec (the one in the walkthru is pay-for):
[http://downloads.lucidcoding.com/msgsm32.acm](http://downloads.lucidcoding.com/msgsm32.acm). 

this solves the codec issue.

---

