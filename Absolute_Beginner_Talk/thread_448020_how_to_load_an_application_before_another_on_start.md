---
title: "how to load an application before another on startup?"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by revealer on 2007-05-18
when i log in, screenlets and beryl automatically initiate because they're inside my ~/.kde/Autostart/ folder...
screenlets always initiate first, but they need beryl for transparency issues so i need screenlets to start with some delay :S
how can i do that?
thanks

---

### Post by PgR on 2007-05-18
In the .desktop file put the line
X-KDE-autostart-after=*xxxx*

[http://l10n.kde.org/docs/admin/autostart-and-runonce.html](http://l10n.kde.org/docs/admin/autostart-and-runonce.html)

---

