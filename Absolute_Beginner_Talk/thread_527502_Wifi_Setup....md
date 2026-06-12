---
title: "Wifi Setup..."
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by jatiesch on 2007-08-16
Hi ppl i have dual boot ubuntu 7.04 system with win xp..
my wifi card is Netgear WG311v3..
My system is AMD64..

Problem is that while installing my card for ubuntu using ndiswrapper...i m getting some problem which i cant understand...maybe u ppl can help me out..

i first installed the drivers using..
[I]
sudo ndiswrapper  /..../wg311v3.INF

ndiswrapper -l[/I]

i get this -
[I]
WG311v3: driver installed
device (11AB:IFAA) present[/I]

meaning everythings correct till now...

then i give-

[I]sudo depmod -a
sudo modprobe ndiswrapper
[/I]
on running ifconfig it do not shows wlan0 meaning later commands dont work...
log is something like-

[I]jatiesch@MisraSoft:~$ tail /var/log/messages
Aug 21 12:47:11 MisraSoft kernel: [  878.677968] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
Aug 21 12:47:11 MisraSoft loadndisdriver: loadndisdriver: load_driver(359): couldn't load driver wg311v3 
Aug 21 12:47:11 MisraSoft kernel: [  878.739669] usbcore: registered new interface driver ndiswrapper[/I]

so can u ppl figure out where i went wrong..
i desperately want net running on my ubuntu system so that i can explore it in bigger way...
plz help me out...

---

### Post by walkerk on 2007-08-16
> **jatiesch said:**
> Hi ppl i have dual boot ubuntu 7.04 system with win xp..
my wifi card is Netgear WG311v3..
My system is AMD64..

Problem is that while installing my card for ubuntu using ndiswrapper...i m getting some problem which i cant understand...maybe u ppl can help me out..

i first installed the drivers using..
[I]
sudo ndiswrapper  /..../wg311v3.INF

ndiswrapper -l[/I]

i get this -
[I]
WG311v3: driver installed
device (11AB:IFAA) present[/I]

meaning everythings correct till now...

then i give-

[I]sudo depmod -a
sudo modprobe ndiswrapper
[/I]
on running ifconfig it do not shows wlan0 meaning later commands dont work...
log is something like-

[I]jatiesch@MisraSoft:~$ tail /var/log/messages
Aug 21 12:47:11 MisraSoft kernel: [  878.677968] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
Aug 21 12:47:11 MisraSoft loadndisdriver: loadndisdriver: load_driver(359): couldn't load driver wg311v3 
Aug 21 12:47:11 MisraSoft kernel: [  878.739669] usbcore: registered new interface driver ndiswrapper[/I]

so can u ppl figure out where i went wrong..
i desperately want net running on my ubuntu system so that i can explore it in bigger way...
plz help me out...

```
iwlist scanning
```

wireless nics aren't always assigned as wlan0. lets see.

---

### Post by jatiesch on 2007-08-16
thanks, but then how to proceed??

---

