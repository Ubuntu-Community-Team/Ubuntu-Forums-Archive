---
title: "[SOLVED] &amp;quot;Frozen&amp;quot; appearance preferences?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by berZirker on 2007-10-22
I just installed ubuntu 7.10 64 on my emachines m6809. Nearly everything is working beautifully. One remaining issue is the theme menu. The "Appearances Preferences" window acts very sluggish (to the point that, if any other window started acting like that, I would think it was frozen and reboot.) The buttons are not frozen for some reason: when I click on theme>customize it brings up a window (not sluggishly for some reason) but the new window has no information. If I act like everything is working and click a different tab (which doesn't change anything visually) and then move down to where a button <would> be, it will respond with another vacant window.  It If anybody can give me a lead as to why this might be it would be greatly appreciated. 

BTW: I ran TOP just to check, and it showed the user window "Appearances Preferences" using over 90% of the CPU. Am I really the only one having this problem?

Anybody else having this problem too?

In case anybody needs it, I solved this problem with
> sudo apt-get remove gtk-qt-engine

Thanks to Askeptykal and eltadcirad1on this post:
[http://ubuntuforums.org/showthread.php?t=574463&highlight=gutsy+appearances](http://ubuntuforums.org/showthread.php?t=574463&highlight=gutsy+appearances)

---

