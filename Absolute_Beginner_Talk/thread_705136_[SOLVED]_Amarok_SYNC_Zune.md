---
title: "[SOLVED] Amarok SYNC Zune?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by articwolf939 on 2008-02-23
can they sync and if so how and if not what program can

---

### Post by igknighted on 2008-02-23
As of right now, there isn't a way to sync a Zune on linux.  There is work in progress, but nothing is usable yet.  You will need to keep a dual boot (or certain virtual machine setups) to sync it.  It's a shame, because aside from the lack of support on linux, I'd take a zune over that wretched ipod I have any day...

---

### Post by prkfriryce on 2008-02-24
> **igknighted said:**
> As of right now, there isn't a way to sync a Zune on linux.  There is work in progress, but nothing is usable yet.  You will need to keep a dual boot (or certain virtual machine setups) to sync it.  It's a shame, because aside from the lack of support on linux, I'd take a zune over that wretched ipod I have any day...

hopefully with Micorsoft opening up its proprietary MTP, linux developers will be able to solve it.

---

### Post by Luinfana on 2008-02-24
There's been some progress with libmtp, but files can only be displayed and deleted. Write-access is denied because the Zune waits for a secret handshake key from the Zune software to authenticate its connection. Until (a) Microsoft reveals something about the inner workings of this (not likely), or (b) someone analyzes the USB traffic between software and device enough to figure out how the handshake functions, you aren't going to be able to "sync" your Zune with Linux. I have VirtualBox with XP set up on my installation, pretty much solely for the purpose of syncing my Zune. But that's not a hack or a solution, it's just a workaround - and one that involves Windows. :(

Just be patient...someone will figure it out.

---

### Post by prkfriryce on 2008-02-24
> **Luinfana said:**
> There's been some progress with libmtp, but files can only be displayed and deleted. Write-access is denied because the Zune waits for a secret handshake key from the Zune software to authenticate its connection. Until (a) Microsoft reveals something about the inner workings of this (not likely), or (b) someone analyzes the USB traffic between software and device enough to figure out how the handshake functions, you aren't going to be able to "sync" your Zune with Linux. I have VirtualBox with XP set up on my installation, pretty much solely for the purpose of syncing my Zune. But that's not a hack or a solution, it's just a workaround - and one that involves Windows. :(

Just be patient...someone will figure it out.

This is what I was referring too:

[http://dailybriefing.blogs.fortune.cnn.com/2008/02/21/glasnost-at-microsoft/](http://dailybriefing.blogs.fortune.cnn.com/2008/02/21/glasnost-at-microsoft/)

---

