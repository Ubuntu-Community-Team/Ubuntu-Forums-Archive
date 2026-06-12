---
title: "Ubuntu 7.10 sets Bios to default"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by chimchim on 2008-01-18
Ubuntu 7.10 is the only OS on my PC. 
I configure the motherboard BIOS and Ubuntu boots OK.
The next time I logon I see "Checksum bad" and have the option of resetting my BIOS or going with the default settings.
If I choose the default settings Ubuntu still boots OK but all my previous settings have disappeared.
Should I just give up on trying to configure my BIOS and go with the default settings or am I missing something here?
The default settings are not optimal but I guess I can live with them if necessary.
Thanks for reading.

---

### Post by stoodleysnow on 2008-01-18
That is definitely not Ubuntu's fault. The problem here is that your motherboard's CMOS battery (the little 3V lithium one, button cell) needs replacing. It is what keeps your motherboard's time and BIOS settings correct. In the absence of 3V DC, the BIOS reverts to default.
New batteries can be obtained from car repair/spares shops, where the same type of battery happens to be used in some alarm keyfob remotes.
Hope this helps.:)

---

### Post by stump138 on 2008-01-18
That isn't so much an ubuntu issue as a bios issue. You should check to see if a bios update is available for your motherboard and replace the battery.

---

### Post by ByteJuggler on 2008-01-18
Try changing your BIOS battery, Ubuntu's not going to modify your BIOS settings.   It sounds like your BIOS settings are being lost, likely due to flat BIOS battery I'd guess.

---

### Post by chimchim on 2008-01-18
Thanks for the quick response guys.
I am not surprised to learn that it is a MB issue but am surprised that it could be the battery - it is a brand new board!
Unfortunately replacing the battery on my setup is not a simple task. Asus in their wisdom made it inaccessable without some disassembly. However I will certainly replace it over the weekend andf move on to my next problem.
Thanks again.

---

### Post by Iowan on 2008-01-18
If you have access to voltmeter, you could check it first.

---

### Post by ByteJuggler on 2008-01-18
> **chimchim said:**
> Thanks for the quick response guys.
I am not surprised to learn that it is a MB issue but am surprised that it could be the battery - it is a brand new board!
Unfortunately replacing the battery on my setup is not a simple task. Asus in their wisdom made it inaccessable without some disassembly. However I will certainly replace it over the weekend andf move on to my next problem.
Thanks again.

Hmmm, in that case it might be something else that's causing the BIOS to lose its settings. Could still be the battery.  I would also suggest checking with a voltmeter.

---

### Post by shad0w_walker on 2008-01-18
It definately sounds like the CMOS battery, it is possible its a dud even if new (Every now and then something comes out of the factory broken) or it might be there is something screwing up the connectors. Possibly a slither of plastic wrapping or such stopping the battery from connecting up properly. Best bet is check/replace the battery and make sure there isn't anything obviously out of place in the socket

---

### Post by Dr Small on 2008-01-18
Sounds like a battery issue.
Even if the motherboard is new (new to you, meaning you just recently got it), that still doesn't account for how long it sat at the factory or the store before you bought it.

It could very possibly be the battery (by the symptoms), so I would check it out first, as the least exspensive resolution.

Dr Small

---

### Post by Paulmd on 2008-01-18
> **chimchim said:**
> Thanks for the quick response guys.
I am not surprised to learn that it is a MB issue but am surprised that it could be the battery - it is a brand new board!
Unfortunately replacing the battery on my setup is not a simple task. Asus in their wisdom made it inaccessable without some disassembly. However I will certainly replace it over the weekend andf move on to my next problem.
Thanks again.

If you have a multimeter, you can test the battery, It should be 3 volts.

If you don't have a multimeter, you can still test. Place the battery on your tongue, if it doesn't tingle, it's dead. :)

---

### Post by stoodleysnow on 2008-01-19
> **Paulmd said:**
> If you have a multimeter, you can test the battery, It should be 3 volts.

If you don't have a multimeter, you can still test. Place the battery on your tongue, if it doesn't tingle, it's dead. :)

OW!!
I thapped my dongue!
:lolflag:

---

