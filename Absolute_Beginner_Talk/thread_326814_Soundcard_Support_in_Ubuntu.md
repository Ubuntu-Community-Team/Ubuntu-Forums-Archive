---
title: "Soundcard Support in Ubuntu"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by dancallo on 2006-12-28
I'm new to Ubuntu.  I just installed Ubuntu 6.06.1 LTS (Dapper Drake) yesterday on my HP Pavilion 8485Z, 450 MHz, P3 system that used to run Redhat Linux Server.

When I installed Ubuntu, I had no problems with the exception that my sound card appears not to be supported by default in this OS.  I have a Rockwell Riptide Audio/Communication Combo card, which combines support for audio as well as the integrated modem in that system.  The manufacturer's web site is [http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph07114&lc=en&cc=us&dlc=en&product=59261&lang=en#N366](http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph07114&lc=en&cc=us&dlc=en&product=59261&lang=en#N366).

Does anyone know if there are any Linux drivers for this card, and, if so, how I can go about configuring Ubuntu Linux for this card in my system?

I would appreciate any assistance I can get.

Thanks.

---

### Post by pseudonym on 2006-12-28
Did you have the card when you ran Redhat and was it working? If so, what driver were you using? HP doesn't appear to offer a proprietary driver so your only Linux options are [ALSA]("www.alsa-project.org") or [Opensound]("www.opensound.com").

HTH

PS - if you have no luck finding a linux driver, PCI soundblasters and modem cards can be had for real cheap on ebay. :)

---

### Post by dancallo on 2006-12-28
Pseudonym,

Thanks for the very quick response.  

I have toyed with the idea of replacing the sound card in that system since I don't use the modem anyway.  I have DSL broadband and connect to the Internet using a Cisco WRT-54G broadband router, which works quite well with Ubuntu to connect me to my LAN as well.

I will take your advice and look at ALSA and Opensound first.  If I can't find a driver for the sound card, I'll probably replace it.

P.S.  No, the sound card was not supported in RedHat Linux either.

Thanks, again.

---

