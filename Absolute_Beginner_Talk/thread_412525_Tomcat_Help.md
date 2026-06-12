---
title: "Tomcat Help"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2007-04-18
Hi im desperately trying to get Tomcat to work, but I really cant.

On edgy this took me about 15 mins to install and all was working, but now on Feisty it just wont work. I hope someone can help.

I installed Tomcat5.5 with apt-get.
Then I set my JAVA_HOME to /usr/lib/jvm/java-1.5.0-sun

I then run the startup script.
```
aktiwers@HAL:~$ sudo /etc/init.d/tomcat5.5 start
 * Starting Tomcat servlet engine tomcat5.5                                        [ OK ] 
aktiwers@HAL:~$ 
```

Okay, everything seams fine.. but when visiting 
localhost
localhost:8080
localhost8180
in firefox it doesnt display the usual Tomcat page.. I just get the "Page can not be found". :(

So I go to look in server.xml to see the port it is set too, and it its on 8180. So I guess Localhost:8180 should work.

Then I run some trouble-shooting commands, but I dont really get the output of them?

> aktiwers@HAL:~$ ps -aux | grep tomcat
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
root      8247  0.0  0.0   1980   312 ?        Ss   12:32   0:00 jsvc.exec -user tomcat55 -cp /usr/share/java/commons-daemon.jar:/usr/share/tomcat5.5/bin/bootstrap.jar -outfile /var/lib/tomcat5.5/logs/catalina.out -errfile &1 -pidfile /var/run/tomcat5.5.pid -Djava.awt.headless=true -Xmx128M -Djava.endorsed.dirs=/usr/share/tomcat5.5/common/endorsed -Dcatalina.base=/var/lib/tomcat5.5 -Dcatalina.home=/usr/share/tomcat5.5 -Djava.io.tmpdir=/var/lib/tomcat5.5/temp -Djava.security.manager -Djava.security.policy=/var/lib/tomcat5.5/conf/catalina.policy -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.util.logging.config.file=/var/lib/tomcat5.5/conf/logging.properties org.apache.catalina.startup.Bootstrap
root      8281  0.0  0.0   1984   312 ?        Ss   12:32   0:00 jsvc.exec -user tomcat55 -cp /usr/share/java/commons-daemon.jar:/usr/share/tomcat5.5/bin/bootstrap.jar -outfile /var/lib/tomcat5.5/logs/catalina.out -errfile &1 -pidfile /var/run/tomcat5.5.pid -Djava.awt.headless=true -Xmx128M -Djava.endorsed.dirs=/usr/share/tomcat5.5/common/endorsed -Dcatalina.base=/var/lib/tomcat5.5 -Dcatalina.home=/usr/share/tomcat5.5 -Djava.io.tmpdir=/var/lib/tomcat5.5/temp -Djava.security.manager -Djava.security.policy=/var/lib/tomcat5.5/conf/catalina.policy -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.util.logging.config.file=/var/lib/tomcat5.5/conf/logging.properties org.apache.catalina.startup.Bootstrap
root      8697  0.0  0.0   1980   308 ?        Ss   12:42   0:00 jsvc.exec -user tomcat55 -cp /usr/share/java/commons-daemon.jar:/usr/share/tomcat5.5/bin/bootstrap.jar -outfile /var/lib/tomcat5.5/logs/catalina.out -errfile &1 -pidfile /var/run/tomcat5.5.pid -Djava.awt.headless=true -Xmx128M -Djava.endorsed.dirs=/usr/share/tomcat5.5/common/endorsed -Dcatalina.base=/var/lib/tomcat5.5 -Dcatalina.home=/usr/share/tomcat5.5 -Djava.io.tmpdir=/var/lib/tomcat5.5/temp -Djava.security.manager -Djava.security.policy=/var/lib/tomcat5.5/conf/catalina.policy -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.util.logging.config.file=/var/lib/tomcat5.5/conf/logging.properties org.apache.catalina.startup.Bootstrap
root      8885  0.0  0.0   1980   308 ?        Ss   12:44   0:00 jsvc.exec -user tomcat55 -cp /usr/share/java/commons-daemon.jar:/usr/share/tomcat5.5/bin/bootstrap.jar -outfile /var/lib/tomcat5.5/logs/catalina.out -errfile &1 -pidfile /var/run/tomcat5.5.pid -Djava.awt.headless=true -Xmx128M -Djava.endorsed.dirs=/usr/share/tomcat5.5/common/endorsed -Dcatalina.base=/var/lib/tomcat5.5 -Dcatalina.home=/usr/share/tomcat5.5 -Djava.io.tmpdir=/var/lib/tomcat5.5/temp -Djava.security.manager -Djava.security.policy=/var/lib/tomcat5.5/conf/catalina.policy -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.util.logging.config.file=/var/lib/tomcat5.5/conf/logging.properties org.apache.catalina.startup.Bootstrap
aktiwers  9097  0.2  1.7  58972 17676 ?        S    12:49   0:01 gedit file:///etc/tomcat5.5/server.xml
root      9230  0.0  0.0   1984   312 ?        Ss   12:51   0:00 jsvc.exec -user tomcat55 -cp /usr/share/java/commons-daemon.jar:/usr/share/tomcat5.5/bin/bootstrap.jar -outfile /var/lib/tomcat5.5/logs/catalina.out -errfile &1 -pidfile /var/run/tomcat5.5.pid -Djava.awt.headless=true -Xmx128M -Djava.endorsed.dirs=/usr/share/tomcat5.5/common/endorsed -Dcatalina.base=/var/lib/tomcat5.5 -Dcatalina.home=/usr/share/tomcat5.5 -Djava.io.tmpdir=/var/lib/tomcat5.5/temp -Djava.security.manager -Djava.security.policy=/var/lib/tomcat5.5/conf/catalina.policy -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.util.logging.config.file=/var/lib/tomcat5.5/conf/logging.properties org.apache.catalina.startup.Bootstrap
root      9450  0.0  0.0   1984   312 ?        Ss   12:56   0:00 jsvc.exec -user tomcat55 -cp /usr/share/java/commons-daemon.jar:/usr/share/tomcat5.5/bin/bootstrap.jar -outfile /var/lib/tomcat5.5/logs/catalina.out -errfile &1 -pidfile /var/run/tomcat5.5.pid -Djava.awt.headless=true -Xmx128M -Djava.endorsed.dirs=/usr/share/tomcat5.5/common/endorsed -Dcatalina.base=/var/lib/tomcat5.5 -Dcatalina.home=/usr/share/tomcat5.5 -Djava.io.tmpdir=/var/lib/tomcat5.5/temp -Djava.security.manager -Djava.security.policy=/var/lib/tomcat5.5/conf/catalina.policy -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.util.logging.config.file=/var/lib/tomcat5.5/conf/logging.properties org.apache.catalina.startup.Bootstrap
aktiwers  9531  0.0  0.0   2880   752 pts/2    R+   12:59   0:00 grep tomcat
aktiwers@HAL:~$ 


and there is no sign of tomcat in netstat either?! 

Can anyone see whats wrong here? I really need this working for a schoolprojekt.
Thanks a lot!

---

### Post by aktiwers on 2007-04-18
Bump

---

### Post by aktiwers on 2007-04-18
No one?

---

### Post by aktiwers on 2007-04-18
My last try..  really no one? :(

---

### Post by jrourke on 2007-04-20
I am having the same problem.  I am going to try and completely remove java, some java-related libraries, and tomcat, and re-install.

---

### Post by aktiwers on 2007-04-20
Okay cool.. Let me know how it went :)
Strange thing is this was an easy install on Edgy.. only  feisty is giving me this problem.

I have tried removing everything and doing a clean install of Tomcat and Java, but without luck. It looks like its running fine, but it isnt :(

Let me know. Thanks

---

### Post by jyrinx on 2007-04-20
See bug [#97096]("https://bugs.launchpad.net/ubuntu/+source/tomcat5.5/+bug/97096") in Launchpad for a workaround.

---

### Post by aktiwers on 2007-04-20
Thanks.. im going to try this tomorrow.

---

### Post by jrourke on 2007-04-23
In the meantime I was using the java command directly, sudo /usr/lib/jvm/java-1.5.0-sun/jre/bin/java...org.apache.catalina.startup.Bootstrap start 

I just tried the bug #97096 in Launchpad for a workaround, and it works now.  Thanks!

---

### Post by jrourke on 2007-04-23
After trying a few times, I am getting intermittent issues with the workaround, like logging not working or classes not being found.  I am going to start tomcat5.5 without jsvc until this becomes more stable by using sudo /usr/lib/jvm/java-1.5.0-sun/jre/bin/java  with all the -D options

sudo /usr/lib/jvm/java-1.5.0-sun/jre/bin/java -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.util.logging.config.file=/var/lib/tomcat5.5/c
onf/logging.properties -Djava.endorsed.dirs=/usr/share/tomcat5.5//common/endorsed -classpath /usr/share/tomcat5.5/server/lib/:/usr/share/tomcat5.5/server/lib:/usr/li
b/jvm/java-1.5.0-sun-1.5.0.11/lib/tools.jar:/usr/share/tomcat5.5/bin/bootstrap.jar:/usr/share/tomcat5.5//bin/commons-logging-api.jar -Dcatalina.base=/var/lib/tomcat
5.5/ -Dcatalina.home=/usr/share/tomcat5.5/ -Djava.io.tmpdir=/var/lib/tomcat5.5/temp/ org.apache.catalina.startup.Bootstrap start

---

### Post by aktiwers on 2007-04-23
I didnt have time to check it yet. I will let you know. It might be a month or so before I need it.

---

