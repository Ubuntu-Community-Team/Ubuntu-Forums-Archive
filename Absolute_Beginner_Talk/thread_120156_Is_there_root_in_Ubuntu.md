---
title: "Is there root in Ubuntu?"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by earwig on 2006-01-20
I am a noob to linux... I just installed Ubuntu and I don't think it ever asked me to provide a root password... is there a root password?  a default password maybe?

---

### Post by 23meg on 2006-01-20
Not by default.

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by gravediggers on 2006-01-20
Hi,

The default installation has root locked, and all root or su tasks are performed under your user account as sudo.

ie, at the command line type
sudo whatevevercommand

---

### Post by Crazy Man on 2006-01-20
enter the command
```
sudo passwd root
```

Then enter what you want as the root password

Now you can su to root like in most other distros. :D

---

### Post by gravediggers on 2006-01-20
and i forgot to say, you can unlock root (I have) but its not recommended.
Check the following wiki to find out more  
 [RootSudo]("https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29")

---

### Post by aysiu on 2006-01-20
Read the third link of my signature for easy ways to accomplish root-like tasks without logging in as root.

---

