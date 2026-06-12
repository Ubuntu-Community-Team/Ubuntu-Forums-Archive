---
title: "[SOLVED] removing programs."
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by CapitanYochua on 2007-09-02
How do you remove a program that you installed through a .deb that you found on a site?

---

### Post by Dr Small on 2007-09-02
```
sudo dpkg -r packagename
```

---

### Post by dpar on 2007-09-02
It's probably listed in synaptic too. You can uninstall it that way too if you prefer gui.

---

### Post by csimons on 2007-09-02
From the shell, I believe you can use "dpkg --remove <package_name>" or "dpkg --purge <package_name>" (remove will keep configuration files, purge will remove them).

If you aren't sure about the package name, you can use "dpkg --list <pattern>" to attempt to find the name.

There are some examples on the dpkg manual page ("man dpkg").

---

### Post by CapitanYochua on 2007-09-02
I keep doing those commands with the program name in it. But it says that it isn't installed. but when I type it in another command it starts up.

---

### Post by CapitanYochua on 2007-09-02
What should I dooo?

---

### Post by jordanmthomas on 2007-09-02
```
dpkg -l '*' | grep *genericnameforpackage*
```
where genericnameforpackage is the command you use to run the program, most likely.

Then, ```
sudo dpkg -r *whateverlastcommandgaveyou*
```

---

### Post by CapitanYochua on 2007-09-02
Thanks worked.

---

