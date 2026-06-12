---
title: "Cannot execute c/cpp files as user?"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by kanna1620 on 2007-01-13
Iam very much new to Ubuntu.
I installed gcc and g++ and compiled both c and c++ programs.
when I execute them using the command
**a.out**
as a user i got an error saying that **a.out:command not found**
I copied the **.profile** from the root to the user,but still it is not working.In the **.profile** i placed a single line which is:
** PATH=$PATH:.**
But it is still not working.But when i give the command as **./a.out** then it is working.How to get the **a.out** worked for the user?
Plz anybody help me.
Any help would be greatly appreciated.

---

### Post by taurus on 2007-01-13
Move it to /usr/local/bin (or even ~/bin) and modify your ~/.bashrc to include it in your path.

```
PATH=$PATH:/usr/local/bin:~/bin
export PATH
```

---

### Post by kanna1620 on 2007-01-13
> **taurus said:**
> Move it to /usr/local/bin (or even ~/bin) and modify your ~/.bashrc to include it in your path.

```
PATH=$PATH:/usr/local/bin:~/bin
export PATH
```

**Thanks.**Its working.

---

