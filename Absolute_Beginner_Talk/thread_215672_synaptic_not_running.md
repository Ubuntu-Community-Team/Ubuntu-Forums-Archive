---
title: "synaptic not running"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by pjeeanah on 2006-07-14
When asked for password, I give the password I created during the install of ubuntu 6.06. However it says that the password is wrong.

So I enabled root password and gave it this password, when prompted by Synaptic. However nothing seems to happen when I click OK. The password dialog box just disappears and Synaptic does not open.

Anyone has any ideas? Thanks.

---

### Post by Paerez on 2006-07-14
you need to use your password, not the root one, so your first try was correct.

Try running it from the terminal, like this:
```
# sudo synaptic
```

and see if you get helpful error messages.

---

