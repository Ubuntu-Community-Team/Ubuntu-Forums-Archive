---
title: "Moneydance and Admin Logon"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by roscoetuff on 2007-06-11
To install Moneydance - a purchased program I've used on Mepis 6.5 Linux - since it isn't in the package manager, it looks like I need access to more than just my home directory. But how to logon as root? The regular login screen says I can't do it there. Hmmm. Now I'm confused. What to do?

Thanks!

---

### Post by WW on 2007-06-11
Rather than login as root, use the **sudo** command.  If, for example, the installer program is called installer.bin, you would use the command
```

$ sudo ./installer.bin

```
in the directory where the file is saved.  You will be asked for *your* password.  (I am assuming that you actually have sudo privileges.)

For more information, check out the [RootSudo wiki page]("https://help.ubuntu.com/community/RootSudo").

---

