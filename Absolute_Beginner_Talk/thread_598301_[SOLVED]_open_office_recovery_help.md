---
title: "[SOLVED] open office recovery help"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by celticbhoy on 2007-10-31
Having a problem with open office 2.3. Every time I start it goes to recovery of a lost document due to a crash. there is no document listed and it takes me to writer when I select 'ok'. This happens if I try to create any kind of open office document, ie presentation, or database. I think there must be a file left from a proper recovery that has not been deleted. Does anyone know how to fix this. I have tried to un-install and re-install from fresh.

using Gutsy

---

### Post by caffienefree on 2007-10-31
This seems like it might be related to [https://launchpad.net/ubuntu/+source/openoffice.org/+bug/33444](https://launchpad.net/ubuntu/+source/openoffice.org/+bug/33444)

I would comment there that you're still seeing the same occurrence.

---

### Post by Steve1961 on 2007-10-31
There seems to be a bug in the openoffice.org-gtk package when working with some themes.  You can uninstall this package or revert to the human theme - mine works ok when I do this but crashes every time when using crux

---

### Post by celticbhoy on 2007-11-01
Thanx. That worked fine after I removed the gtk package.

---

### Post by Pevichaey5 on 2007-11-03
hi

jus a question as i have the same problem, is it ok to remove openoffice.org-gnome as it trys to remove it with th gtk thing

cheers

---

### Post by Steve1961 on 2007-11-03
Yes, no problem.

---

