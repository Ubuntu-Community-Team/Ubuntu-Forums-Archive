---
title: "What's up with Tracker Search Tool"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Djalmahal on 2008-02-11
Hi,

being new to Uuntu I was curious about Seacrh Tool Tracker, but it does seem to work, items that should show up don't show up etc. Is it automatically indexing, otherwise, I didn't find the place to tell it to re-index.

Thanks for repsonses

Andreas

---

### Post by FuturePilot on 2008-02-11
To force a reindex try
```
killall trackerd
trackerd -v 2 -R
```

---

