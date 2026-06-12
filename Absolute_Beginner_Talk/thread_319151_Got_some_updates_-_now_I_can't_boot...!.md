---
title: "Got some updates - now I can't boot...!"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by John E on 2006-12-15
Ever since I first installed Ubuntu a balloon prompt has been nagging me that 206 new updates are available for my system. So today I finally got around to installing them, and guess what.... now I can't boot my system!!

It took about 20 mins to download the new updates and a further 20 mins or so to install them. At the end of this I was asked to re-boot my computer - but suddenly it won't boot up, either in normal mode or recovery mode. In normal mode I only get these 3 lines:-

[B]Loading essential drivers
Mounting root file system
Waiting for root file system[/B]

In Recovery mode I can see that the 3rd stage gets reached and shortly afterwards, these lines appear:-

[B]registered new driver usbhid
drivers/usb/input/hid-core.c: v2.6:USB HID core driver[/B]

At this point, the system hangs with no disk activity occurring. Any ideas anyone??

---

### Post by gn2 on 2006-12-15
> **John E said:**
> Ever since I first installed Ubuntu a balloon prompt has been nagging me that 206 new updates are available for my system. So today I finally got around to installing them, and guess what.... now I can't boot my system!!

It took about 20 mins to download the new updates and a further 20 mins or so to install them. At the end of this I was asked to re-boot my computer - but suddenly it won't boot up, either in normal mode or recovery mode. In normal mode I only get these 3 lines:-

[B]Loading essential drivers
Mounting root file system
Waiting for root file system[/B]

In Recovery mode I can see that the 3rd stage gets reached and shortly afterwards, these lines appear:-

[B]registered new driver usbhid
drivers/usb/input/hid-core.c: v2.6:USB HID core driver[/B]

At this point, the system hangs with no disk activity occurring. Any ideas anyone??


Have you tried re-booting with all USB peripherals unplugged?

Do you have a PCI USB card? Try removing it?

Do you have USB keyboard and/or mouse, tried PS2 ones?

I haven't a clue really, just suggesting some options to try....:-k

---

### Post by John E on 2006-12-15
Thanks for the suggestions. Everything's backed up so I can easily revert to a working copy and I'm open to ideas. My mouse and ADSL modem are USB devices so I'll try unplugging them.

---

### Post by John E on 2006-12-15
I tried booting up in Recovery mode with all my USB devices unplugged. This time, it stops at the stage "Waiting for root file system".

If I then plug in my mouse, it continues to the stage where it previously stopped - and stops again.

If I then unplug & re-plug my mouse a few times, I eventually get to a command prompt and I seem to be in the folder /**usr/sh**. However, no matter what I type in at this prompt, it isn't recognised.

---

### Post by rich.bradshaw on 2006-12-15
Which version are you using? Dapper, Edgy etc?

I haven't used Ubuntu for long, but in a lot of other distros upgrading too much at once often messes things up - it's a good idea to either do all upgrades as you get them, or don't upgrade at all. Doing it in massive goes always breaks things...

Normally it can be fixed though - not sure how in this case though!

---

### Post by John E on 2006-12-15
I'm using Dapper. I might just revert to my backup and forget about the updates!

---

### Post by tocleora on 2006-12-15
**THE POTENTIALLY SUPER HARD WAY:**

Hah! :)  You should be able to see a list of everything it's going to install and I want to even go as far as to say you can uncheck everything but one thing.  Make a note of what's going to install, install it, reboot, repeat.  If you can't uncheck everything but one, then write them all down, and go into synaptic and update them one at a time.  you might make a backup after every one so when/if you do find a particular one causing the problem you can revert back to the last step and **AVOID THAT ONE AT ALL COSTS NEXT TIME!!!!**  :)  

I would agree just to leave it alone except in the case where one of the updates might be security related, so I would be hesitant not to do it at all.  But maybe there's a moderately hard way out there (maybe do 10 at a time to lower the reboots to 21?  Or maybe just each time you boot in install 10, reboot and continue working for that day) that might be easier than my super hard way. :)

---

### Post by John E on 2006-12-15
This is starting to look like a fundamental problem of backwards compatibility.

I restored my Ubuntu backup and re-booted.... Naturally, I was again prompted to download 206 updates - but this time, I unticked them all - except for the options that said "base system files" and anything beginning with "Linux" (e.g. "Linux kernel" and "Linux Image files" etc).

This time, I had only 7 packages to update - but I got the same problem. I think there's some kind of hardware compatibility issue perhaps in the Linux kernel... :(

---

### Post by John E on 2006-12-15
Is there a way to stop the Update application from automatically ticking the available updates? I'd like to home in on which package is causing this problem - but each time I install just one package, all the others get automatically ticked and I then have to untick over 200 options, just to install one more package!! ](*,)

---

### Post by gn2 on 2006-12-15
Perhaps you could post a list/description of your hardware?

---

