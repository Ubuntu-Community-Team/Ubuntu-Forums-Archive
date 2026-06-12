---
title: "collecting shells"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-06-08
In my long-lasting battle to get my BROTHER HL1230 printer working across the hallway, I found yet another HOWTO with the following line

Install csh &#8211; this is required:
----------------------------------

sudo aptitude install csh

Hence the question: can you have more than one shell installed and operating at any time? Or will installing csh kill bash?

---

### Post by Najand on 2007-06-08
Yep, sure.... After installing csh, you can use
```

csh

```
command to switch to csh and ```
 exit
``` to exit. You can also change your shell permenantly by editing /etc/passwd file.

---

### Post by pmg on 2007-06-10
Better than editting /etc/passwd by hand, use **chsh** to change your login shell.  (If you mess up /etc/passwd you can have a bad day.)  Anything listed in /etc/shells can be used as a login shell - not that you'd want to.  (2nd note, don't make your shell /bin/false.)

---

