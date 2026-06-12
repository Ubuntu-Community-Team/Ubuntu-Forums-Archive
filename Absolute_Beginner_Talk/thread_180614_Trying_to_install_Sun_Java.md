---
title: "Trying to install Sun Java"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by learning on 2006-05-22
I followed the instructions from the [forums]("http://www.ubuntuforums.org/showthread.php?t=148075&highlight=java")
but it isn't working.

when I run java version, this is my output:

jason@jason-desktop:~$ java version
Exception in thread "main" java.lang.NoClassDefFoundError: version
at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: version not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
at java.net.URLClassLoader.findClass(libgcj.so.7)
at java.lang.ClassLoader.loadClass(libgcj.so.7)
at java.lang.ClassLoader.loadClass(libgcj.so.7)
at java.lang.Class.forName(libgcj.so.7)
at gnu.java.lang.MainThread.run(libgcj.so.7)

Any ideas what I should do?

---

### Post by S{yndrom}e on 2006-05-22
[QUOTE=learning]I followed the instructions from the [forums]("http://www.ubuntuforums.org/showthread.php?t=148075&highlight=java")
but it isn't working.

when I run java version, this is my output:

jason@jason-desktop:~$ java version
Exception in thread "main" java.lang.NoClassDefFoundError: version
at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: version not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
at java.net.URLClassLoader.findClass(libgcj.so.7)
at java.lang.ClassLoader.loadClass(libgcj.so.7)
at java.lang.ClassLoader.loadClass(libgcj.so.7)
at java.lang.Class.forName(libgcj.so.7)
at gnu.java.lang.MainThread.run(libgcj.so.7)

Any ideas what I should do?[/QUOTE]


Try checking this site:

[http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)

Easy instruction really, execute the .bin file by doing 

./name_of_java.bin

Make sure you pick the right java for you

---

### Post by learning on 2006-05-22
As near as I can tell...

I think I have it installed just might not have it properly enabled or configured for firefox.

---

### Post by S{yndrom}e on 2006-05-22
to tell if you have it installed go to system --> Prefrences --> and look for java control panels or sumthing.

I think there is a guide to get it working with firefox ill look it up. Do you have the latest version of firefox?

---

### Post by S{yndrom}e on 2006-05-22
found it. if you have java do this

   1.  Go to the plugins sub-directory under the Mozilla installation directory
      cd <Mozilla installation directory>/plugins
   2. In the current directory, create a symbolic link to the JRE ns7/libjavaplugin_oji.so file Type:
      ln -s <JRE installation directory>/plugin/i386/ns7/libjavaplugin_oji.so

      Example:
          * If Mozilla is installed in this directory:
            /usr/lib/mozilla-1.4/
          * and if the JRE is installed at this directory:
            /usr/java/jre1.5.0
          * Then type at the terminal to go to the browser plug-in directory:
            cd /usr/lib/mozilla-1.4/plugins
          * Enter the following command to create a symbolic link to the Java Plug-in for the Mozilla browser.
            ln -s /usr/java/jre1.5.0/plugin/i386/ns7
            /libjavaplugin_oji.so .
   3. Start Mozilla browser or restart it if it is already running. Note that if you have other Mozilla components (ie: Messenger, Composer, etc) running, you will need to restart them as well.
   4. Go to Edit > Preferences. Under Advanced category > Select Enable Java

---

### Post by learning on 2006-05-22
Have firefox 1.5.0.3

Don't see a java anything under system preferences.  But, from looking at the instructions on java's site, it appears installed because I get:

jason@jason-desktop:/usr/local$ ls
bin    include      jre-1_5_0_06-linux-i586.bin  man   share
games  jre1.5.0_06  lib      

...so it looks like it is there, right?

---

### Post by S{yndrom}e on 2006-05-22
i guess.. you could always try and automated script to install if for you.

---

### Post by _simon_ on 2006-05-22
For dapper, Sun Java is available via Synaptic now.

