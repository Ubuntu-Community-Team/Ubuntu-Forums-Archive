---
title: "How to manually upgrade amaroK?"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by mrvgarg on 2006-06-11
I have amaroK installed but it is an old version. How can I manually upgrade it to the latest version?

---

### Post by Aurelias on 2006-06-11
The easiest way is to use the kubuntu amarok packages.
[http://kubuntu.org/announcements/amarok-1.4.php](http://kubuntu.org/announcements/amarok-1.4.php)
Details exactly what you need to do.
-Aurelias

---

### Post by JanVH on 2006-06-11
If the new amaroK-version is already in the Ubuntu-packages

```
sudo apt-get upgrade
```

doesn't only upgrade amaroK, but also every other package installed.

---

### Post by Jucato on 2006-06-11
Use the repository from the page linked by Aurelias.
And enable the universe repository because some dependencies of the amarok engines are found there, so you won't be able to upgrade if you don't enable them.

@JanVH: the latest amarok version is not included in the main Ubuntu repositories. A special Kubuntu repository was made for it.

---

