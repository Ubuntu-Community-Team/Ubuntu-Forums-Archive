---
title: "APTonCD"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-08-02
where do I get aptoncd?thanx

---

### Post by chewearn on 2007-08-02
Here:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by ushills on 2007-08-02
What's wrong with 

```
sudo apt-get install aptoncd
```

---

### Post by ushills on 2007-08-02
A good alternative is

```
dpkg --get-selections > installed_apps
```

This will write a file with all you installed applications to a file called installed_apps.

To re-install all apps or install on another machine

```
apt-get update
dpkg --set-selections < installed_apps
apt-get -u dselect-upgrade

```

No need to burn them all to CD, you can just donwload the apps that are not currently on the system.

---