---

### Post by Sef on 2006-05-22
From the Terminal

type

sudo apt-get update

sudo aptitude install sun-java5-bin

or do you have Kubuntu?

---

### Post by user1397 on 2006-05-22
[quote=Sef]From the Terminal

type

sudo apt-get update

sudo aptitude install sun-java5-bin

or do you have Kubuntu?[/quote]
if he's installing with aptitude, wouldn't it be wiser to first do:
```
sudo aptitude update
```
instead of ```
sudo apt-get update
```
?

---

### Post by learning on 2006-05-22
Have Ubuntu

I ran the first command fine, then when I did install I got this:

jason@jason-desktop:~$ sudo aptitude install sun-java5-bin
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "sun-java5-bin"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by S{yndrom}e on 2006-05-22
AHHH dude. You know how you said java version command doesnt work?

It's java -version

NOT java version

---

### Post by learning on 2006-05-22
O.K.!  I get proper output now!

jason@jason-desktop:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
jason@jason-desktop:~$


Still not working though when I go to verify installation on java website

---

### Post by mlind on 2006-05-22
that's not the Sun's java

if you've installed java using java-package method
(fakeroot make-jpkg some_jre_or_jdk.bin)

then you have to do *sudo update-alternatives --config java*
and choose Sun's jvm.

---

### Post by learning on 2006-05-22
Have to get kids to scouts or I'm in touble...

Here is where I am though:

jason@jason-desktop:~$ sudo update-alternatives -configure java
update-alternatives: unknown argument `-configure'
jason@jason-desktop:~$

I'll have to play with it some more tomorrow.

Thanks for all the help!

---

### Post by mlind on 2006-05-22
[QUOTE=learning]Have to get kids to scouts or I'm in touble...

Here is where I am though:

jason@jason-desktop:~$ sudo update-alternatives -configure java
update-alternatives: unknown argument `-configure'
jason@jason-desktop:~$

I'll have to play with it some more tomorrow.

Thanks for all the help![/QUOTE]

I mistyped that earlier, sorry.

It's sudo update-alternatives **--config** java

---

### Post by user1397 on 2006-05-22
[quote=learning]Have to get kids to scouts or I'm in touble...

Here is where I am though:

jason@jason-desktop:~$ sudo update-alternatives -configure java
update-alternatives: unknown argument `-configure'
jason@jason-desktop:~$

I'll have to play with it some more tomorrow.

Thanks for all the help![/quote] that's because its 
```
sudo update-alternatives --config java 
```

EDIT: mlind, you beat me to it! :)

---

### Post by Sef on 2006-05-22
> /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386 That's the new path instead of the old one.

In restricted formats, it tell you to do this to installl the plugin to firefox:

>   cd ~/.mozilla/plugins

  ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so

  sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/



It needs to be changed to this:

```
cd ~/.mozilla/plugins

ln -s /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/ns7/libjavaplugin_oji.so 

sudo ln -s /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/ns7/libjavaplugin_oji.so/ns7/libjavaplugin_oji.so   /usr/lib/mozilla-firefox/plugins/
```

I did that then I had to install java once again. (sudo aptitude intall sun-java5-bin)

---

### Post by s_h_a_d_o_w_s on 2006-05-22
My FAQ:

[here]("http://www.ubuntuforums.org/showthread.php?t=176442")

It is for getting frostwire, but just read enbling repos and getting JAVA.

---

### Post by user1397 on 2006-05-22
[quote=s_h_a_d_o_w_s]My FAQ:

[here]("http://www.ubuntuforums.org/showthread.php?t=176442")

It is for getting frostwire, but just read enbling repos and getting JAVA.[/quote]
actually, in the part where you say to type the command:
```
echo 3 | sudo update-alternatives --config java

```
that wont do anything.
you have to just do ```
sudo update-alternatives --config java
```,
and choose the this one: /usr/lib/j2re1.5-sun/bin/java

---

