---
title: "Server Edition: changing user password"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by ImpelGD on 2007-06-14
I've just received a new PC with Ubuntu Server Edition pre-installed, and I'd like to change the password of the user account. How do I do this from the command line, and will it change the root password too? (If not, how do I?)

Thanks.

---

### Post by Catsworth on 2007-06-14
Open a terminal and take a look at the man pages for the 'passwd' command, like this:

```
man passwd
```

That should tell you all you need to know.  Note, changing your user password won't change the root password because there isn't one normally.  Ubuntu usually installs with the root password set as null, you then use sudo or su in order to carry out 'root' tasks.

---

### Post by ImpelGD on 2007-06-14
Thanks for the clarification. :)

---

