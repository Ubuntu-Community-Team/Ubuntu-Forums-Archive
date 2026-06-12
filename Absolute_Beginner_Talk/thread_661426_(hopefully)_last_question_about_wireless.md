---
title: "(hopefully) last question about wireless"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by winsall on 2008-01-07
ok so ive borrowed my mums PCMCIA wireless card (she wont miss it, her work gives her a new one when she asks for it).

i plug it in, all the sudden, network manager has wireless connection settings! 

Whoo! :guitar:

but, i cant figure out how to connect to my wireless network! GAH
i tried manually putting it in (SSID: default [im too slack to change it]) and theres no protection, and the router does all that IP stuff.

but its not finding my wireless network!!! :(:(

what can i do?

thanks in advance,
winsall

EDIT: i forgot to add the iwconfig
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      NOT READY!  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=31 dBm   Sensitivity=0/200  
          Retry short limit:0   RTS thr=0 B   Fragment thr=0 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

any response is greatly appreciated

---

### Post by blurryone on 2008-01-07
are you running the correct drivers? i had a similar problem once that i had to reinstall with the device plugged in to resolve :S good luck to you.

---

### Post by winsall on 2008-01-07
im not actually sure. i plugged it in and it recognized it immediately. i tried installing the windows driver through NDISWRAPPER (its listed on their website as supported, however, this is what happens:

 ndiswrapper -i WL54Cfg.inf
couldn't open WL54Cfg.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.

any ideas?

---

### Post by winsall on 2008-01-08
ok i got the driver to install, but eth1 is still NOT READY! (apparently ubuntu thinks caps lock is cruise control for awesome :lolflag:)

what can i do?? this is killing me!!!
i could go to work and buy a new wireless card, but we only sell Dlink ones and i have no clue if it would work :S:S:S

---

