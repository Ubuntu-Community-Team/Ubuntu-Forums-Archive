---
title: "How to change update URL link"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by sikandarnoori on 2006-09-25
hi all,
i want to know how can i change the location of download link of update manager, because when i want to update, it needs download from cn (China) URL, which has so much slow speed and responding.
thank you

---

### Post by siacs on 2006-09-25
You can change the two letter country code by

using Synaptic, goto Settings > Repositories > Edit > Custom 

or

manually editing in /etc/apt/sources.list

---

### Post by siacs on 2006-09-25
Remember in manual editing you need to open sources.list with sudo priviledges

press Alt and F2

type gksudo gedit 

then open sources.list from there

---

