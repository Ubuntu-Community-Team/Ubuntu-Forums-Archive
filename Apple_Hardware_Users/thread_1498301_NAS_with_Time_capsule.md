---
title: "NAS with Time capsule"
date: 2010-05-31
forum: Apple Hardware Users
---

### Post by banff2010 on 2010-05-31
Which command/documents  should I use to access Time capsule (500GB) from my linux 10.04 PC?
I am hoping to attach all my USB hard drives to Time capsule and make it like a poor man's NAS without installing linux on the time capsule or iMac. Right now, I manually plug them from PC to imac and USB drives are already in NTFS format.

Thanks

---

### Post by sha.goyjo on 2010-06-01
I've never used a time capsule before, but for lack of other replies I'll attempt to give you some information.

See if you can find it's local network ip. If you can, try a few different connection methods. Ftp,ssh, and definitely samba. You can research them elsewhere on the forums. Also, try using netatalk. You can research it on their websites.

I actually know nothing about this, and if anybody else would have answered your question, I'd be keeping my mouth shut. But this is the best advice I can give you. I've never actually seen a time capsule in person, nor really played around much with NAS.

Sorry I couldn't be more helpful.

---

### Post by sha.goyjo on 2010-06-01
Okay, a thought just occurred to me. Try
```

$sudo apt-get install service-discovery-applet

```
Add it to your panel, and see if you can see the timecapsule on there. If you can we might have some success.

---

