---
title: "Can't get audio working with 10.04 on iMac 27&quot; i7."
date: 2010-04-18
forum: Apple Hardware Users
---

### Post by jisaac on 2010-04-18
Hi,

I have sound using my headphone without any trick but my internal speakers don't work.

Do some manage to make them work on an iMac 27" i7 and Lucid Lynx?

Thanks.

---

### Post by markbirss on 2010-04-18
Hi,

Im running Beta 2 10.04

1. Install

sudo apt-get install linux-backports-modules-alsa-lucid-generic gnome-alsamixer

2. Reboot

3. Check output is on "Internal Audio Analog Stereo" on Sound Preferces (system - prefereces - sound)

4. Open gnome-alsamixer

increase "front sp" and "headphone" volume

---

### Post by jisaac on 2010-04-21
Thanks markbirss!

That's now working for me. Will make tests to look at the sound quality!

Regards.

---

### Post by jisaac on 2010-04-21
So far the sound quality looks good. This is user point of view, demanding one but not audio professional ;)

---

### Post by ifknot on 2010-07-01
Thanks :D

---

