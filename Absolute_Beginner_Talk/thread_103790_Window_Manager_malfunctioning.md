---
title: "Window Manager malfunctioning"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by johnnymo87 on 2005-12-14
I have this problem with window manager. When I boot up and enter the GNOME session, this splash says "window manager". I click it, and it goes away.

The problem is that I don't have those minimize, restore, or close buttons in the upper-lefthand of any of my windows. I can't close anything!

Also when I click my "go to desktop" shortcut, it says *Your window manager does not support the show desktop button, or you are not running a window manager.*

When I go to preferences for my window manager, it says ***Cannot start the prefernces application for you window manager.** Window manager "unknown" has not registered a configuration tool.*

On a side note ...

When I click on my recycling bin nothing happens.

Also,

How do I access a "My Computer" (Windows filesystem explorer) type of thing in linux?

How do I get icons onto my desktop?

---

### Post by johnnymo87 on 2005-12-15
:-({|= ... bump

---

### Post by kaamos on 2005-12-15
Just a thought. Open a terminal and type:
```

killall metacity
killall nautilus
nautilus &
metacity &

```
And let me know if anything has changed

---

### Post by luxor on 2006-07-25
I had the same problem, and I found that metacity was not running.  Somehow, metacity was no longer one of the apps included in my session.  So I ran metacity based on Kaamos' suggestion, and everything works fine now.  Thanks Kaamos.

---

