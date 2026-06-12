---
title: "Setting network up with speedstream 5200 e270 (as router) and Encore switch"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by bcortizo on 2007-03-24
So, I've been trying to set up a home network between my desktop and my sister's desktop with a speedstream 5200 e270 ethernet modem as a router and a encore enh908-nwy switch.

thing is: my sister's desktop (running windows XP) doesn't recognize the connection when I use the switch, but otherwise connects normally (i.e.: when it's connected directly to the modem/router)

I've tried setting up a fix IP, but to no avail: again, it only works when it's connected directly to the modem.

The strange thing is: when I connect my desktop, it's all ok. using this confioguration:
modem--->switch--->my desktop
it connects, regardless of booting up via XP or Ubuntu.

My modem is DHCP enabled (and working) and I have also tryed booting up my sister's desktop via the ubuntu 6.10 live cd and, not surprisingly, it also only connects to the internet when directly plugged into the modem.

Any ideas? I tried updating the ethernet adapter driver, but it didn't work.

Her desktop's a amd athlon 2,4+ GH with a asus a7v8x-x motherboard with onboard via rhine II ethernet adapter. (very similar to mine, only that my motherboard's a asrock k7vm3, but the ethernet adapater's the same)

any help will be greatly appreciated. :)

---

### Post by kelbizzle on 2007-03-24
Are you power cycling your cable modem? Because most cable modems clone the mac address of the last computer conntected. You want to be resetting all power to the cable modem. If your switching between computers and switch. As a test maybe you can boot your machine into windows xp, write down the network settings (ip,subnet,gateway, and both dns servers) then disconnect your machine, and connect your sisters computer to the switch and change her network settings to match yours.

---

### Post by bcortizo on 2007-03-24
Something I forgot to mention: my connection is a DSL one, not cable.

> 
As a test maybe you can boot your machine into windows xp, write down the network settings (ip,subnet,gateway, and both dns servers)

Thanks kelbizzle, but i already tried that too. It didn't work. =(
I also tried connecting just ione computer at a time. Mine works fine, but hers only work when directly connected.

i could simply plug her computer via the moem's USB port, but she's being a real jack-*** about it (not to mention incredibly childish, but that's another issue =p) and simply won't let me set up our computers like that.  :(

but thanks anyway. =]

---

### Post by bcortizo on 2007-03-25
Ok, I contacted Encore (the maker of the switch) in the hopes that maybe they knew what to do, even though I don't believe the switch is broken.

They suggested me to check if the problem persists after exchenging cables (i.e.: using my sister's cable to plug my computer to the switch and see if it works). If it don't work, it should be easy to settle: new cable = problem gone.

I'll go there and try swtiching the cables to see if it works out. wish me luck.

---

### Post by bcortizo on 2007-03-25
Yeah, it seems the problem is with the cable connecting my sister's computer to the hub.

replacing the defective cable should solve my problems.

=]

---

