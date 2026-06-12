---
title: "dial up problem Sis AC'97"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by willhurt on 2005-11-26
hello all,
im new to linux just downloaded ubuntu yesterday and the install went fine but i cant get my laptop onto the internet via the modem, the broadband network card worked fine but am away from home and only have a phoneline.
the modem, an sis ac'97 onboard modem, shows up in network settings :
and i enter all my details but under modem port:
autodetect finds nothing.
when i click the drop down box:
/dev/modem ---hitting ok then activates gives me the error Could not enable the interface ppp0

when i go back to the modem port drop down box and select any other i.e /dev/ttyS0, /dev/ttyS1, /dev/ttyS2 e.t.c then hit ok activate i get no error messgaes but nothing happens and when trying to go anywhere with firefox i get "whatever" could not be found, and when i return to network settings the modem is "disabled" again.


so im forced to boot back to windows to go on the net.

after looking around a bit on the net ive typed lspci into terminal ad i get the following :
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)

btw im running a fujitsu-siemens AmiloD 1840w and ubuntu 5.10
 
if anyone could help me that would be great.

thanks
will

also im trying to install a program which required me ot use the make command in terminal- i installed build-essential through synaptic so now the make command exists but when i run it i get errors about biosn, so after googleing ive downloaded:
bison_1.875d-1_i386.deb
but dont know how to install it

---

