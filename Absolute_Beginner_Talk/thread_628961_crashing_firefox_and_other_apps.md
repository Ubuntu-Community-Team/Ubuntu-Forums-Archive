---
title: "crashing firefox and other apps"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by tysonh on 2007-12-01
My fire fox will turn grey and is unresponsive.  my bittorrent is doing the same thing.  I've looked though similiar posts but I didn't see any answers there.

Am I missing a plugin in for firefox or something?  It crashed three times before I could load this page.  Thanks in Advance.

---

### Post by PmDematagoda on 2007-12-01
I am not really sure about Bit Torrent, but when my Firefox crashes, it revives itself after a a few moments, may be if you cared to wait a little yours would do the same.

---

### Post by alienexplorers on 2007-12-01
If you are running Advanced Graphics (Compiz) try turning it off and see if the crashes go away.

---

### Post by pressed on 2007-12-01
if your firefox crashes (just closes without freezing) only after going to certain websites, it might be the same font issue i had with mine. try typing
*export MOZ_DISABLE_PANGO=1* or just disable the "Allow sites to choose their own fonts" option in FF

before running this fix, i was getting the message
[I]Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Tahoma 8.25'
Segmentation fault (core dumped)[/I]

in the terminal after running firefox from there. if this fixes the stability issue, type 
*echo MOZ_DISABLE_PANGO=1* in the terminal

---

