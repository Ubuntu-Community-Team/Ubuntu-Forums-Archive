---
title: "how do i set up a root password + checking for wrireless"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by wannaBeHacker on 2007-01-10
Hey can someone tell me how to set up a root directory through terminal

and how do i check to see if there are wireless access points where i am?

---

### Post by JamieC on 2007-01-10
Well to scan for access points, open a new terminal window and run the following (where <device> is the name of your wireless interface, usually wlan0):

```

iwlist <device> scan

```

---

