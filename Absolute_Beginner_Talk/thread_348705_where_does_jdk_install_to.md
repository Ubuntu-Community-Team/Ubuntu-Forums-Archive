---
title: "where does jdk install to???"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by bcs on 2007-01-29
Hello,
I installed the java sdk a while back, and I was looking around trying to find the directory where it was installed...but I don't see any jdk (or similarly named) directory that has binaries.  I do have a /usr/lib/jvm directory that looks like it probably was installed with jdk...does anyone know where jdk5 installs by default??  Thanks!

---

### Post by hal10000 on 2007-01-29
If you installed sun-java it shout be in a subdirectory of /usr/lib/jvm/java-1.5.0-sun (or whatever java version you unstalled)

---

### Post by bcs on 2007-01-29
OK; thanks a lot!

---

### Post by Ben Sprinkle on 2007-01-29
Any other would be in /opt

---

### Post by bcs on 2007-01-29
Actually, one more quick question.../usr/lib/jvm/java-1.5.0-sub-1.5.0.06 is where my jdk installed to.  When I run the command:
java -version

it says i have version 1.5.0.10...how come the different version? does java version just refer to the jre?  Where in the filesystem do I find that?

---

### Post by jvc26 on 2007-01-29
The java -version command should pop up the JRE version you are running my output looks something like this:
```

java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

```
If you're interested in jdk version you could use:
```

javac -version

```
Which will give the output from the javac which should be the same as your jdk.
Il

---

### Post by bcs on 2007-01-29
OK, thanks.  I have jre's in a number of directories..is it possible to figure out which one the "java -version" is referencing?  For example, is it referencing the firefox plugin, or system-wide jre?

---

### Post by phossal on 2007-01-31
Yes. There is a way. This is how you do it:
```
ls -l $(type -path -all java)
```

If you use this command: java -version, the "answer" you get in response is coming from the first "java" found in your path.  You can view your path this way:
```
echo $PATH
```

Technically, you can use my little command up there to find the source of *any* command. Just change java to something else.
Example: perl
```
ls -l $(type -path -all perl)
```

Put that in your bag of tricks. It's handy. ;)

---

### Post by bcs on 2007-01-31
Hi phossal,  Thanks, but I'm not sure I understand.  I should type command```
ls -l -path -all java
```

??? and then echo the path variable?  Can you explain another way, I don't quite understand what to do :confused:

---

### Post by Unterseeboot_234 on 2007-01-31
Look, there is a lot of confusion about java but what it all boils down to is the path to your /bin file within whatever jdk you have installed. Also, the plug-in so that java applets run within a browser is a separate issue from the Java Development Kit (JDK).

Me? I did a manual install, from a .tar downloaded from Sun and the Java JDK I use is in the top level of my /home folder. If I had used the apt install, the automatic install that Apt/Get offers will put everything inside the /opt. I like having it in my /home so I can have all file permissions. When I have all file permissions I can add libraries and other things conveniently.  That's the thing, it is a Java DEVELOPMENT kit. Whatever java software you finalize is another thing you release as a desktop icon without the JDK.

If you use the NetBeans 5.5 there are no "path missing" issues because NetBeans slams the full path name for every javac, every java, every appletviewer command. You can do the same with a Terminal window. Here is an example. Modify the following in a TextEditor, save into the folder of your current java project folder.

```
#!/bin/sh
JAVA_HOME="/home/vcbrad/jdk1.5.0_10"
PATH=$JAVA_HOME/bin:$PATH
export PATH JAVA_HOME

java -version
java -classpath ./:/home/vcbrad/javaWork_1_5/java_stoffPlan_4/xperiments/stoffPlan_x_Mar01
java StoffPlanDesk


```
(note the classpath line is all one line, and note that each path has a colon ( : ) separator )
save it as **yourJavaClass_run.sh**
close the document
right-click the icon to this document, --> Permissions tab --> tic the Owner as Executable

This will be the equivalent of a .bat file in the Windows world. You just double-click this icon now from within your project. Gnome pops up a option window, click "Run" (not the Run in Terminal). This will teach you all about paths and lets you customize everything on the fly.

It's good and well trying to customize ubuntu default shell but it turns into un-needed work.

Also, I mentioned the plug-in. You see, in 64-bit there is not 64-bit plug-in. Sun leaves it to us to make up our own configuration for the plug-in. Click the following link from these forums. It taught me a lot.

**[Custom Install java]("http://www.ubuntuforums.org/showthread.php?t=319138")**

And, I can't say enough for NetBeans, it's powerful and you can accomplish textbook, pure java with NetBeans.

good luck

---

### Post by hal10000 on 2007-01-31
If you type the command [COLOR="Red"]ls -l $(type -path -all java)[/COLOR]
it shows you the path of all java commands known by the system.
e.g. on my sytem this comand returns:
```

lrwxrwxrwx 1 root root 22 2006-06-17 01:06 /usr/bin/java -> /etc/alternatives/java
lrwxrwxrwx 1 root root 22 2006-06-17 01:06 /usr/bin/X11/java -> /etc/alternatives/java

```
It says, that /usr/bin/java and /usr/bin/X11/java are both symbolic links to /etc/alternatives/java, which in turn is a link to /usr/lib/jvm/java-1.5.0-sun/jre/bin/java:
```

ls -l /etc/alternatives/java
lrwxrwxrwx 1 root root 40 2006-11-10 13:20 /etc/alternatives/java -> /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

```
So, if i type [COLOR="Red"]java /run/a/program [/COLOR] then the java version used is /usr/lib/jvm/java-1.5.0-sun/jre/bin/java.
Now to make it a bit more complicated the /usr/lib/jvm/java-1.5.0-sun/ path itself is also a symbolic link which points to /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/
```

ls -l /usr/lib/jvm/
drwxr-xr-x 5 root root 4096 2006-05-31 02:52 java-1.4.2-gcj-4.1-1.4.2.0
lrwxrwxrwx 1 root root   23 2006-11-10 21:20 java-1.5.0-sun -> java-1.5.0-sun-1.5.0.08
drwxr-xr-x 6 root root 4096 2006-11-10 21:21 java-1.5.0-sun-1.5.0.08
lrwxrwxrwx 1 root root   26 2006-06-17 01:08 java-gcj -> java-1.4.2-gcj-4.1-1.4.2.0

```

If you then do echo $PATH you can see which of these are in your PATH variable. Again, on my sytem the PATH variable looks like:
```

echo $PATH
/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

```
This is a list of paths, separated by colons (:) Only programs (or scripts or any other executable files) which reside in one of these paths can be found by the system.
This means, if you installed your java somewhere e.g. under /opt and this path is not shown in your PATH variable, than it can not be found by the system and if you want to execute this one you cannot simply say [COLOR="Red"]java /run/my/program[/COLOR] because in this case only the java version known by your system is executed (in my case this would be /usr/bin/java, because this is the one known by the system). 
You either have to say
[COLOR="Red"]./opt/path/to/your/jdk-installdir/bin/java /run/my/program[/COLOR]
or you have to include this path to your PATH variable.

---

### Post by bcs on 2007-01-31
Thanks, hal10000!  I missed the "$" in phossal's command (teach me to not cut and paste).  Thanks!

---

### Post by phossal on 2007-01-31
Doh! :( lol

---

