---
title: "Alacarte - can't make changes...  ??"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by ccheaton on 2007-02-18
I'm trying to make changes with Alacarte, but I am unable to show or hide any of the options in the menus.  Clicking on the check box doesn't do anything.  I've tried getting into it from both right-clicking on Applications and from Alt-F2 and typing gksu alacarte...  It opens and runs, I can move things up and down, but cannot show or hide them.  Any thoughts? It's a fresh install and I haven't installed anything particularly strange, just a few things through Automatix, such as Nvidia drivers and the Debian menu (which doesn't show in the menu...).

Any idea how to fix this problem?

---

### Post by islander_810 on 2007-02-18
Well the very same thing happ to me in my last Ubuntu installation. Dunno why it happens or how to correct it. But this is a workaround...

type "sudo alacarte" in the terminal

that's it, make the changes.

If that doesn't work, try this longer method

"cd /usr/share/applications"
open the corresponding .desktop file in a text editor
near the ending lines, there's a line called, "NoDisplay=True", just comment it out

That should work

---

### Post by ccheaton on 2007-02-19
Thanks for the response.  Your first suggestion doesn't work.  As for commenting out the line, that seems like a laborious way to continue to manage the menus.  Would it be safe to uninstall and reinstall alacarte?  Does anybody else have an idea why this might happen?

---

### Post by surxain on 2007-02-21
I meet the same problem. How to fix it?

---

### Post by IcemanV9 on 2007-02-27
Alacarte doesn't work at all in Dapper (isn't it LTS?!). It drives me batty for a long time. I have already tried -reinstall option. No luck. It is definitely a bug ([[COLOR="Orange"]#85216[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/85216")).

---

### Post by islander_810 on 2007-02-27
i was facing the same problem. then when i reinstalled ubuntu (from the same setup cd), it disappeared. dunno why. both methods worked for me tho

---

