---
title: "Aliases not saving"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by uzd4ce on 2006-08-27
I've tried to setup a couple aliases, such as alias zzz="truecrypt -d", and it works for a while, but when I come back from a hibernate or reboot, it doesn't work anymore.

Alias -p shows the aliases before the hibernate, but after it doesn't show them anymore.

Am I doing something wrong?  Do I need to save them somehow?

Thanks,
Uzd4ce

---

### Post by Pragmatist on 2006-08-27
> **uzd4ce said:**
> I've tried to setup a couple aliases, such as alias zzz="truecrypt -d", and it works for a while, but when I come back from a hibernate or reboot, it doesn't work anymore.

Alias -p shows the aliases before the hibernate, but after it doesn't show them anymore.

Am I doing something wrong?  Do I need to save them somehow?

Thanks,
Uzd4ce

Check out your .bashrc file in your home directory (files preceded by a period are hidden and can be listed with **ls -a** )  There is an explanation there about what to do.  Basically, you add them to .bashrc or create a seperate file called .bash_aliases and put them there.  You can read more about aliases by typing
```
man bash
```

---

