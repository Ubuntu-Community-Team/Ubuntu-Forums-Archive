---
title: "Is it necessary to defrag ntfs partition?"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by dinostabOMG on 2008-04-15
I have an NTFS partition with Windows XP x64, then an ext3 partition with Gutsy 64-bit, then my swap. I recently expanded the NTFS partition at the expense of the ext3 partition in order to use the space for a project. I'm done with this, so I want to know if I have to defrag the NTFS partition again if I want to contract it and give the space back to Ubuntu.

---

### Post by Fire_Chief on 2008-04-15
I would say this is definitely a good idea.
Though I'm curious. If the disk space is not significantly large, is there a strong motivation for moving it back and forth like this? You could just leave it as NTFS and then use the ntfs-3g module to access it from Ubuntu. That way both OSes can use the space.

---

### Post by dinostabOMG on 2008-04-15
Thanks. I will look into this module.

I am a computer animator and I am interested in migrating to Ubuntu completely, but at the moment I can't because of a few unsupported pieces of software (although the latest major one, 3ds max 9, is reportedly working in Wine now, though I haven't had success yet). Still, I try to do most things in Ubuntu and I like to think of the NTFS space as just there as a contingency.

---

### Post by Sidewinder1 on 2008-04-15
Another vote to defrag.; it certainly can't hurt. Unless of course you have a power failure during the proceedure. :-)

---

