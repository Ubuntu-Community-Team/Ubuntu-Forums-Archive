---
title: "My libc6 is giving me problems."
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-01-23
Is there any way to roll back my version of libc6? I currently have v.2.7, but I have several packages complaining that that version is too NEW, and that I need to have v2.6 instead.

I tried to click "mark for removal" next to libc6 in Synaptic, but it wants to remove what appears to be the majority of my system along with it. It didn't look safe to follow through with that process, so I didn't.

What do I do?

---

### Post by mssever on 2008-01-24
> **doctorbighands said:**
> Is there any way to roll back my version of libc6? I currently have v.2.7, but I have several packages complaining that that version is too NEW, and that I need to have v2.6 instead.

I tried to click "mark for removal" next to libc6 in Synaptic, but it wants to remove what appears to be the majority of my system along with it. It didn't look safe to follow through with that process, so I didn't.

What do I do?

You can try setting the version explicity through apt-get: ```
sudo apt-get install libc6=2.6.1-1ubuntu9
``` Be sure to specify the full version that you want. My example is the current version for Gutsy.

This isn't guaranteed to work, however. APT isn't very good at downgrading. If it doesn't, you're out of luck. For the future, unless you know exactly what you're doing, you shouldn't touch libc6 unless you're upgrading to a new Ubuntu version or a new version is released as a part of the standard Ubuntu update process.

---

