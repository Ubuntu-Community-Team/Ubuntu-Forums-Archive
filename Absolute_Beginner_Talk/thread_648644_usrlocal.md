---
title: "/usr/local/"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by ffluff on 2007-12-23
$ /usr/local/bin/winecfg

When the wine website says to run this command what do I really type?

---

### Post by wormser on 2007-12-23
You need to type in the whole thing.  Ubuntu and all *nix have a thing called Path.  Standard commands like ls are in your Path so you do not need to type the whole path to where the command is located.  Extra programs are not always in your Path so you have to tell the shell exactly where it is.  So in your case if winecfg does not work you need to type in the whole thing.  If you are in the same folder as the command then you need to put ./ infront to make it run.  Hope that helps.  Google for more info.

```
/usr/local/bin/winecfg
```

---

### Post by jw5801 on 2007-12-23
/usr/local/bin/ is on the default path. So simply typing "winecfg" should produce the same outcome.

---

