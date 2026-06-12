---
title: "Gusty freezes for 10s from time to time."
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by ralphz on 2007-12-02
Hi

From time to time my Gusty freezes for 10 - 15 seconds then everything is ok. I have noticed that during that time my hdd LED on the case is lit solid. That means that some process is writing or reading to the hard drive. Does anyone have the same problem?

---

### Post by FakeOutdoorsman on 2007-12-03
It could be updatedb running in the background.  If you could open up a terminal and use the "top" command somehow while your computer is frozen it might show "updatedb", "find", or "sort" at the top of the list.  updatedb creates a database of file locations for the "locate" command.  Try running updatedb and see if it freezes:

```
sudo updatedb
```

---

