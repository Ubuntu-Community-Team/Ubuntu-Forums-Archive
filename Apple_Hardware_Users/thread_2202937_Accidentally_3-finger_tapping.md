---
title: "Accidentally 3-finger tapping"
date: 2014-01-31
forum: Apple Hardware Users
---

### Post by Brandon_MacEachern on 2014-01-31
Hello, I am using Ubuntu 13.10 on my MacBook Pro Early 2011, and all works well.  Except for one thing, when 2-finger scrolling, I keep accidentally 3-finger tapping the pad, and keep accidentally triggering the window switcher screen.  Normally the answer is, just use the pad better.

However 2 things.  1, sometimes it seems my 3rd finger isn't actually touching it, and still somehow accidentally triggers, and 2, I am actually disabled and have shakey hands at times, and it's just difficult to manage.

I've tried to see ways to permanently remove it, but it appears to be hard coded into Unity.

---

### Post by mikewhatever on 2014-02-01
This is a guess, as I am not at all familiar with macbooks. Usually, the three finger tapping is governed by the "synclient ClickFinger3" setting. If that's the case, then running "synclient ClickFinger3=0" in a terminal window should disable it.

PS:You can check the defaults by running "synclient -l | grep ClickFinger". (-l <--that's a dash and a small L)

---

### Post by Brandon_MacEachern on 2014-02-01
> **mikewhatever said:**
> This is a guess, as I am not at all familiar with macbooks. Usually, the three finger tapping is governed by the "synclient ClickFinger3" setting. If that's the case, then running "synclient ClickFinger3=0" in a terminal window should disable it.

PS:You can check the defaults by running "synclient -l | grep ClickFinger". (-l <--that's a dash and a small L)
Hmm, according to this, it's already on 0 for ClickFinger3.

    ClickFinger1            = 1
    ClickFinger2            = 3
    ClickFinger3            = 0

---

### Post by Brandon_MacEachern on 2014-02-01
Ok doing synclient ClickFinger3=2 actually fixed the issue.  3=0 just turns the problem back on.

---

### Post by Brandon_MacEachern on 2014-02-02
How do I make this permanent?  A reboot enabled the tapping again.

---

### Post by mikewhatever on 2014-02-03
Just add the desired command to session autostart. Glad you've figured it out.

---

