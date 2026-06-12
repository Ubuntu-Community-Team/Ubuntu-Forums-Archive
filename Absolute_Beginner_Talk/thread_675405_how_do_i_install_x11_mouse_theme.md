---
title: "how do i install x11 mouse theme"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2008-01-22
how do i install a mouse theme?

---

### Post by chris200x9 on 2008-01-22
7: Cursors

The next thing you may want to change is your mouse cursors. You can do this under
System->Preferences->Mouse under the cursors tab. Still you can't add new cursor themes here, so you basically have two ways.

The simplest is to install gcursor, which is in the repositories
Code:

sudo apt-get install gcursor

It will show up under System->Preferences->Cursor Selection and it lets install new cursors. It is quite strange, but it doesn't let you delete themes, so you have to manually remove cursors themes, which are stored under ~/.icons.

The fact that cursors are stored in the same folder as icons can be annoying, because cursor themes will show up under the icon themes settings. Yet this can be useful to remove cursors (just the same way you'd remove icon themes), even if is not intuitive to do.

The second way to install cursors is, as you can now guess to unzip the theme, which usually will be a tar.gz file, under ~/.icons.

I would highly recomend:

[http://ubuntuforums.org/showthread.php?t=203093](http://ubuntuforums.org/showthread.php?t=203093)

---

