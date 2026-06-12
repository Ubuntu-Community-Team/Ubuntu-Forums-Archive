---
title: "apt-get"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by dmm1983 on 2007-09-27
Does anybody know how to automatically config yes for apt-get 
so i don't get asked yes all the time

---

### Post by kelnage on 2007-09-27
sudo apt-get -y install *package-name*

To find out information like that, always try running: "*program* --help" or "man *program*". These will give you useful information about the program.

---

### Post by akiratheoni on 2007-09-27
IIRC, it's 

sudo apt-get install -y packagename

---

### Post by Dr Small on 2007-09-27
You could try:
```
sudo apt-get install packagename -y
```

Or make an alias to automatically do that, I guess.

---

### Post by llamakc on 2007-09-27
[http://linux.die.net/man/5/apt.conf](http://linux.die.net/man/5/apt.conf)

---

