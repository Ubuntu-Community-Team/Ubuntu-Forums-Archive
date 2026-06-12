---
title: "Tutorial on using command lines"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by pedrotheswift on 2007-06-11
Is there a simple tutorial on how to use command lines and where can I get it? I need to install Java Runtime Environment in Ubuntu 7.04 running Firefox. can anyone tell me if there is a Ubuntu -friendly Java RE. And how can I install the files?
Thank you , Pedro.

---

### Post by yabbadabbadont on 2007-06-11
[http://ubuntuforums.org/showthread.php?t=468321](http://ubuntuforums.org/showthread.php?t=468321)

That thread contains some good links to tutorials.

---

### Post by taurus on 2007-06-11
Sun's java is available from the repos.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
java -version
```

---

### Post by moffa on 2007-06-11
You don't really need to use the command line all that much anymore.  A decent beginners tutorial is available here: [http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal).

To install Java, go to Applications > Add/Remove Programs and type in Java.  Make sure you get the plugin as well.

Installing programs is easily accomplished using Synaptic.  You probably have to go to Settings > Repositories and enable all the servers

---

