---
title: "Upgrade to Jaunty on Macbook"
date: 2009-04-21
forum: Apple Hardware Users
---

### Post by fbp90crx on 2009-04-21
I am currently dual booting with Ubuntu and OSX and It took me a while to get all the codes and stuff right for Ubuntu to work on the mac, I was wondering if I did the sudo upgrade to 9.04, will I have to redo all that work? or will it stay the same

---

### Post by anando on 2009-04-22
Hi

> **fbp90crx said:**
> I am currently dual booting with Ubuntu and OSX and It took me a while to get all the codes and stuff right for Ubuntu to work on the mac, I was wondering if I did the sudo upgrade to 9.04, will I have to redo all that work? or will it stay the same

I could not resist the temptation and jumped right in - and discovered that it sort of works. But of late a couple of random freezes - especially when I was half way through my work, pissed me off. But then, I am to blame for it. If I were you, I'd wait until a week after the official release - when the teething issues have been sorted out. For me, it's the random freezes, and having to manually modprobe my wireless ath5k driver for now. Wish I had heeded my better judgement then ;)

What the heck - go upgrade *hee *hee

- Anand.

---

### Post by fbp90crx on 2009-04-22
I'll probably just wait a week until the release comes out. Finals are next week and I don't really have time to start messing with codes and trying to fix stuff lol. Thanks

---

### Post by cyberdork33 on 2009-04-22
honestly, I would recommend backing up important fines and installing from scratch. I have never had an upgrade go well.

---

### Post by fbp90crx on 2009-04-23
> **cyberdork33 said:**
> honestly, I would recommend backing up important fines and installing from scratch. I have never had an upgrade go well.

How easy is it to reinstall on just that partition? I don't wanna mess with the OSX partition. On installation, can I just choose that partition that has ubuntu on it and go from there?
Also, then will have to do all that crap just to get the right click and other stuff working again?

---

### Post by cyberdork33 on 2009-04-23
> **fbp90crx said:**
> How easy is it to reinstall on just that partition? I don't wanna mess with the OSX partition. On installation, can I just choose that partition that has ubuntu on it and go from there?
Also, then will have to do all that crap just to get the right click and other stuff working again?
There is likely a root partition and a swap partition for ubuntu. You can use the manual partition method to select them for use with your new install. You could also use the partition editor before installing and deleting the ubuntu partitions, then choosing "install to the largest free space" when prompted by the installer.

You will need to follow the direction for Jaunty and your hardware. They may be different. However, unless you have a specific reason to upgrade, why not stick with what you have?

---

### Post by Rog-Mahal on 2009-04-24
I'm thinking of doing the same thing. If I want to do a fresh install of 9.04 on my Ubuntu partition, what do I need to do to maintain refit functionality? Do I need to reinstall refit or boot using the rescue cd? Also, can I try out ext4 with refit?

---

### Post by cyberdork33 on 2009-04-24
> **Rog-Mahal said:**
> I'm thinking of doing the same thing. If I want to do a fresh install of 9.04 on my Ubuntu partition, what do I need to do to maintain refit functionality?Nothing...

> **Rog-Mahal said:**
> Do I need to reinstall refit or boot using the rescue cd?
Shouldn't. rEFIt is installed on your OSX partition.

> **Rog-Mahal said:**
> Also, can I try out ext4 with refit?
Yes, it should work. ext4 is backwards compatible with ext3, meaning that ext3 drivers can access ext4 filesystems (albeit without the other goodies that ext4 offers over ext3, but that wouldn't matter for loading grub.)

In fact, it is my understanding that the partition table syncing bug is finally gone in Jaunty.

---

### Post by Rog-Mahal on 2009-04-24
Sweet! Well, I'm upgrading right away!

---

### Post by Rog-Mahal on 2009-04-24
Well, the upgrade seemed to go smoothly, but now I've run into some problems with GRUB. The refit partition table appears to be correct as cyberdork said. See[this thread]("http://ubuntuforums.org/showthread.php?t=1135774") for further info.

---

### Post by jamessnell on 2009-04-25
> **cyberdork33 said:**
> honestly, I would recommend backing up important fines and installing from scratch. I have never had an upgrade go well.

Well, for what it's worth, I've had a few upgrades turn out fine - though I have to agree, generally a fresh install is preferable. However my general approach is to try an upgrade first and then if it's feeling imperfect, then I just try a fresh install. 

And if that doesn't work I install DOS 5 and play Lemmings for a few hours. Okay, not that last part..

---

