---
title: "HELP for Java/FrostWire"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-03-15
Hi, i need help running Frostwire, i have installed Java 5 but it still wont start. Here is what i tried
[PHP]andreas@Jacobsen:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
andreas@Jacobsen:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java5-jre is already the newest version.
sun-java5-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andreas@Jacobsen:~$ sudo dpkg-reconfigure dash
andreas@Jacobsen:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
andreas@Jacobsen:~$ 
[/PHP]
Anny one know what to do?

---

### Post by overdrank on 2007-03-15
> **ajmannen said:**
> Hi, i need help running Frostwire, i have installed Java 5 but it still wont start. Here is what i tried
[PHP]andreas@Jacobsen:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
andreas@Jacobsen:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java5-jre is already the newest version.
sun-java5-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andreas@Jacobsen:~$ sudo dpkg-reconfigure dash
andreas@Jacobsen:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
andreas@Jacobsen:~$ 
[/PHP]
Anny one know what to do?

Hi if you get automatix it will install the java you need to run frostwire. Good luck!

---

### Post by lamalex on 2007-03-15
go to java's website and upgrade java. they have very good instructions there. automatix will work but automatix can cause more problems than it will solve.

---

### Post by jondecker76 on 2007-03-15
I used automatix with no problems..

Have you looked in synaptic yet?

---

### Post by old_geekster on 2007-03-15
[QUOTE=jondecker76;2302678]I used automatix with no problems../QUOTE]
Me too!:) 

Go to this link:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28xine-ui.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28xine-ui.29)

Scroll down to "How to install Automatix2" and follow the instructions.  I have used Automatix2 to solve several of my newbie problems.

---

