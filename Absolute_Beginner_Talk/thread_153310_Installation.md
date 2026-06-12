---
title: "Installation"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by eyesoftheworld on 2006-03-31
How do you install and uninstall programs in ubuntu?

---

### Post by christhemonkey on 2006-03-31
you can either go into the synaptic package manager and search for what you want or select add remove applications.  either way is very goood.  Just try it.  (All in the system menu synaptic under administration)

---

### Post by taurus on 2006-03-31
You can use synaptic (GUI) or apt-get (terminal base).  For instance, if you want to install program Z, then open a terminal and type
```

sudo apt-get install Z

```
But if you change your mind and don't want Z anymore, then you can remove it with
```

sudo apt-get remove Z

```
For more info regarding apt-get, run
```

man apt-get

```

---

### Post by eyesoftheworld on 2006-03-31
thanks that helps alot

---

### Post by christhemonkey on 2006-03-31
This topic is very well documented, maybe you should try looking at the wiki, wiki.ubuntu.com

---

