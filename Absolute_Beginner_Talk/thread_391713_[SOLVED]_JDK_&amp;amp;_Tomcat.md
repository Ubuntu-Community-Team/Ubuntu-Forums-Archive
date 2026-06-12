---
title: "[SOLVED] JDK &amp;amp; Tomcat"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by DaveyG on 2007-03-23
Ok, i downloaded and installed Java Development Kit, then installed Tomcat 5 but got errors. so im at the momment editing etc/default/tomcat5.5 and need to change "#JAVA_HOME=/usr/lib/j2sdk1.4-sun" to were JDK is installed to, but iv got no clue as to were it could be, does anyone know? any help would be much appreciated.

Thanks, Davey

---

### Post by DaveyG on 2007-03-23
Bump

---

### Post by compmodder26 on 2007-03-23
Try searching in the folder /usr/lib/jvm.  I have the sun jdk installed on my Dapper server and JAVA_HOME is pointing to /usr/lib/jvm/java-1.5.0-sun

---

### Post by DaveyG on 2007-03-23
Thanks for your help but /usr/lib/jvm/ doesnt seem to exist.. il do a re-install and see if i can catch were its gone to..

---

### Post by DaveyG on 2007-03-23
iv finaly found it.. im so dumb.. i looked in /home/davey/ and there sat a folder named jdk1.5.0_11.. all fixed :)  thanks for your help

---

### Post by aktiwers on 2007-04-18
Where do you set your JAVA_HOME?
I tried in  ~/.bashrc but it still doenst work?
Im also using  /usr/lib/jvm/java-1.5.0-sun

??

---

