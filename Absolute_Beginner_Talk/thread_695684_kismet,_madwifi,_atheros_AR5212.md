---
title: "kismet, madwifi, atheros AR5212"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2008-02-13
I have been trying to get kismet working with my Thinkpad T60 Atheros 5212 card. I have downloaded madwifi-tools and have edited the kismet.conf file several times, following the wide range of advice on the forums:
I have tried as the source:
madwifi,ath0,atheros
madwifi_g,wifi0, atheros
and several other combinations with no luck.

sudo kismet gives the message: FATAL: support for capture source type 'madwifi_g' was not built...
(substitute  'madwifi_g' for whatever is in the source)

 Do I need to download a madwifi driver? I thought this was installed by default with Ubuntu. If so which one would I need for an atheros AR5212 chipset?

---

### Post by jba6511 on 2008-02-13
figured it out. Compiled Kismet from source with libpcap support from tcpdumps.org (or something like that - shows you the address when ./configure). Then I edited the kismet.conf section for the source to:
madwifi_ag,wifi0,atheros and it is up and running. No need to install any additional madwifi drivers so far.

---

### Post by abuakel on 2008-03-11
I have the exact same wireless card and I'm getting the same error.. 
How did you compile kismet?

---

### Post by mehfuz on 2008-03-11
same question - but i can't configure kismet, help please

---

### Post by txpolo on 2008-04-20
Yup... same exact problem too... I've been working on this for and embarrasing long time... any help from some Linux gods out there? Yes i'm afraid i must be annother ubuntu idiot... sorry I'm working on it!  same chipset  (using airlink AWLC4130, on Dapper... on an inspiron 1100)

I've tried installing the kismet a zillion times (even after i've tried to install libpcap -- which i thought was installed both through the synaptic and when more recently when i downloaded the more recent version from their website... haven't been able to get the tcpdump to work though) here's what i get from the kismet ./configure  I'm pretty sure that libpcap is installed.

*** WARNING ***
LibPCAP was not found.  Kismet previously included a local copy of this
library, however it now expects libpcap to be provided by the system.
Kismet on Linux without LibPcap cannot capture data locally and will
almost certainly NOT BE WHAT YOU WANT.
Your distribution should provide packages for libpcap, otherwise
it can be downloaded from [http://tcpdump.org](http://tcpdump.org)

Oh and then when i do run kismet i get this:

FATAL: Support for capture source type 'madwifi_ag' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.

where is this 'configure' output????

---

### Post by openflame06 on 2008-04-23
Hey all - i think the way the original poster had more success was by running 
sudo aptitude install libpcap

Press tab after writing libpcap and you will be shown the packages available, on my system 7.10 Gutsy it was libpcap0.8-dev.

I then ran ./configure for kismet and it didnt complain about libpcap.

Im in the process of installing it now so i'll edit this post once i see if it works.

---

### Post by txpolo on 2008-05-04
yup i got it fixed a little while ago (but forgot to come here and post how i got it done)... as soon as i installed the libcap dev package it worked!

---

### Post by Monicker on 2008-05-04
Why not use the kismet in the Ubuntu repos?

---

