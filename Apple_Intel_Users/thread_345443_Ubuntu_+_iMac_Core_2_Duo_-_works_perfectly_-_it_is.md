---
title: "Ubuntu + iMac Core 2 Duo - works perfectly - it is possible!"
date: 2007-01-24
forum: Apple Intel Users
---

### Post by ehird on 2007-01-24
Facts:

1. Uses rEFIt as the bootloader, which calls the linux partition "Linux on ". You could probably get rid of it after using its sync tool but I'm too scared :P
2. After booting the linux one on that, you'll get a lilo menu. Standard stuff, works fine.
3. No nice bootup splash screen! Enjoy pages and pages of text before GDM comes up.
4. Untested things right now: ATI drivers (1024x768, yay!), Airport, Bluetooth (know these don't work - will find out), ..., profit, etc.
5. Uses Boot Camp, but after partitioning it it will be b0rked and you will never be able to use Boot Camp again without destroying your linux partitions.

I... haven't actually tested booting into OS X after syncing yet, but - it was relatively easy once I found out what to do, and I'll post a HOWTO if anyone's interested.

Edit: Oh yes, you'll have to manually edit a config file and rerun lilo after every kernel update.

Edit: ARRRRGH! turns out i installed the 32bit edition.... gaaah

---

### Post by MichaëlVD on 2007-01-24
> **ehird said:**
> I... haven't actually tested booting into OS X after syncing yet, but - it was relatively easy once I found out what to do, and I'll post a HOWTO if anyone's interested.

I am *very* interested! I'm glad it worked for you, but I can't wait to finally to get Ubuntu working side by side with os x on my iMac myself. (In fact, I would ditch os x completely if there was something like Photo Booth for ubuntu... I'm not joking, it's a killer app...)

---

### Post by spigolo on 2007-02-23
very interesting. i'm about to make the big jump and buy a 20" imac c2duo. i wanted it to dual boot, keep osx partion only for working (basically: only one application) and linux partition for everything else.
did you follow a specific howto? (i found many for macbooks and macbooks pro but none specific for the new imacs)
would you recomend to install the 64 bit version?

---

### Post by MichaëlVD on 2007-02-23
Since my last post, I managed to get Ubuntu Feisty and Mac OSX running side by side, with rEFIT to choose an OS at boot. I don't remember how I did it exactly, but you need the Ubuntu wiki and find something about installing ubuntu on a macbook. Then you'll also have to find out how to use rEFIT, but that can wait.

---

