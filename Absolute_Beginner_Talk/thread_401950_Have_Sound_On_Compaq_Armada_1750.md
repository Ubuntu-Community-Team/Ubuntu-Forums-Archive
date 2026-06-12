---
title: "Have Sound On Compaq Armada 1750"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by chemtut on 2007-04-05
YEEEEEEEEEEEEEESSSSSSSSSSSSSSSSSSSS !!!!!!!!!!!!!!!!!!!!!!
having tried umpteen distros on this old computer and none of them recognised the sound card I did not think that I would ever hear sound. BUT,
Iinstalled Mepis(yes I know that this is ubuntu,but bear with me),and I plugged in(before boot) a Trust usb stereo speaker(ten pound tos from Tesco uk) and I am now listenning to some wonderful sound!

:)My question is quite simple-----Why and how ??????

---

### Post by crispy_420 on 2007-04-05
Kernel update or alsa update are my guess?

---

### Post by aeb1 on 2007-04-07
I have sound on this Armada 1750. I also have wired and wireless connectivity & can play movies.

How? The key is USB. First, upgrade the microprocessor to a 500Mhz PIII. The compaq Armada CANNOT handle a faster one without losing the built in PC card functionality.


[http://www.wireball.com/armada_1750_review.htm](http://www.wireball.com/armada_1750_review.htm)

Upgrade the RAM. I use the 256Mb SODIMM.

Sound: I bought & used the cheapo USB plug-in sound card. $5.00 on eBay. Ubuntu recognized it, but you must configure the rest of the programs to use the ALSA USB device. This applies to the VLC video/movie player too.

Wireless: USB to the rescue: I used the GIGAFAST USB wireless card. Ubuntu also recognizes it out of the box. You still have to set up you SSID and connectivity. $15.00 at geeks.com

Wired Ethernet: You must use the ONE PORT Xircom PCMCIA card that comes without the dial up modem. The usual Xircom card will cause conflicts and won't work. $3.95 on eBay. 

There you have it. With the addition of a larger hard drive, I have the functionality I need at a fraction of the cost & have recycled a perfectly good computer!

:guitar:

---

