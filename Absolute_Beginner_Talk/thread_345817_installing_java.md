---
title: "installing java"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Blaster95 on 2007-01-24
How do you install java on linux?

---

### Post by pesach on 2007-01-24
I think I got the same prob as you go t[http://www.ubuntuforums.org/showthread.php?t=318649]("http://www.ubuntuforums.org/showthread.php?t=318649")

---

### Post by bruenig on 2007-01-24
Make sure you have the multiverse repository enabled.

sudo apt-get install sun-java5-jre - use that for the jre
sudo apt-get install sun-java5-jdk - use that for the jdk
sudo apt-get install sun-java5-plugin - use that for the plugin

If you don't know how to enable the multiverse repo, do
```
cat /etc/apt/sources.list
```
and paste the output in here so I or someone else can tell you what you should do to enable it.

---

### Post by Blaster95 on 2007-01-26
thanks guys i'll try that out later

---

### Post by phossal on 2007-01-29
My sig contains a link to a tutorial for pulling down the latest Java from Sun. It's not the only way, but it's a fairly *easy* way, and it beats having to wait for packages.

---

