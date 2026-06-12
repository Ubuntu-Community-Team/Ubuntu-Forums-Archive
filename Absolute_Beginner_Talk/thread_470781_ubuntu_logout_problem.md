---
title: "ubuntu logout problem"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by yuvlevental on 2007-06-11
when i try to logout, the background remains and so does the cursor. It freezes completely, and I have to reboot manually. What could be the problem?

---

### Post by yuvlevental on 2007-06-11
bump anyone?

---

### Post by yuvlevental on 2007-06-11
bump

---

### Post by Gagle on 2007-06-11
Have you tried looking in your system logs ?
Perhaps some info is there
.  Also, you could try ctrl-alt-backspace , wich resets the X server.  It will force a logout from your current session.  Not prettty but it works and seems better than a brutal power-off.

Hope it helps,

Gagle

P.S.  I'll try to see if a logout can be done using the terminal

---

### Post by Gagle on 2007-06-11
It seems to be a known bug for some users who upgraded to Feisty : [https://bugs.launchpad.net/ubuntu/+bug/85730](https://bugs.launchpad.net/ubuntu/+bug/85730)
Browse through the replies, a lot is said there.

regards,

Gagle

---

### Post by Gagle on 2007-06-11
Another way to debug/monitor your system shutdown is to enter the following in a terminal :

```
sudo strace gedit
```

HIH

gagle

---

