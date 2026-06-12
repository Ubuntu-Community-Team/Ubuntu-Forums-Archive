---
title: "automated set up"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by yoopernate on 2007-08-23
I'm trying to set up a script that will download and install ndiswrapper.  I was wondering if there is a command line to download the newest file of ndiswrapper or am i just out of luck on that part.

---

### Post by ddrichardson on 2007-08-24
```
sudo apt-get install ndiswrapper
```

If it's going in a script file i'd leave out the sudo and run the script as sudo.

---

