---
title: "trying to make a file in /usr/lib access denied"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-06-15
How do I get write access to this file or gain access to owners account

---

### Post by H.E. Pennypacker on 2007-06-15
You will need administrative priviliges to do that.  Use sudo.  

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You can also open up the file manager (Nautilus) using these priviliges using GUI only, by pressing ALT-F2, and typing gksudo nautilus.  You will be asked for a password, enter it, and browse to the desired folder.

---

