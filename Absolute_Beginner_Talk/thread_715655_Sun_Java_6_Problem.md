---
title: "Sun Java 6 Problem"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by mikkko on 2008-03-05
i cant seem to run out of questions and problems.. ^_^

anyways, i tried installing eclipse but it required me to install JRE first..

i followed everything here: [http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/)

everything was cool up until i got to this part: 
> You also need to edit a file called /etc/jvm. This file defines the default system JVM search order. Each JVM should list their JAVA_HOME compatible directory in this file. The default system JVM is the first one available from top to bottom. Open /etc/jvm
```
$ sudo vi /etc/jvm
```

i cant seem to edit the jvm.. 

can anyone help me? ^_^ thanks.. coz i need to install eclipse.. im already experienceing problems and i havent installed eclipse yet.. :(

---

### Post by zvacet on 2008-03-05
```
sudo gedit /etc/jvm
```

---

### Post by glotz on 2008-03-07
[QUOTE=zvacet]```
sudo gedit /etc/jvm
```[/QUOTE]
No no no no! Use sudo for command line interface programs and gksudo for graphical applications.

So you either
sudo nano /etc/jvm or
gksudo gedit /etc/jvm

See [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

