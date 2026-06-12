---
title: "Refreshing Menus?"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-09-29
After a system update in kubuntu I noticed I got all these menu entries for wine apps I had installed (entries that werent there, so now im happy :D) I was wondering if there is a command for refreshing the menu?

---

### Post by %hMa@?b&lt;C on 2006-09-29
wouldn't "killall kicker" do it?
edit: you need to enter "update-menus" into terminal. thats the command!

---

### Post by Marsolin on 2006-09-29
kbuildsycoca

That command tells kicker to refresh the menu. It looks through a few directories for .desktop files. If your extra menu entries still exist after running it then there are .desktop files that exist.  Most likely somewhere in a hidden folder in your home directory.

---

### Post by WalmartSniperLX on 2006-09-30
Alrighty. Thanks :D

---

