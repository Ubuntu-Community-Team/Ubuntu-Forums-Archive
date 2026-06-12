---
title: "Java_home"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by fractalvibes on 2007-05-15
Just downloaded the free-java-sdk via synaptic.  Instructions say to:
After installation of this package you should be able to set JAVA_HOME
environment variable to /usr/lib/fjsdk (and preferably add /usr/lib/fjsdk/bin
at the beginning of your PATH) 

Question  - where might I find the file where this needs to be changed or added?

thanks,

fv

---

### Post by reidms on 2007-05-15
It should be located at /usr/lib/fjsdk

try running this from the command line(ya may needa be root)

```
gedit /usr/lib/fjsdk
```

---

### Post by fractalvibes on 2007-05-15
No, that is the directory I need to point the JAVA_HOME environment variable to....
I just don't know where/what file I need to add or change that environment variable = /usr/lib/fjsdk is located....

fv

---

### Post by fractalvibes on 2007-05-15
Is there somewhere a file where the environment variables are persisted?  I need to set the value of JAVA_HOME so it finds the java compiler, and I only want to do this once.....

fv

---

### Post by jordanmthomas on 2007-05-15
I don't use Ubuntu, so I can't say 100% sure this is how it works in Ubuntu, but in most Linux systems, you can put something like this in /etc/profile
```
export JAVA_HOME=/usr/lib/fjsdk
```

If all else fails, you could put it in your .bash_profile or something

---

