---
title: "System sounds"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by s14sh3r on 2007-12-24
I'm not sure if I'm posting this in the right place, but where can I find the startup sound on a live cd? I have the 6.04 Dapper cd and I like the startup sound and would like to use it. I can't seem to find it on the cd, any ideas?

Thanks

---

### Post by nick_h on 2007-12-24
/usr/share/sounds/startup.wav

---

### Post by s14sh3r on 2007-12-24
> **nick_h said:**
> /usr/share/sounds/startup.wav

That works for my computer, but not the Live CD. The file structure isn't the same. I tried searching the cd for startup and found nothing.

*Edit*

I found what I was looking for. I was trying to browse the cd itself. I had to boot to it to see the file system and copy the sounds. Thanks!

---

### Post by nick_h on 2007-12-24
Do you want to find the file on the CD without actually booting to the Live CD?

The startup.wav file is actually stored within a deb file on the CD.

/pool/main/u/ubuntu-sounds/ubuntu-sounds_0.3_all.deb

---

