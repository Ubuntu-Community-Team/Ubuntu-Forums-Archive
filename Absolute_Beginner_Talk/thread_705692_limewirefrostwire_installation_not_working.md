---
title: "limewire/frostwire installation not working"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by xdanxx on 2008-02-23
Hi guys everytime I try to install limewire or frostwire it gets stuck on "Preparing sun-java6-bin" no matter how long I leave it there it doesn't get anywhere. Anyone know why this could be happening, or if there is a way to manually install the java files needed? Thanks alot.

---

### Post by taurus on 2008-02-23
I think it is waiting for you to except the license term for java.  Install it from a terminal with

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```
When you get to the license window, press the Tab key to highlight <OK> and Return to except it.

---

### Post by xdanxx on 2008-02-23
worked great, thanks so much.

---

