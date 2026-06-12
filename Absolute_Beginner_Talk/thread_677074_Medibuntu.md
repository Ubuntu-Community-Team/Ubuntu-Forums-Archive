---
title: "Medibuntu?"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by BarfBag on 2008-01-24
What is the difference between adding and using Medibuntu (as a repository) and using the codecs from the default repos?  If I'm not mistaken, they're in there now, correct?

---

### Post by PeterJS on 2008-01-24
> **BarfBag said:**
> What is the difference between adding and using Medibuntu (as a repository) and using the codecs from the default repos?  If I'm not mistaken, they're in there now, correct?

It's not so much that they're newer, its that they are in a legally gray area under US law. Some of them are wholesale illegal like libdvdcss2, others require nonstandard licensing requirements like w32 codecs requiring a windows licenses to be used legally, and some of them are just comercial pakages from companies that don't have contracts with Canonical, like adobe reader and google earth,

---

### Post by FuturePilot on 2008-01-24
The Medibuntu repository has a few things that are not in the Ubuntu repos for legal reasons like libdvdcss2 and w32codecs and some other non-free stuff like Acrobat Reader and Google Earth. Also some of the stuff like Mplayer is built against the restricted codecs whereas the MPlayer in the Ubuntu repos has disabled all the restricted stuff.

---

### Post by BarfBag on 2008-01-24
Thanks for the help!

I'm aware of the questionable legality of libdvdcss2 and w32codecs, but aren't the codecs for at least .MP3 playback included in the default repositories?  I remember when Gutsy (or was it Feisty?) first came out, getting .MP3 playback was possible through Add/Remove Programs.  My question is - if I just want DVD and .MP3 support, what's the difference between Medibuntu and the default repositories?

---

### Post by FuturePilot on 2008-01-24
Yes, the codecs for mp3 are in the Ubuntu repos. AFAIK they always were in the repos, it's just that before Feisty the non-free repos were disabled by default, now they are enabled by default.

---

