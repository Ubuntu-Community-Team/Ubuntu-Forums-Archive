---
title: "cant get ubuntu installation.. ide.rc ??"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by Felix21685 on 2006-03-10
i cant get the ubuntu installationg to boot up

fyi im using a WD Sata Raptor

i hit enter when the first screen pops up which tells me i want the regular install so i hit enter.

then it loads the drivers and what not 

and stops here :
pci [success]
running etc/hotplug/usb.rc
usb [success]
Running /etc/hotplug/ide.rc

there it just hangs..forever..
i used this same cd to install linux on a non sata sstem and it worked.
ive tried different cd's and i ve even disconnected my sata altogether and just attached a regular ATA drive and still the same halt

what do you guys think it is ?
thx in advance

---

### Post by Felix21685 on 2006-03-10
also
its an ABIT VT7 mobo..
is there something i should be changing in bios?

---

### Post by pbaehr on 2006-03-10
I had the same problem when I installed.

I believe the way I finally got it to intall was to add "noapic nolapic" parameters to the boot. It's been a while and I don't have any notes on it but I believe when you put the CD in rather than just press enter you should type:
```
linux noapic nolapic
```

See if that works for you.

(Disclaimer, I have no idea what this actually does, I found it as a fix for this problem listed on the net)

---

### Post by Felix21685 on 2006-03-10
hmm 

i just tried that and still no dice..i made sure to spell it correctly etc..

anyone else have any ideas?

---

### Post by Felix21685 on 2006-03-11
still trying to find a solution to this..

how come if worked on the same HD in the other machine but not in this one..
it has to be motherboard issues..yet this one is better than the one in the other one..
any help is greatly appreciated

---

### Post by Felix21685 on 2006-03-12
i got another suggestion
from someone on my photo forums
to try
linux acpi=off noapic

but that didn't work either.

is it supposed to be scpi first then apic second ?
meaning..is it mispelled?

---

