---
title: "Hardware Requirements"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by VladTheImpaler on 2008-02-09
I've got a couple of PC's running 6.06 Dapper that we use for Internet and light word processing.  They are Dell Dimension XPS-T machines sporting:

PIII 1GHz processor
768 MB of necksnapping PC100 RAM
GeForce 3 Video
Soundcards that work
NICs that work

I haven't upgraded Ubuntu because these old beasts do what we need and I've been too busy/lazy to spend the time.  These machines exceed the recommended minimum requirements, but will they really run Gutsy or the upcoming Hardy?

---

### Post by neurostu on 2008-02-09
They should run Gutsy and Hardy just fine, but i would recommend leaving off the desktop effects.

---

### Post by VladTheImpaler on 2008-02-11
For S&G I installed Gutsy and let it roll.

With desktop effects off it runs OK.
With desktop effects Normal it runs but frequently hangs up.
With desktop effects Extra Gutsy locks up.

So desktop effects are video card dependent.  What's the minimum card to run them?

---

### Post by jw5801 on 2008-02-11
Compiz (desktop effects) will run on most video cards, provided you're using the correct driver for them rather than the generic vesa drivers.

---

### Post by VladTheImpaler on 2008-02-12
I enabled the restricted nvidia drivers that Gutsy wanted  after instalation.

I found that the problem was Audacious.  When I closed it, the desktop effects ran fine on extra.  I can run xmms, a website on firefox, a spreadsheet, and a word document simultaneosly and the effects ran flawlessly.

Audacious wasn't that great anyway and I won't miss it.

---

