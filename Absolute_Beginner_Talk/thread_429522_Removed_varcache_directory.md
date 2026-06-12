---
title: "Removed /var/cache directory"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by netsoul on 2007-05-01
Hello friends!

I have occasionally removed the whole directory /var/cache :confused: I manually created the /var/cache/apt directory, but when I try to install or upgrade software I got this error message:

E: Could not open lock file /var/cache/apt/archives/lock - open (2 No such file or directory)
E: Unable to lock the download directory

Could you help me t fix that?

Thanks.

---

### Post by Cypher on 2007-05-01
You are doing
```

sudo apt-get <command> <package>

```
If not, add the "sudo", also it's better to use APT to clear it's own cache as opposed to destructively removing it's directory..

---

### Post by taurus on 2007-05-01
You shouldn't remove that directory by hand.  Try

```
sudo mkdir /var/cache/apt/archives
sudo mkdir /var/cache/apt/archives/lock
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by netsoul on 2007-05-02
Thank you, that helped.

---

### Post by jaywee on 2007-05-03
hmm,great!! It really works!!

---

