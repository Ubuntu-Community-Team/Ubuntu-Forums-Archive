---
title: "Won't Install/Update"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by hiroziro on 2007-12-20
Every time I try to install a new program or update, I get this:

[I]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I]

I'm new to this so I'll need very detailed instructions to walk me through. Sorry .

---

### Post by bump_ on 2007-12-20
The error message tells you what command to try next. Enter this into the terminal

```
sudo dpkg --configure -a
```

Hope it helps.

---

### Post by hiroziro on 2007-12-21
> **bump_ said:**
> The error message tells you what command to try next. Enter this into the terminal

```
sudo dpkg --configure -a
```

Hope it helps.
 
 I don't know were to go to enter the command. I tried entering it into the error box but nothing happen.

---

### Post by bump_ on 2007-12-21
Go to Applications>Accessories>Terminal

then cut and paste the above command.

---

### Post by hiroziro on 2007-12-21
Thanks. That got it going.

---

### Post by bump_ on 2007-12-21
Glad to help :)

---

