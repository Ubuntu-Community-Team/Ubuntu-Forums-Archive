---
title: "a couple questions from a linux noob"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by bigb0i on 2007-11-13
what command would i use to bring my system up to date?
what is the simplest revision control system in common use?
what is the difference between CVN and SVN?

thanks~

---

### Post by shad0w_walker on 2007-11-13
This thread is almost a certain target of the spammer. Do not run any rm based commands. It will wreck your system.

Check out the top sticky.

---

### Post by bapoumba on 2007-11-13
Please read my sig, last line.

---

### Post by aysiu on 2007-11-13
In answer to your first question, I would use ```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by mcduck on 2007-11-13
The update manager will notify you automatically when there are updates available.

But if you really wish to do it from command line, 'sudo apt-get update' will check all available updates, and after that run 'sudo apt-get upgrade' to install all possible updates

---

