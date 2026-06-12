---
title: "Asus G60Jx: wireless is disabled by hardware switch"
date: 2011-06-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by grade-a on 2011-06-04
Hello all.  Earlier today I completed a fresh install of Ubuntu 11.04 on my Asus G60Jx (with less difficulty than I expected).  The only issues I am currently experiencing is that wireless capability is disabled.  Previous to this install I was using Windows 7 and occasionally would be informed that "Wireless hardware cannot be detected on your computer".  About two weeks ago this occurred and none of the previous fixes would work.  Fed up with that and other mysterious issues that seem to always plague my Windows machines, I decided to switch back to Ubuntu.

Wired connection is working just fine, however the option to enable wireless is greyed out, with the annotation "wireless is disabled by hardware switch". 

lspci tells me that my wireless adapter is an Atheros AR9285, and running rfkill list gives the following:

> 
grady@multivac:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


The hardware switch on this machine is FN + F2.  Pressing this toggles the soft block on/off.

> 
grady@multivac:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes


Additionally, I can toggle the soft block from on to off with rfkill unblock, however this does not remove the hard block.  Any ideas?

---

### Post by grade-a on 2011-06-04
Ok, so after trying every solution I could find I gave up for a while and shut down my machine.  Booted it up again and it is now working, couldn't tell you why.

---

