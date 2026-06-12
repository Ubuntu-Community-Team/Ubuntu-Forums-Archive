---
title: "Changing Terminal Prompt"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by think13 on 2006-10-02
Ok, I want to change the default terminal prompt that turns up when I run the terminal.  I have this book 'Linux for Dummies' that recommends editing /etc/profile, .bash_profile, and .bashrc

I have edited the first two (bashrc looked to complicated to mess around with) and the prompt is the same after logging out and back in.

---

### Post by IYY on 2006-10-02
At the end of .bashrc:

```
PS1='Prompt goes here'
```

For example, the DOS prompt is:

```
PS1='C:\> '
```

---

### Post by think13 on 2006-10-02
Thanks, that worked.

---

