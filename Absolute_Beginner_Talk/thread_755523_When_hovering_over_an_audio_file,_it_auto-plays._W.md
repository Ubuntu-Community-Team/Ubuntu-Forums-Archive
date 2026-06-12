---
title: "When hovering over an audio file, it auto-plays. Why?"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Jackelope on 2008-04-14
I installed several audio codecs and encoders, as well as SoundKonverter, and now when I hover my mouse over a music file in nautilus, it starts playing automatically. This is a great feature, but I have no idea how it got there :confused:. Could someone please tell me what I accidentally installed to get this feature? Thanks.

---

### Post by VoidedCheck on 2008-04-14
I think it was always there.  In a Nautilus window, Edit  --> Preferences --> Preview tab, Sound Files, Preview sound files: switch to Always, Local Files Only, or Never.

---

### Post by estaticd on 2008-04-14
This should be what caused it... pretty sweet find!

sudo apt-get install mpg123-esd

---

### Post by bt224 on 2008-04-14
It's the default. You can turn it off as mentioned in the second post.

---

### Post by Jackelope on 2008-04-14
Thanks! I didn't know the feature was already installed in Nautilus. Maybe it wasn't working with MP3 files until I installed Mpg123. That's my guess, anyway. Thanks again for the help. :)

---

