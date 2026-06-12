---
title: "Live cd will not install"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by v_dragon on 2007-01-06
DL and try to install from live CD. try both 6.10 and 6.06

both installs die in the same spot, can not load GUI.
then it goes to command line

specs:
Asus P5n32-sli DL
Core2duo E6300
Nvidia 8800 GTS

somthing wrong with my DL or do the live cd not like my hardware?

---

### Post by teaker1s on 2007-01-06
download alternate .iso and verify md5 checksum. next be prepared for text install-alternate iso has lots more flexibility and more reliable

---

### Post by v_dragon on 2007-01-07
ok its not the cd's, i try them on my P3 bench tester and they boot properly. it must not like something in my hardware.
 As for a text install..um i am not at that level of knowledge for that. unless i missunderstand what text install means.

The exact errer is:

Failed to start the X server (your gui). it is likey that it is not set up correctly. would you like to view teh x server output to diagnose the problem.

Fatal server error
No screens found


The x server is now disabled
restart GDM when it is configured correctly.

---

### Post by jvc26 on 2007-01-07
The text install is not a command line install if thats what you fear. The Alternate CD install as it is called is a text interface (with boxes and words and things) but just really basic: Like here: [http://psychocats.net/ubuntu/images/w2u40.gif](http://psychocats.net/ubuntu/images/w2u40.gif)
Rather than having a GUI. Basically it just means that it uses up less resources and should allow you to install and the install process may fix your Xserver.
Il

---

