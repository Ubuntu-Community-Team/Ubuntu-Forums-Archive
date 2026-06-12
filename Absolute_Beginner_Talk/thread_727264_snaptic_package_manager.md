---
title: "snaptic package manager"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by La.Cutter1 on 2008-03-17
After several days of trying, I finally got downloads to install.  Then went to the terminal and typed "sudo apt-get updates.

When the updates finished installing, tried to open the synaptic package manager and got a blank page with this error message........

E: dpkg was interrupted. you must manually run 'dpkg--configure-a' to correct the problem.

E_cache->open()failed. please report.  

Tried entering dpkg--configure-a in terminal but received"command not found"

This noob really needs help.

---

### Post by mali2297 on 2008-03-17
Type (or copy/paste):
```

sudo dpkg --configure -a

```
Note the spaces.

---

### Post by La.Cutter1 on 2008-03-17
THANK YOU FOR YOUR PROMPT ANSWER....worked perfectly...
This 66 year old noob has a hell of a lot to learn....

---

### Post by jan quark on 2008-03-17
linux is very case sensitive :)

so every space has its meaning and a capital letter is really a capital letter

see here for basic commands guides:

[LIST]
[*][https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands)
[*][http://blog.lxpages.com/ultimate_linux.html](http://blog.lxpages.com/ultimate_linux.html)
[/LIST]

---

