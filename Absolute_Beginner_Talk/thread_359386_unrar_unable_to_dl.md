---
title: "unrar unable to dl"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by aalr1986 on 2007-02-11
code:
sudo apt-get install unrar

I got a message telling me that the package was not found, or missing, or something.
Any ideas?

---

### Post by Maestro23 on 2007-02-11
> **aalr1986 said:**
> code:
sudo apt-get install unrar

I got a message telling me that the package was not found, or missing, or something.
Any ideas?

Enable extra repositories: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by aalr1986 on 2007-02-11
the thing is that i'm using Ubuntu 5.04, and it won't let me save the sources.list file when I do the whole thing
do I have to DL the last version, for this to be done?

---

### Post by seshomaru samma on 2007-02-12
you have to use sudo in order to have permission to change the list
```
sudo gedit /etc/apt/sources.list
```

is ubuntu 5.04 breezy?

---

