---
title: "Noobie removed wrong file"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by 25an on 2006-10-20
Hi!

I tried to install apache2 and tomcat5 but I couldn't get it to work.
But the problem is that I managed to remove the file /etc/default/tomcat5](*,) 
I thought for sure that when I reinstall it would create a new one, but no? ](*,) 
What can I do to get a tomcat5 file in the /etc/default/

Thanks

---

### Post by jordanmthomas on 2006-10-20
```
sudo aptitude purge tomcat5
sudo aptitude install tomcat5
```

Does this work?

---

### Post by bsussman on 2006-10-20
> **jordanmthomas said:**
> ```
sudo aptitude purge tomcat5
sudo aptitude install tomcat5
```Does this work?

Or in synaptic, mark for complete removal, apply, install, apply

---

### Post by 25an on 2006-10-21
What dose these commands do?

sudo aptitude purge tomcat5
sudo aptitude install tomcat5

---

### Post by Quintin Riis on 2006-10-21
> **25an said:**
> What dose these commands do?

sudo aptitude purge tomcat5
sudo aptitude install tomcat5
Consulting the manual pages 'man aptitude' or google will teach you more than you ever want to know.

Purge uninstalls software, but also removes configuration files.

"Install" should be self-explanatory.

---

### Post by 25an on 2006-10-21
Yes I did. Thanks, it helped a lot.

But it doesn't help.
Any ideas how I can remove tomcat5 and the install it again so that I can get the file back?

---

### Post by maaronB on 2006-10-21
I don't know how, but I know there is some way to unpack the .deb files.  If you could figure out how to do that, then you could probably place the file manually.

---

### Post by podunk on 2006-10-21
If going to 
Administration
Synaptic Package Manager
Finding your app and right clicking and &#8220;mark for complete removal&#8221;
Click Apply at the top

doesn't get your app completely removed I don't know what will. You could try
```
sudo updatedb
```
```
locate application_name | less
```

and delete everything one file at a time.

Have you tried  cheating yet? I had something I couldn't get running because some file was misiing and I couldn't find it anywhere.

So I used the terminal and used the cd command to get to the right directory and did
```
sudo touch file_name
```

and it ran fine.

---

### Post by maaronB on 2006-10-21
I don't know if there would be any differences caused by different computers and such.

But here is what mine looks like if you want to try copy/paste.
```

# Run Tomcat 5 as this user ID (default: tomcat5). Set this to an empty string
# to prevent Tomcat from starting.
#TOMCAT5_USER=tomcat5

# The home directory of the Java development kit (JDK). You need at least
# JDK version 1.3, just the Java runtime environment (JRE) will not work
# because a Java compiler is needed to translate JavaServer Pages (JSP).
# If JAVA_HOME is not set, some common directories for the non-free JDKs
# as packaged by the Debian java-package and the directories of
# java-gcj-compat-dev and kaffe are tried.
#
# You can also set JSSE_HOME here to enable SSL support
# (this is automatically done for JDK 1.4+, java-gcj-compat-dev and kaffe).
#JAVA_HOME=/usr/lib/jvm/java-gcj
#JSSE_HOME=/usr/local/jsse

# Directory for per-instance configuration files and webapps. It contain the
# directories conf, logs, webapps, work and temp. See RUNNING.txt for details.
# Default: /var/lib/tomcat5
#CATALINA_BASE=/var/lib/tomcat5

# Arguments to pass to the Java virtual machine (JVM)
# "-Djava.awt.headless=true -Xmx128M" is automatically set if CATALINA_OPTS
# is left empty here
#CATALINA_OPTS="-Djava.awt.headless=true -Xmx128M -server"

# Java compiler to use for translating JavaServer Pages (JSPs). You can use all
# compilers that are accepted by Ant's build.compiler property.
#JSP_COMPILER=jikes

# Use the Java security manager? (yes/no, default: yes)
#TOMCAT5_SECURITY=yes

# Timeout in seconds for the shutdown procedure (default: 30). The Java
# processes will be killed if tomcat5 has not stopped until then.
#TOMCAT5_SHUTDOWN=30

# Number of days to keep old log files in /var/log/tomcat5 (default: 14)
#LOGFILE_DAYS=30

```

---

### Post by Ocxic on 2006-10-21
try "sudo dpkg-reconfigure tomcat5"

---

### Post by 25an on 2006-10-23
I managed to fix i.
I am running KUbuntu so I started adept searched for tomcat5 pushed the 
detail button and then installed files and there I could see that it had not installed everything. So I removed the dir where it should have installed the package. And then I reinstalled it and it worked. 

Thanks for your help.

---

