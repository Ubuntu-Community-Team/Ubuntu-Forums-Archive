---
title: "Java enabled browsers"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Obalende on 2007-11-16
Essentially, I would like to find out how I can add java supoprt to my mozilla firefox browser in Ubuntu so I can run a Java applet application. Any ideas?

---

### Post by jaybombalous on 2007-11-16
```
sudo apt-get install sun-java6-jre
sudo apt-get install j2re1.4-mozilla-plugin
```


edit: ... or u could search synaptic and look for yourself.

---

### Post by Obalende on 2007-11-19
Thanks so much.

---

### Post by rsambuca on 2007-11-19
> **jaybombalous said:**
> ```
sudo apt-get install sun-java6-jre
sudo apt-get install j2re1.4-mozilla-plugin
```


edit: ... or u could search synaptic and look for yourself.

That is a really old blackdown java.  Why not the current version?  sun-java6-plugin?  That way you don't have security issues.

---

### Post by jfinkels on 2007-11-19
```
sudo aptitude install sun-java6-plugin
```

---

