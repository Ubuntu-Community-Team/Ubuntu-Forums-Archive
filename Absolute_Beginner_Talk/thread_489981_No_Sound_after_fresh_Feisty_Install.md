---
title: "No Sound after fresh Feisty Install"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Rush_898 on 2007-07-01
the only place I know to check is System  > Preferences > Sound.  I see my mobo sound card is recognized.  It is chosen as the sound playback option.  I thought maybe it was the speakers so I tried headphones and no sound either.  I went to the alsa mixer and made sure it wasn't muted.  I had Dapper on here before this and the sound worked without problem.  Where/what else can I check?  I'm really baffled here.  Thanks.

---

### Post by Marshall2day on 2007-07-02
Check your primary output channel in alsamixer. I had the same problem and had to change it to PCM.

---

### Post by Rush_898 on 2007-07-03
ok if I type alsamixer into the terminal I get a kind of terminal menu for moving the volume stuff around but how do I tell which is the primary output channel?

---

### Post by Hobo Joe on 2007-07-04
I could use some help on this too, I've already tried all the basic fixes for this, and none of them have worked so far.

---

