---
title: "JAVA, Just installed some NEw Updates and JAVA Quit"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by hobo on 2007-04-13
I just installed some new update to the OS and now JAVA has quit working on NOAA and I assume POGO. Whats up? I think I was running 2.0 something JAVA. How do I get it back?

---

### Post by taurus on 2007-04-13
I thought the latest version is 1.6!  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
java -version
```

---

### Post by hobo on 2007-04-13
hobo@hobo-desktop:~$ java -version
bash: java: command not found
hobo@hobo-desktop:~$ sudo java -version
Password:
sudo: java: command not found
hobo@hobo-desktop:~$



Look like whatever I did Java is gone?????

---

### Post by taurus on 2007-04-13
Try running this command from a terminal.

```
locate java
-or-
sudo find / -name java -print
```
If you don't get anything back, then you probably need to reinstall java again.

---

### Post by hobo on 2007-04-13
hobo@hobo-desktop:~$ sudo find / -name java -print
Password:
/var/lib/dpkg/alternatives/java
/etc/alternatives/java
/etc/java
/home/hobo/vr11/java

/usr/bin/java
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/bin/java
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/bin/java
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin/java
/usr/lib/jvm/java-6-sun-1.6.0.00/bin/java
/usr/lib/openoffice/share/Scripts/java
/usr/share/java

---

### Post by taurus on 2007-04-13
What happens when you run this from a terminal?

```
/usr/bin/java -version
```

---

### Post by hobo on 2007-04-13
hobo@hobo-desktop:~$ /usr/bin/java -version
bash: /usr/bin/java: No such file or directory
hobo@hobo-desktop:~$


I just tried the NOAA Site and seems to work? I am not sure what is going on. And we just went to POGO and all seems to work.  I have no idea why I received some bogus JAVA messages. All seems to be OK!

---

### Post by taurus on 2007-04-13
What's the output of this command?

```
ls -la /usr/bin/java
```

---

### Post by hobo on 2007-04-13
hobo@hobo-desktop:~$ ls -la /usr/bin/java
lrwxrwxrwx 1 root root 22 2007-01-29 02:56 /usr/bin/java -> /etc/alternatives/java
h

---

### Post by taurus on 2007-04-13
How about

```
/usr/lib/jvm/java-6-sun-1.6.0.00/bin/java -version
```

---

### Post by Martin Paulo on 2007-04-20
You can set the default version of Java that the system is to use by entering the following at a command prompt:
 sudo update-alternatives --config java
Select the version that you want to use.

---

