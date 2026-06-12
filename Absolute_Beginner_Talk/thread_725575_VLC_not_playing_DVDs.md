---
title: "VLC not playing DVDs"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Dom[i]no on 2008-03-15
Hello all.  I recently installed VLC on my machine so that I could play DVDs and MP3s.  My Ubuntu machine isn't connected to the internet so I had to get the packages individually from packages.ubuntu.com.  I installed all of the dependencies then VLC itself.  It plays MP3s perfectly, but DVDs cause a problem.  When I insert the DVD and open it with VLC, it pulls up the root menu as it should.  But if I click on any of the options, it shrinks back down to the compact size, as if it was just idle.  Any ideas as to why this happens?  I can try and get some more info if necessary.  Move this topic if need be, but I'm a beginner so it seemed appropriate.  Thanks in advance.

---

### Post by p_quarles on 2008-03-15
Most commercial DVDs have strong copy protection on them, which prevents playback if you don't have the correct codecs. Since these codecs have an ambiguous legal status in some countries, Ubuntu does not distribute them.

More information can be found here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

You can also download the individual codecs, just like you did with VLC and its dependencies.

---

### Post by Dom[i]no on 2008-03-15
Thank you.  Worked like a charm.  I must have over-looked the libdvdccs codec since it wasn't listed in VLC's dependencies.  But it works now so it's all good.

---

