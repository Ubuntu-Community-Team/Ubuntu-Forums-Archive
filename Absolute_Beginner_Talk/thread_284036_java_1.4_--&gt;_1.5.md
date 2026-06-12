---
title: "java 1.4 --&gt; 1.5"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by nitro_n2o on 2006-10-25
Hi all, 
I've just installed ubuntu.. it's really amaaaaaazing. I installed eclipse with sun jre's (1.5) but ubuntu comes in with java 1.4... how can i uninstall the java 1.4 without messing up the 1.5 
Thx,

---

### Post by Perfect Storm on 2006-10-25
With this command you can choose which version of java you want to use on your system:
```
sudo update-alternatives --config java
```


To uninstall Java1.4:
```
sudo aptitude remove j2re1.4
```

---

### Post by nitro_n2o on 2006-10-25
thx a lot that worked just perfect 
But how to setup the path to run the javac command, i can run java but not javac

Thx again

---

