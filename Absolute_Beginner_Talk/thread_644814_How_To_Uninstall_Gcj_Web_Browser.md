---
title: "How To Uninstall Gcj Web Browser???"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by finker282 on 2007-12-19
Can someone please tell me
same problem as [http://ubuntuforums.org/showthread.php?t=630156](http://ubuntuforums.org/showthread.php?t=630156)
:'(.

---

### Post by odiseo77 on 2007-12-19
So, I guess you want to install the java plugin? If this is the case, try this:

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

After the installation is complete, execute:

```
sudo update-alternatives --config java
```

At the prompt menu, select the number for Java 1.6 and press enter. That should do it.

---

### Post by finker282 on 2007-12-19
I installed java 2 days ago...

It says its using java but I'm still uncertain.
I am pretty sure firefox is using the other plugin :\

---

### Post by odiseo77 on 2007-12-19
hmm, could you post the output of the following command?:

```
java -version
```

---

### Post by Marco Ceppi on 2008-01-02
I had a similar issue. What I did was search the Filesystem for

libgcjwebplugin.so


There are about 5 instances of links and one file in "/usr/lib/classpath/libgcjwebplugin.so" after deleting the file and all other associations to it I was able to restart firefox and load Java Applets using the proper Java 6.0 Runtime.


Marco

---

