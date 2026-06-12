---
title: "SD Cards + USB Reader different from USB sticks? For installing OSes."
date: 2014-09-03
forum: Any Other OS
---

### Post by AnttiV on 2014-09-03
Hi.

I won't go into too much reasons here, but here's the general situation:
I used to carry around a box/case of CDs/DVDs with installation medias for different operating systems (few flavor of *nix, Win98/Win7, MacOSX...). However, now that more and more computers do not even have optical drives and I'm tired of carrying around heavy (yeah, "heavy") boxes, I figured I'd transfer my installation media -collection to USB sticks. However, then an idea struck me - why use multiple USB sticks when you can go one step further and use (micro)SD cards and just one USB stick (card reader)?

I figured that since computers can boot from USB sticks, they'd be able to boot from USB-connected card readers, eh? Well, this might be true, but a moot point, since I cannot, for the life of me, get this to work. And I don't know what I'm doing wrong.

So, here's my procedure:
1) download ISO (or directly from unetbootin)
2) use unetbootin to write it to USB/card
3) boot computer with the stick inserted.

With a "genuine" USB stick (not a reader + card combo), everything works fine 99% of the time (could not get eComStation to boot from USB, but hey, beta and old OS).

When I do the same with a card + reader combo, messages wary a bit, but the ultimate result is the same - it won't boot, no matter what I do.

Mostly I get just "Boot error" or "Missing operating system" - and nothing else, it just hangs there.
I've tried a few different readers, with and without microSD-to-fullSD adapters. Nothing works.

Does the *adapter* matter and needs to be "boot compatible" or what is the problem here. (Or does the *card* matter? I don't think so, but... So far I've been using 4-8Gb Kingston ones and one 2GB no-name.) Is it possible, that a reader can read/write a SDHC/SDXC card at run-time, but can only BOOT from a "regular" SD card when starting the computer?


tl;dr:
I can make a bootable USB stick from an ISO and boot the computer from it, but I can't use a SD+USB-reader combo to do the same (from the *same* ISO).

ps. Haven't tried Windows yet, just a few *buntu variations and elementaryOS. Funnily enough, I have an old 512Mb Kinston SD card, tried to make it a bootable Debian-netinstall -media, and that one worked. It's slow, but does the job. I have no idea why that one works, but can't try any other OSes on it, because they don't fit into 512Mb...

---

