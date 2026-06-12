---
title: "sending output to file in bash"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by skierkegaard on 2006-09-11
Whenever I try to use the '>' command (write output to file), bash is responding:
bash: foo.txt: Permission denied
No matter what the name, if I'm sudo or not.  Any suggestions?

---

### Post by goodfella on 2006-09-11
can you give an example of the command you are typing

---

### Post by goodfella on 2006-09-11
can you give an example of the command you are typing

---

### Post by skierkegaard on 2006-09-11
yeah, sorry about that.

sudo ls -l > foo.txt

something like that.

---

### Post by drummer on 2006-09-11
make sure you're in a folder that has correct ownership and permissions to let you and root write to it. Anywhere in your home dir should do.

---

### Post by skierkegaard on 2006-09-11
Thanks, I knew it was something simple like that.  I was in a folder with goofy permissions.

---

