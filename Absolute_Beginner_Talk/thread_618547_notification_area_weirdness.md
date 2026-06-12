---
title: "notification area weirdness"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Evil Wayz on 2007-11-20
Is there a properties or manager for notification area? MY wirelss bars have disappearedd. I tried adding them manually, didn't work.

I created a new user, and boom, the wireless bars show up fine in the notification area. 

So it's just my original account that won't show me the update manager or wireless bars.

Any thoughts? Any file I can edit? Have I disabled something unknowingly?

---

### Post by Arthur Archnix on 2007-11-22
Make sure nm-applet is in your session startup. Go to >system>prefernces >sessions and look for Network Manager. If it's not there, add it.
The command is nm-applet --sm-disable

---

