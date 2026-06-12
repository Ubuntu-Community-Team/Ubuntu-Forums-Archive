---
title: "JRE and JDK 6.0"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by jvc26 on 2006-12-17
Hi there, am looking to install JRE and JDK 6.0 on my ubuntu box (AMD64)

I ran through
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_JRE_v5.0_Update_10](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_JRE_v5.0_Update_10)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0)
The first link's instructions failed with:
```

sudo apt-get install java-package

```
The second link's instructions failed with:
```

sudo apt-get install sun-java5-jdk

```
So since both of these were java5 JRE and JDK I decided to try out JRE and JDK 6 so went to:
[https://sdlc5d.sun.com/ECom/EComActionServlet;jsessionid=9254320FF871084B5F93C46CEA130821](https://sdlc5d.sun.com/ECom/EComActionServlet;jsessionid=9254320FF871084B5F93C46CEA130821)

And downloaded the Linux x64 Platform - Java(TM) SE Development Kit 6 self extracting file, giving me a file named jdk-6-linux-amd64.bin on my desktop.

I then right clicked, made executable, chose 'run in terminal', accepted the license agreement, at which point it ran through the install and it has installed it to /home/james/jdk1.6.0

That seems all well and good. The two issues I have are:
1/ How do I add the javac etc. to my paths so that I can just type $ javac x.java into my terminal in the right directory to compile a script.
2/ How can I be sure that the JRE (also installed by the same package) to /home/james/jdk1.6.0/jre is the one used by my system.

Thanks,
Il

---

### Post by scoon on 2006-12-17
Hey there, 

I used this: 
[http://www.ubuntuforums.org/showpost.php?p=1877195&postcount=15]("http://www.ubuntuforums.org/showpost.php?p=1877195&postcount=15")


-scoon

---

