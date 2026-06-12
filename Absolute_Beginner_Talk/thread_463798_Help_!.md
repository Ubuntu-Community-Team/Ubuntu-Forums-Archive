---
title: "Help !"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by anuraggautam on 2007-06-04
Will Any one tell me how to download this jdbc drivers........

the Error is coming like that 

```

com.mysql.jdbc.Driver
Exception in thread "main" java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at DBDemo.main(DBDemo.java:27)


```

I tried all steps which has been posted in this thread```
   http://ubuntuforums.org/showthread.php?t=122771&highlight=jdbc+HOWTO  
```

but still its not working

Regards!

---

### Post by jvictor on 2007-06-04
First of all it'd be more helpful to know what you are trying to do .. 

I'd suggest that you just download the jar file from 

[http://dev.mysql.com/downloads/connector/j/5.0.html](http://dev.mysql.com/downloads/connector/j/5.0.html)

If its a web-app then drop it into WEB-INF/lib and if not Just add the jar to the CLASSPATH.

hth

---

### Post by anuraggautam on 2007-06-04
i am trying to write a program for scraping and i want to store all data in the mysql database....

now i am installing the connector which you have provided up.....
so is any more do you know.......or will you want to post me the code which i jave written...in java.

---

### Post by anuraggautam on 2007-06-04
please help frndz.....

---

### Post by jvictor on 2007-06-04
I hope you are not new to Java too.. 

**java.lang.ClassNotFoundException** this happens when a class is not found , which translates to the fact that the mysql jar file cannot be located by the VM in the classpath.

First download the Jar file and put in some directory you would want to for eg: /home/<ur user>/jars

next, open a shell and be sure that you are in ur home directory 

then type 

nano .bashrc

and then add the lines

CLASSPATH=$CLASSPATH:<path to your jar dir>
export CLASSPATH

type ^O ^X to save and exit

(replace stuff in <..> with actual location)

re open a shell 

and run your program

---

### Post by anuraggautam on 2007-06-04
can you tell me where to add ...i mean after which line should i add this comment....

CLASSPATH=$CLASSPATH:</usr/share/java/mysql.jar>
export CLASSPATH

..i added that lines but when i am reopening the shell its coming like

bash: /home/anurag/.bashrc: line 68: syntax error near unexpected token `newline'
bash: /home/anurag/.bashrc: line 68: `CLASSPATH=$CLASSPATH:</usr/share/java/mysql.jar>'


so suggest me where to add those lines...

and about java that problem belongs to mysql...not from the class ...... ;)

---

### Post by jvictor on 2007-06-04
The actual problem is the angled brackets.

replace </usr/share/java/mysql.jar> with /usr/share/java/mysql.jar

You can add it to the end of the file

locate the lines that look like

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

....add your stuff here..

---

### Post by bedjo on 2007-07-11
if you are using netbeans IDE, try this 

[http://www.netbeans.org/kb/41/using-netbeans/project_setup.html#manageclasspath](http://www.netbeans.org/kb/41/using-netbeans/project_setup.html#manageclasspath)

it make me smile :)

---

