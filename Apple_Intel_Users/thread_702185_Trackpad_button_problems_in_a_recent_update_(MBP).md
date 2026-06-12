---
title: "Trackpad button problems in a recent update? (MBP)"
date: 2008-02-20
forum: Apple Intel Users
---

### Post by Skitalets on 2008-02-20
Have any other 7.10 users on Macbook Pros noticed problems with the trackpad button in the last few days?  I am finding that when I tap and release the mouse button, my laptop thinks I have only depressed it (but not let up).  So as I drag across the screen, text gets selected, Alt-Tab and Apple-Tab are broken (because X thinks I'm in the middle of clicking), etc.  Really annoying.

However, when I tap the touchpad itself to click, none of this happens.

This started up maybe three or four days ago.  I did install a few updates then -- I think some small kernel changes and a few other things.

Anyone else seeing this?

---

### Post by cyberdork33 on 2008-02-20
If you have special option set in your xorg.conf, try commenting them out and restarting. If you get the same behavior, then I would file a bug report. You also need to specify which Macbook Pro you have.

---

### Post by Skitalets on 2008-02-22
It's a first-gen MBP.  I think it's actually related to enabling horizontal scrolling.  I just realized I did that before the problems started -- I just reinstalled for other reasons and I'm not seeing this same behavior anymore, even with the latest updates.

---

