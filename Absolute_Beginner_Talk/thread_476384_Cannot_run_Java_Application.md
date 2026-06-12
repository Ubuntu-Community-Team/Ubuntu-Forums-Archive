---
title: "Cannot run Java Application"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by ahlandberg on 2007-06-17
This is my java program, test.java :
[B]
public class test
{
   public static void main(String[] args)
   { System.out.println("Hello world!"); }
}[/B]

The program compiles:
[B]
ahlandberg@ubuntu610:~$ javac test.java
ahlandberg@ubuntu610:~$ chmod +x test.class[/B]

But when I run it, I get this weird exception:
[B]
ahlandberg@ubuntu610:~$ java test
Exception in thread "main" java.lang.NoClassDefFoundError: test
   at gnu.java.lang.MainThread.run(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: test not found in gnu.gcj.runtime.SystemClassLoader{urls=[], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)[/B]

Can someone please tell me what's wrong here?

Thanks in advance!

Anders

---

### Post by Golyadkin on 2007-06-17
Don't you need to add the local directory to the path Java uses to find classes? It had something to do with an -I flag. 

Java is too long ago for me to remember though.  I do remember classnames had to be capitalize: "Test"

---

### Post by proalan on 2007-06-17
program is fine, just need to set classpaths so the jvm / linux knows where the java system classes (the errors in your report) are located in your directory structure

Classnames don't have to be capitalise, its just common software engineering practice

---

### Post by ahlandberg on 2007-06-17
Please have a look at my env vars, maybe there is sth wrong:

#/etc/environment

CLASSPATH=.:/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin
JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.11
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:
/usr/games"
LANG="en_AU.UTF-8"


It looks all fine to me!!

---

### Post by ahlandberg on 2007-06-17
#~/.bashrc

export CLASSPATH=.:/usr/share/tomcat6/lib/jsp-api.jar:/usr/share/tomcat6/lib/servlet-api.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin:/usr/lib/jvm/java-1.5.0-
sun-1.5.0.11/jre/lib:$CLASSPATH

---

### Post by proalan on 2007-06-17
the program compiles so I'm thinking your missing runtime library perhaps? 

try this if you haven't already done so

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_JRE_v6.0](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_JRE_v6.0)

don't worry about the version mismatch.

---

### Post by steve.horsley on 2007-06-17
I would suggest you get rid of CLASSPATH altogether. You don't need it.
> 

steve@StevesPC:~$ cat test.java
public class test
{
    public static void main(String[] args)
    {     
        System.out.println("Hello world!"); 
    }
}

steve@StevesPC:~$ javac test.java
steve@StevesPC:~$ echo $CLASSPATH

steve@StevesPC:~$ java test
Hello world!
steve@StevesPC:~$ 

---

### Post by ahlandberg on 2007-06-17
Thanks for that! It fixed my problem!!

---

