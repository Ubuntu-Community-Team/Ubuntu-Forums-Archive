---
title: "Just bought a Power Mac G4 and need to run test."
date: 2009-01-28
forum: Apple Hardware Users
---

### Post by Gen2ly on 2009-01-28
I bought a old Power Mac G4 Sawtooth and I'm trying to install Ubuntu on it but I'm getting a blank screen when I try to boot the CD holding C and nothing when I hold Option down (just circular arrow and a forward arrow button).  I did have an old Mac OS 9 installcd around and that I was able to install and check if the firmware was updated (it is), but have had no luck getting any Linux CD to boot (I'm pretty sure they don't but the CD/DVD-ROM drive is pretty quiet).

I just read that Apple has released their [PowerPC Hardware Test Images]("http://www.info.apple.com/support/aht.html").  And I think it would be a good idea to check the hardware, but I need help with this.  The download is an dmg and the Power Mac doesn't have a CD Burner.  I've tried dmg2iso and dmg2img and both failed, I've even tried Acetoneiso2 with no luck.  I did learn that the Mac OS X Disk Utility can covert it.  Could someone with Mac OS X convert it for me?

```
hdiutil convert /path/to/filename.dmg -format UDTO -o /path/to/savefile.iso
```

Another howto do it is, [here]("http://forums.whirlpool.net.au/forum-replies.cfm?t=940978#r7").

---

### Post by mkvnmtr on 2009-01-28
If you are having trouble booting from a Ubuntu install disk maybe it is not burned as an image. Where did you get the disk? What system do you have access to to reburn a disk?

---

### Post by Gen2ly on 2009-01-28
Ah, I figured it out!  This is an old firmware and looks not to be programmed to recognize seeing yaboot.  I entered:

```
boot cd:,\install\yaboot
```

My bad.  Would really appreciate though if anyone would convert the G4 Hardware Test to iso format, this is a reallyold mac and would really like to be able to check the hardware first.  I'm at Dirk period R dot Gently at gmail hmm com.

---

### Post by cyberdork33 on 2009-01-28
> **Dirk.R.Gently said:**
> Ah, I figured it out!  This is an old firmware and looks not to be programmed to recognize seeing yaboot.  I entered:

```
boot cd:,\install\yaboot
```My bad.  Would really appreciate though if anyone would convert the G4 Hardware Test to iso format, this is a reallyold mac and would really like to be able to check the hardware first.  I'm at Dirk period R dot Gently at gmail hmm com.
I'll work this for you Dirk. Long time, no see man!

---

### Post by Gen2ly on 2009-01-29
Definitely good to see you too cyber.  Looks like you've been keeping busy in the forums ;).

Ah, yes, now I can see if the hardware is up to snuff.  

Just did a check and all is good.  Now I can build a running linux server.

Appreciate the help cyber!

---

