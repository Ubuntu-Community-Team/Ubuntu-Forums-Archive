---
title: "how do I test my wireless card in Ubuntu?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by buckety on 2007-09-11
hi there,

Several people have suggested that I can find out if my wireless card will work in Ubuntu by testing it first on the live CD.

How do I do this? I no longer have the set-up disk that came with the wireless card: do I need it? I'd like to make sure that my wireless will work before installing Ubuntu on my hard drive.

If you've got instructions for me, please deliver them as layperson-y as you can. I've been running Mepis for a few years now, but I'm still not up on the lingo.

Thanks!
Buckety.

---

### Post by bmeyer on 2007-09-11
> **buckety said:**
> hi there,

Several people have suggested that I can find out if my wireless card will work in Ubuntu by testing it first on the live CD.

How do I do this? I no longer have the set-up disk that came with the wireless card: do I need it? I'd like to make sure that my wireless will work before installing Ubuntu on my hard drive.

If you've got instructions for me, please deliver them as layperson-y as you can. I've been running Mepis for a few years now, but I'm still not up on the lingo.

Thanks!
Buckety.

What brand is your card?  Most will work without any sort of CD.  The only reason you'd need a CD is if your driver isn't supported already by Ubuntu in which case you'd need to install the driver off the CD with ndiswrapper (I won't go into those details unless a problem actually comes up).

---

### Post by buckety on 2007-09-11
hey bmeyer,

My wireless card is a Motorola, WN825G.

-Buckety.

---

### Post by rsambuca on 2007-09-11
[Here is a list of supported cards]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported").

---

### Post by rsambuca on 2007-09-11
According to that list you will need ndiswrapper.

---

### Post by bmeyer on 2007-09-11
> **rsambuca said:**
> According to that list you will need ndiswrapper.

He's probably right.  If your card doesn't work right away, install the ndiswrapper and ndiswrapper-utils with Synaptic.  Insert your card's driver CD and find your specific model's .inf file (the driver).  Use the ndiswrapper-utils interface to install that file.  You might need to reboot, but it'll work eventually.

But, you're using the Ubuntu Live CD right?  Not sure how that works with a Live instance -- might have to do the install first.

---

### Post by hyper_ch on 2007-09-12
Here's a howto for ndiswrapper:  [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I have not tested it myself as my card is recognized out of the box...

---

