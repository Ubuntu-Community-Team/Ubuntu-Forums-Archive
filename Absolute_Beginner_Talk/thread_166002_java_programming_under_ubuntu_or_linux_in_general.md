---
title: "java programming under ubuntu or linux in general"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by Silver-revo on 2006-04-25
There is nothing like trying to learn a new OS to make you feel like a moron...

I am currently trying to get my laptop setup under linux so that I can start CS classes in the fall. I know that is the default setting of the CS computer labs computers so I figured it would be a good idea to get a head start.

Anyway, I beleave I have SDK 1.4 installed and can compile a program with javac but this is where the problems begin...

> clyde@PortableMAGIK:~/programming/java$ ls
HelloJava.java  semantic.cache  semantic.cache~
clyde@PortableMAGIK:~/programming/java$ javac HelloJava.java
clyde@PortableMAGIK:~/programming/java$ java HelloJava.class
Exception in thread "main" java.lang.NoClassDefFoundError: HelloJava/class
clyde@PortableMAGIK:~/programming/java$

](*,) 

> class HelloJava {
    public static void main (String args[]) {
          System.out.println("Hello Java!");
           }
    }


So this is the extremly simple program I am trying to run based out of my Java book.  I am not quite sure what it is looking for, maybe a library or something..

Any help is more than welcome.:D

---

### Post by siminone on 2006-04-25
Hi Silver-revo, you can run program by typing 

java HelloJava

I don't use Java but by looking at error message, everything looks like its installed.

---

### Post by Silver-revo on 2006-04-25
I tried that that is how it came up with the error message.

---

### Post by gibson on 2006-04-25
[QUOTE=Silver-revo]I tried that that is how it came up with the error message.[/QUOTE]

Siminone was correct, 

you typed 

> java HelloWorld.class

but you omit the .class part.

> java HelloWorld

The "." in java signifies a package.

Hope this helps

---

### Post by Silver-revo on 2006-04-25
ok I tried that also...
Here is what I get now:
> clyde@PortableMAGIK:~/programming/java$ ls
HelloJava.class  HelloJava.java  semantic.cache  semantic.cache~
clyde@PortableMAGIK:~/programming/java$ java HelloJava
Exception in thread "main" java.lang.UnsupportedClassVersionError: HelloJava (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
clyde@PortableMAGIK:~/programming/java$

This seems like it has encured even more issues

---

### Post by gibson on 2006-04-25
The problem you are encountering is you are compiling with a version of the JDK that is newer than the version you are running against.

How did you install the JDK?

I would recommend automatix, or looking around for a tutorial to set it up properly as i think you have the JDK that is compiling, but the JRE installed with ubuntu is trying to run it.

or alternativley this is what i did - [http://www.jroller.com/page/triplem74?entry=install_java_jdk_1_5](http://www.jroller.com/page/triplem74?entry=install_java_jdk_1_5)


If you want to double check this is the problem then do

> java -version

then 

> javac -target 1.4[or whatever your version is] HelloJava.java

all in all, you are on the right track on how to run java files

let me know how you get along

---

### Post by Silver-revo on 2006-04-25
Ok guys you are right I do have 2 conflicting versions of java javac.
So maybe the easiest thing to do would be to uninstall all of java sdk jre everything and then start over with jdk jre 1.5?

If that is the case how do you unistall java I used automatix to isntall 1.5 jre and jdk should I unistall that also?

---

### Post by Jagot on 2006-04-26
[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Java#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Java#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

You can have a look at the link above to install 1.5.

---

### Post by index_0@ya.com on 2006-04-26
A suggestion ,

try the following comand to get the current path of javac 
$which javac 

try the following comand to get the current path of java
$which java

make sure two paths are pointing from same folder 
if not,

1. make a copy of existing java shortcut
cp <existingpath>/java  <existingpath>/java_old
rm -rf <existingpath>/java

2. Now, make a new shortcut for new java file
ln -s <newpath>/java <existingpath>/java 

obviously, replace "<existing path>" with path obtained from which command
and the "<new path>"  with new required java version path


hope it might help ,
cheers ,

---

### Post by steve.horsley on 2006-04-26
I think you'll find that **which java** tells you that you will use /usr/bin/java.  But this is a symlink to /etc/alternatives/java. The alternatives directory's sole function is to choose which of several alternative program versions should be used.  /etc/alternatives/java probably points to the default installation java version. I suggest you delete this symlink (or rename it to java.original) and create a new symlink to the java you want like this:
```
sudo ln -s /opt/jdk1.5.0_05/jre/bin/java /etc/alternatives/java
```

---

### Post by Nequeo on 2006-04-26
Hey there. Everyone has given you lots of great advice... But I can see you've been given about three different ways do to things. Hands-down easiest way to get Java working under Ubuntu is to follow the instructions on the link that Jagot posted. 

Make sure you follow all the way to the bottom of the page, where it shows you the 'update-alteratives' command. I.e. 

"sudo update-alternatives --config java"

That will update all the symlinks automatically for you.

P.s. I, too, am currently taking a post-grad CS course in Java. At home I work using Sun JDK and Vim under Ubuntu. For Uni I remastered a DSL Cd to include the Sun FDK, vim, and my .vimrc from Ubuntu. Works a treat, and beats having to lug a laptop around or use 'JCreator' on the Windows lab PCs. Sure, they have an X-server installed on the Windows machines, which can get us a Gnome or KDE session ona crusty old version of Red-Hat. But it chugs like anything, because of network latency and all the kids using it. DSL just flies.

---

