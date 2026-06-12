---
title: "wireless not seen in 'network setting' window"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by sleeper414 on 2008-02-10
hi folks,

i have been banging my head figuring out the broadcom bcm43xx nightmare.
i have figured out the fwcutter and ndiswrapper, eveything seems to check out...
but when i goto system>administration.>network.

it doesnt show wireless.only wired and modem.

any ideas?

---

### Post by jan quark on 2008-02-10
hm when you have the broadcom 4311 wlan card then I know your pain

check pleas with
```

lspci
```
and

```
lshw -C network
```

the exact model of your card

broadcom cards are sometimes the hell on earth 
I for instance removed my broadcom card today, it was fun opening the laptop, removing the keyboard, it was tricky but worth it, now I have an usb wlan stick plugged in and no trouble at all

so if either the fwcutter method worked nor the ndiswrapper thing
remove the broadcom and invest few dollars into a new wlan card
weird solution but  after hours spent with a impossible fight with broadcom the only one I would recommend

---

### Post by sleeper414 on 2008-02-10
thank you for the advise. but im poor, and buying anything is out of the question.

if i buy anything, it will be a longer ethernet cable. 

i got so frustrated, i am just going to reinstall gutsy.

---

### Post by jan quark on 2008-02-10
yea sleeper414

I know your trouble, try the fwcutter method once you fresh installed the OS
perhaps it will work

that's what i have done to enable my broadcom 4311

[http://laiconic.quotaless.com/tutorial1.html](http://laiconic.quotaless.com/tutorial1.html)

I haven't found a solution for my broadcom but perhaps you will be more successful

---

