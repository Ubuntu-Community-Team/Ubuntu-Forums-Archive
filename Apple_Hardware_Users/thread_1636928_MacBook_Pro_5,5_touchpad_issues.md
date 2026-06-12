---
title: "MacBook Pro 5,5 touchpad issues"
date: 2010-12-03
forum: Apple Hardware Users
---

### Post by jmasterx on 2010-12-03
My biggest problem has always been with this touchpad. The fix that I have makes it so that if you click and drag, then release a finger too early, the drag fails. It makes it almost unusable. It is also overly sensitive. I was wondering if anyone has found a solution to this. Right now it is the only thing stopping my migration from Windows.

Thanks

---

### Post by Skinner_au on 2011-01-24
Yeah I'm looking for one too. I have the 2009 MBP (5.5?) which is almost unusable in ubuntu due to it's sensitivity as it's almost impossible NOT to touch the touchpad while  typing and throwing my mouse all over the screen (and more than a few inopportune mouseclicks).

I did one of the hacks mentioned for a previous version (blacklisting the usbhid driver to ensure it loads after the BCM driver) but I can't notice any difference.

In SYSTEM-> Preferences-> Touchpad there is a sensitivity setting which appears to be automaticaly reset the middle of the slider after I exit the control panel. I suppose it's possible that just means that feature isn't implemented with the BCM5974 driver. The acceleration works and continues to work, but doesn't survive reboots or resumes.

I don't have multitouch other than two-finger scroll, but I could live with that if it's bump-resistance could be increased.
There's a thread on here where someone was modifying the XOrg.conf file but unfortunately didn't have any success a couple of years ago.

Anyone got a magical fix? Please?

tks in advance

Sk

---

### Post by cdnaerogeek on 2011-01-24
I have the same version of Macbook Pro, and the touchpad worked quite well out of the box. If you haven't already done so, do the following:

1) Go to System -> Preferences -> Mouse (I'm working under 10.04 LTS, it may be different for your version)
2) Under the "Touchpad" tab, you should see two check boxes under "General", one with "Disable touchpad while typing" and one with "Enable mouse clicks with touchpad." Check the first one and uncheck the second.

That should get rid of most of the sensitivity issues. You'll have to push down fully on the touchpad to click, but it's a small price to pay.

---

### Post by Skinner_au on 2011-01-25
yeah thanks for that, not sure why i didnt think of it before. It'd be nice if tap-clicks worked as I pretty much rely on it, but this is better than having my mouse clicking all over the screen while i'm typing.

Oh for a driver patch. With any luck the 11.04 gods will smile upon us.

Thanks again

Sk

---

### Post by bilallucky on 2011-01-25
I advice you to create a new user account and logging on your [MacBook Pro]("http://www.browse-tools.com/apple-macbook-pro-features-review/") then logged off and signed back into the primary user account and multitouch continued to work.This must be a software issue i think.I have same issue i just deleted the temporary user account and everything seems to be working fine.

---

