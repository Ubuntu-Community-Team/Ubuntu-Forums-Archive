---
title: "terminal entry"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by abbrew on 2006-03-03
I open the terminal window, type the su command and then get a password prompt, but cannot enter my password.  I press keys and nothing happens.  Any help much appreciated!  Thanks.

---

### Post by mhl12 on 2006-03-03
that usually happens. Just type in your password and press enter. It should work.

---

### Post by suRoot on 2006-03-03
Unless you've changed root's password, which you probably haven't, you don't have a password for root - so you can't su.

The ubuntu way of doing it is to sudo, eg.

```
sudo shutdown
```

Try that instead of su'ing to root.  If you need to su to root, dig around the forums & you'll find the answer.

---

