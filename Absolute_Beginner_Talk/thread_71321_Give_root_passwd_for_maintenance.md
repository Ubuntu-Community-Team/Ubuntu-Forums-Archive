---
title: "Give root passwd for maintenance?"
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by mog27 on 2005-10-03
Last few times when Im booting up it says to give the root password for maintenance (and press Ctrl-D to bypass).  Well I usually bypass it, but when I give my root passwd it takes me to the shell.  What is it and how can I get rid of it?  Does it want me to run fsck?

---

### Post by joelito on 2005-10-03
you're booting into recovery mode, however i don't know exactly why you keep doing that. As for setting a root password. you can create one from a terminal by using the command
```

$sudo passwd root
password: (your account's password)
Enter new Unix password: (your prefered root password)
Enter again:
Password updated sucessfully

```

---

### Post by mog27 on 2005-10-03
Yup. I had grub default into the recovery mode option.

---

