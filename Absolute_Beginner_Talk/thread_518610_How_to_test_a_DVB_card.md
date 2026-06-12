---
title: "How to test a DVB card ?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by jc508 on 2007-08-06
Setup Fiesty 7.04 on AMD64 dual core
DVB is 'DVICO Fusion HDTV DVB-T Dual Digital 4'

I know the card is a bit new and doesn't have real driver support yet but
I have been following the instructions at 
[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop)
in general and for the card [http://fremnet.net/article/228/dvico-fusionhdtv-dual-digital-4-under-linux](http://fremnet.net/article/228/dvico-fusionhdtv-dual-digital-4-under-linux)
(but this site is down at the moment)

By all accounts one should test the installation of the card before messing with MythTV.
Can anybody suggest how ??

Being eager I tried Myth anyway and during Backend setup it finds (I think) "DVB DTV capture card (v3.x)"
with frontend 'Zarlink ZL10353 DVB0T Subtype DVB-T' whatever that means
but it can never find any channels just gets "Timeout Scanning - no signal"

I have it connected to an antenna that is running a HDTV perfectly well.

So are there any (simple) diagnostic routines that could be used to test the driver and card??

Thanks in advance
JC

---

### Post by pyxu619 on 2007-08-06
you can give this website a test and see if you have any luck

[http://tvtime.sourceforge.net/](http://tvtime.sourceforge.net/)

:)

---

### Post by jc508 on 2007-08-06
Thanks but that has an even more foreign list of supported cards.
Alas the DVICO doesn't actually list what chip its using.

I have also just experimented with Kaffeine and that too seems happy with the card i.e. says its there. But in scanning the channels all are 0% and SNR 0 in either auto mode or giving it something.

Thanks

---

### Post by pyxu619 on 2007-08-06
you can try using lspci in the terminal and get a detail list of the hardware in your computer. Try to find the video capture card

---

