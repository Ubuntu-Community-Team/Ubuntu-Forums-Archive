---
title: "Unable to boot to OSX but able to boot to Ubuntu"
date: 2010-03-12
forum: Apple Hardware Users
---

### Post by Pholk on 2010-03-12
Hello

My intel macbook 13" (the basic one from a few years back) decided the other day to stop booting to OSX. Upon powering up, the screen would display the grey apple logo on the white screen but wouldn't get any further (no loading cog etc...). I had a look on Apple support and went through their troubleshooting guide for the problem. It has the same problem when booting to safe mode (I can use shift+cmd+v on startup and see where the startup gets stuck if that helps in anyway to identify the problem) and I have tried resetting Pram etc... and booting in both verbose and single user mode (neither of which work).

After failing to get anywhere with any of these methods I tried booting from my OSX disc and the same problem occurs, I can hold option on startup and it recognises the disc but whenever I try to boot from it I get the apple symbol and no further again. I have also tried using a friends OSX disc and the same problem occurs so I'm pretty confident the fault is not with the disc (both in good condition). The issue is not with the disc drive as I have been able to boot to a linux disc and after performing a full hardware check (something else I am able to do from startup) no problems were found.

The strange thing is that I am still able to boot to the ubuntu partition on my hard drive with no problems at all. This would be fine but the partition is only small, I'm not a very proficient ubuntu user and I have a dissertation due in 2 weeks and would very much like to be able to work on my mac partition.

I have all my files backed up with time machine so re-formatting is not a problem (I have gparted on ubuntu with the ability to write to HFS+) but obviously if I reformat and this changes nothing I'm in real trouble, particularly considering my impending deadlines.

My main concern is that there is something wrong with the EFI (or firmware.scap file) which is preventing me booting to either OSX or the OSX disc. I assume there must be a way of getting around this as people can and do buy new hardrives for mac systems and they must have the EFI created somehow (presumably from the disc).

Any help on this problem would be very much appreciated, even if it's just some reassurance that reformatting part of/my entire hard-drive will cause me no probelms.

Thanks in Advance.

P.S. I have tried removing battery and power and holding the power button for a minute or so. Hav ealso done the same with the RAM removed.

---

### Post by linuxopjemac on 2010-03-12
what about buying an external firewire drive and put OSX on it and then try to get your data on the firewire disk ?

something like [this ]("http://cgi.ebay.com/LaCie-250GB-External-Firewire-Hard-Drive-NO-RESERVE_W0QQitemZ170456060984QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item27aff91438")will do the job

---

### Post by Pholk on 2010-03-12
I was hoping I would still be able to use my normal hard-drive as it isn't damaged, I'm a poor student and also like to use my laptop on the move so obviously it's easier if I don't have to bring an external hard-drive everywhere. Cheers for the suggestion though.

I'm just trying to isolate the location of the problem really, whether it's with my OSX partition or the EFI partition if that's possible...

Once I can boot from the OSX disc then the problem is gone, I'm just trying to get to that point.

Thanks for the suggestion though

---

