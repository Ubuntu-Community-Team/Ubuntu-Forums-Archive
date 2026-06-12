---
title: "imac g4 won't boot from cd"
date: 2007-04-19
forum: Apple PPC Users
---

### Post by bballs91 on 2007-04-19
hey burned the powerpc image onto a dvd using infra recorder and it burnt successfully, but when i boot my imac, and hold own "C" I can hear the disc spinning, and then it boots into OpenFirmware (my OS X installation is broken :( )

---

### Post by VWracer18 on 2007-04-19
I had the same problem. It turned out to be a timing issue and learning when to let go of the "C" button. When the "C" button is pressed it should bring a text menu this will give the choice of the cd/dvd-rom or whatever else, I think the other option is "I" but I cannot remember. Does the machine give you any choices at the point where you press "C"?

---

### Post by bballs91 on 2007-04-19
no it doesn't give me any options.  I'll keep playing around with the timing of it though.

---

### Post by pxwpxw on 2007-04-19
What CD are you using and what do you see when it boots into OpenFirmware?
Also, try holding down the Option key for an alternative.

---

### Post by bballs91 on 2007-04-19
I'm using a memorex branded DVD-R.  When it boots into openfirmware it says Apple Powermac6, 1 4.5.9f1 bootROM built on 02/18/03.

Then just a welcome message and type mac-boot to boot (doesn't work)
and shut-down to shutdown

---

### Post by pxwpxw on 2007-04-19
OK, but what ubuntu iso image did you use, and did you burn it at low speed x4.
When it boots into OFware, type
```

0> printenv boot-device

```
and tell me what it returns

---

### Post by bballs91 on 2007-04-20
> -------Partition: common --------Signature: 0x70 ----
boot-device____hd:,\\:txbi_______hd:,\\tbxi

There you go

EDIT: the post didn't format right, i had to add the "_".  It didn't actually print those, imagine they were spaces.

---

### Post by pxwpxw on 2007-04-20
OK  hd:,\\:tbxi is the normal boot-device for macosx, and both values the same means it was not changed, and should boot macosx normally after shut-down, with the CD removed.
Not sure if you mean  macosx was broken or just wont boot?

If macosx  was OK before, from  OFware do 
```

0> eject cd
0> reset-all

```
And see what happens.
(Alternately zap the pram using 4 keys,  Command Optioon P R , all held down through 2 chimes)

---

### Post by bballs91 on 2007-04-20
Didn't make a difference...

I'm trying to get a hold of a copy of Disk Warrior which is supposed to be able to repair the hdd.

---

