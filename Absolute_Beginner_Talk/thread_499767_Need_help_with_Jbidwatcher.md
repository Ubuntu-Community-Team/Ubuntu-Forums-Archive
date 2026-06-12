---
title: "Need help with Jbidwatcher"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by vwbeamer on 2007-07-13
[http://www.jbidwatcher.com/](http://www.jbidwatcher.com/)

I can't get this to work, when i paste the instructions in the terminal, I get

james2@james2-laptop:~$ java -Xmx512m -jar JBidWatcher-1.0.1.jar
Unable to access jarfile JBidWatcher-1.0.1.jar

james2@james2-laptop:~$ sudo java -Xmx512m -jar JBidWatcher-1.0.1.jar
Unable to access jarfile JBidWatcher-1.0.1.jar

---

### Post by fishpie on 2007-07-13
Hi,

When you downloaded the jar file did you save it to the Desktop directory? If so the command you need is ```
java -Xmx512m -jar Desktop/JBidWatcher-1.0.1.jar
``` If libgcj7-awt is not installed you will need to install it before using jbidwatcher. You can do this using synaptic, or from the command line with ```
apt-get install libgcj7-awt
```

---

