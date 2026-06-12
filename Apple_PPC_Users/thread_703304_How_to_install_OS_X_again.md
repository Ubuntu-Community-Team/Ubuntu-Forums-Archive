---
title: "How to install OS X again"
date: 2008-02-21
forum: Apple PPC Users
---

### Post by isitaboat on 2008-02-21
Hi guys - 

I installed Gusty last night on my iBook G4 - installation went pretty well, though there are a number of fatal flaws which renders it pretty much a toy for me*.

Anyway - I'd like to reinstall OS X, but have the minor issue of an intermittently working DVD drive on the laptop...and no other mac - just my main ubuntu box.

I do however have a DMG of the disc, and a bootable firewire hd.



If I had a Mac available this would be simple - I could restore the dmg to the external drive and reboot and hold c...it should "just work".

I don't though - so is there a way of making the correct partiton tables & writing the dmg to the disk?

It seems you can mount the dmg...

```
mount -t hfs -o loop myImage.dmg /macdisk
```
... so I assume I should just be able to dd it to the partition....?

Partitions are the main worry :S

Thanks for the help!


Russ


*If your interested -  I can't use two software packages as they are not distributed as Linux/PPC; Zend Studio & Flash. In retrospect I should have checked this before :lolflag:

---

### Post by isitaboat on 2008-02-22
:popcorn:


Nothing?


I'm currently trying to get Yaboot to boot from a firewire drive with my Leopard install disk on it....no luck


Help!

---

### Post by SpiderGorilla on 2008-02-23
Well, you present a conudrum. In order to install the OS, you need a running OS. So... you... have to either have a DVD drive that's working all the time... or you have to have the external already configured for the process you're trying to attempt.

You've got two EASY choices as I see it:

1) You can try your thing with dd and such, see if it works. Just make sure you back down important data.

2) External DVD drive.

I have absolutely no idea if a Mac can boot from an external DVD drive. For some reason, I want to say "no"... but I never had to try something like that with my Macs, and I no longer own a Mac I can run test that on real quick.

---

### Post by isitaboat on 2008-02-23
I've managed the dd thing, and can now see all the apple partitions...

However I can't get openfirmware to see / boot from the external firewire drive....

The iBook has a working (well, no wifi) ubuntu install?

---

### Post by stream303 on 2008-02-23
> **SpiderGorilla said:**
> I have absolutely no idea if a Mac can boot from an external DVD drive.

It can if it is firewire, you just boot to open-firmware with cmd-opt-O-F and enter:
[B]
boot fw/node/sbp-2/disk:,\install\yaboot[/B]

however this boots Ubuntu, and probably not OSX.

---

### Post by isitaboat on 2008-02-23
I managed to get it reinstalled :)

If I hold the DVD drive (aka laptop) at an angle, it seems to work a treat...bizzare.



Anyway - I'd still be with Ubuntu if it weren't for the issues, infact when I upgrade to a intel mac, I will be running ubuntu / debian :D


Thanks ppl!

---

