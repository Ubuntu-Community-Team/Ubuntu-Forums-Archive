---
title: "ndiswrapper and Netgear WN511B N Draft Card"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by combat squirrel on 2007-10-11
Hey all, trying to get my WN511B card working in 7.04 ubuntu, tried ndiswrapper with the vista,xp, w2k drivers for the card, and no go, any ideas?

---

### Post by myk.dinis on 2007-10-12
Have you done an ndiswrapper driver install before with another wireless card?

I'm asking so I know what to ask you...

It sucks...but without enough info I can't help you any better...

More information is always better than trying to be succinct!

After all...you don't pay by the letter...

:)

Cheers!
Myk

---

### Post by Daveth on 2007-10-12
might be an ndiswrapper version issue?  see

Card: Netgear WN511B Rangemax Next
Chipset: Broadcom unknown device 4329 (rev 01)
pciid: 14e4:4329
Driver: XP version 08/22/2006, 4.80.53.0 downloaded from Netgear 26/10/06
Other: SuSE 10.1, ndiswrapper 1.27

@ [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/)

Might be worth confirming the chipset involved. Post back the results of 

```
lspci  -v
```

---

### Post by dchurch on 2008-04-12
Did you ever work out what the problem was, I have the exact same card.

---

