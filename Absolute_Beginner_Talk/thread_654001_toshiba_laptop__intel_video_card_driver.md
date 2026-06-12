---
title: "toshiba laptop / intel video card driver"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by chaddiesel on 2007-12-30
I have a toshiba satellite laptop with an intel 945GM video card.
I've read somewhere that ubuntu loads all of the restricted drivers for intel cards whenever you install. My video is a little choppy and the restricted drivers aren't showing the video card being supported.

The main reason I can tell that it isn't working correctly is that I can't play a few games. They immediately say to lower resolution and such.

What can I do?

---

### Post by p_quarles on 2007-12-30
The drivers for onboard Intel graphics are open source modules, so there's no need for the restricted ones. The only thing I can suggest is that you may need the 915resolution patch for that card. That will fix a few of the common resolution problems with that series of Intel cards.

---

