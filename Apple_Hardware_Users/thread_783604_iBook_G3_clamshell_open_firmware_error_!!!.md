---
title: "iBook G3 clamshell open firmware error !!!"
date: 2008-05-05
forum: Apple Hardware Users
---

### Post by rectagonal on 2008-05-05
System is a tangerine iBook clamshell.

I was dual booting Tiger & XUbuntu hardy heron... Was in tiger when I got a kernel panic. Shutdown system, restarted and got an open firmware message.

> DEFAULT CATCH! code=300 at %SRR0: 05600ae0 %SRR1: 00083030

Apple PowerBook2, 1 4.1.7f4 BootROM built on 03/20/01 at 17:20:48
Copyright 1994-2001 Apple Computer, Inc.
All Rights Reserved.

Welcome to Open Firmware, the system time and date is : 02:08:57 05/06/2008
   The battery capacity is : 73 percent

To continue booting, type "mac-boot" and press return.
To shut down, type "shut-down" and press return.

No hardware changes have happened in the past month.. new optical drive was installed back in February. yaboot hadn't been touched in a long while. Attempts to boot from Tiger CD have no response, just the searching mac folder icon... Attempts to boot from Mac OS 9 CD , start to load something .. screen turns white... then the cd drive spins down and nothing... booting from a xubuntu CD reveals the bootloader... but it stalls shortly after loading the kernel ...

Zapping pram results in nothing new...
Holding down option on boot presents the menu to select media to boot from... selecting media results in the same phenomena...

Issuing the open firmware commands :

> set-defaults
reset-all

results in a reboot followed by the exact same behavior.

I understand some of these symptoms are common with larger hard drives, but my iBook is running an 8 gig HD... this should not be the case.. I have NEVER had any problems booting an OS from this hard drive ...

Its been a great trooper... and im praying there is a way to fix this...

---

### Post by stream303 on 2008-05-05
Yikes!  When you zap the pram, do you hold down the keys until you hear a chime?

I found something similar in this thread - traverse up and down through it and maybe you can coerce openfirmware to find your boot partition again:
[http://lists.terrasoftsolutions.com/pipermail/yellowdog-general/2004-April/013108.html](http://lists.terrasoftsolutions.com/pipermail/yellowdog-general/2004-April/013108.html)

I'm surprised that the other options didn't work - perhaps loading a rescue shell from an installer cd, and using

```
ybin -v -C /etc/yaboot.conf
```

might revive it..

Update: if that didn't work, I'd be tempted to try mkofboot just in case - the syntax looks similar:

```
mkofboot -v -C /etc/yaboot.conf
```

---

### Post by rectagonal on 2008-05-06
> **stream303 said:**
> Yikes!  When you zap the pram, do you hold down the keys until you hear a chime?

Yes.

> 

I'm surprised that the other options didn't work - perhaps loading a rescue shell from an installer cd, and using

```
ybin -v -C /etc/yaboot.conf
```

might revive it..

Update: if that didn't work, I'd be tempted to try mkofboot just in case - the syntax looks similar:

```
mkofboot -v -C /etc/yaboot.conf
```

Loading any kernel from the install CD hangs indeffinetly at the following screen :

> 
done
copying OF device tree ...
Building dt strings...
Building dt structure...
Device tree strings 0x021a6000 -> 0x021a6b68
Device tree struct 0x021a7000 -> 0x021c1000
Calling quiesce ...
returning from pram_init
_


I did try a few of the suggested openfirmware commands in the thread you linked me to, with no luck... specifically I tried several variations of this :

> boot-device hd:8,\\:tbxi

Anything involving actual use of an operating system... may not be possible as I dont seem to be able to load one.

---

### Post by pxwpxw on 2008-05-06
**rectagonal**

Some more possibilities - assuming a firmware problem. I don't know specifics for your ibook.

In open firmware  reset-nvram,
 
 and resetting the PMU. 

Some apple docs here - 

"To continue booting, type 'mac-boot' and press return" Message
 [http://docs.info.apple.com/article.html?artnum=42642](http://docs.info.apple.com/article.html?artnum=42642)

Resetting PowerBook and iBook Power Management Unit (PMU)
 [http://docs.info.apple.com/article.html?artnum=14449](http://docs.info.apple.com/article.html?artnum=14449)

Resetting your Mac's PRAM and NVRAM
 [http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

Also try the Apple ibook sub forum:
 
Apple - Support - Discussions - Forum Home
 [http://discussions.apple.com/index.jspa](http://discussions.apple.com/index.jspa)

---

### Post by stream303 on 2008-05-06
That's a sticky if I ever saw one!

My other favorite is about firmware upgrades if you ever think about upgrading your system beyond "official" specs:

[http://docs.info.apple.com/article.html?artnum=86117](http://docs.info.apple.com/article.html?artnum=86117)

Heed the warning about NEVER trying to load any OSX installer or OSX utility on a older Mac-OS system that hasn't had the firmware upgraded first.

---

### Post by stream303 on 2008-05-06
Admittedly I'm reaching for straws here, but is there anything else connected to the system that doesn't absolutely need to be there?

Does it need a possible internal cleaning or connector inspection, loose ram chips(?) etc?

---

