---
title: "Java Issues, I think"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by gantww on 2007-09-04
Hello all,
I'm having some weirdness when trying to run java-based apps. Basically, the application terminates during startup, with no error message being displayed. This occurs with JEdit, Eclipse, the Form Wizard in OpenOffice Base, and with Aptana IDE. How can I begin to diagnose this issue? I'm pretty sure I have the java libraries installed. Here's the relevant section of my installer script (I know I could have done this more efficiently, but I was just learning shell scripting when I wrote this):

apt-get install eclipse -y
apt-get install eclipse-cdt -y
apt-get install eclipse-jdt -y
apt-get install eclipse-pydev -y
apt-get install eclipse-rcp -y
apt-get install sun-java5-jdk -y

Any thoughts?

---

### Post by ptillemans on 2007-09-04
Start with the basics : verify if the jvm is correctly installed :

start a terminal  and type** java -version**.

pti@dynip-56-144:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

you see that I have verion 1.6 installed, you're version will be somewhat different.


if you see the following :

pti@dynip-56-144:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


You are running the GNU version, which is currently not yet up to the task to run eclipse, at least I recommend you not to. 

The easiest way to switch between the different alternatives for me is **galternatives**, a GUI client to the alternatives system which allows us to choose different options for the same program.

The commandline alternative (for java at least is **update-java-alternatives**.

pti@dynip-56-144:~$ sudo update-java-alternatives
Password:
usage: update-java-alternatives [--jre] [--plugin] [ -t|--test|-v|--verbose]
           -l|--list [<jname>]
           -s|--set <jname>
           -a|--auto
           -h|-?|--help
pti@dynip-56-144:~$ sudo update-java-alternatives -l
java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-6-sun 63 /usr/lib/jvm/java-6-sun
java-gcj 1041 /usr/lib/jvm/java-gcj
pti@dynip-56-144:~$ sudo update-java-alternatives -s java-6-sun
Using `/usr/lib/jvm/java-6-sun/bin/appletviewer' to provide `appletviewer'.
Using `/usr/lib/jvm/java-6-sun/bin/apt' to provide `apt'.
Using `/usr/lib/jvm/java-6-sun/bin/extcheck' to provide `extcheck'.
Using `/usr/lib/jvm/java-6-sun/bin/HtmlConverter' to provide `HtmlConverter'.
Using `/usr/lib/jvm/java-6-sun/bin/idlj' to provide `idlj'.
Using `/usr/lib/jvm/java-6-sun/bin/jarsigner' to provide `jarsigner'.
Using `/usr/lib/jvm/java-6-sun/bin/jar' to provide `jar'.
Using `/usr/lib/jvm/java-6-sun/bin/javac' to provide `javac'.
Using `/usr/lib/jvm/java-6-sun/bin/javadoc' to provide `javadoc'.
Using `/usr/lib/jvm/java-6-sun/bin/javah' to provide `javah'.
Using `/usr/lib/jvm/java-6-sun/bin/javap' to provide `javap'.
Using `/usr/lib/jvm/java-6-sun/bin/java-rmi.cgi' to provide `java-rmi.cgi'.
Using `/usr/lib/jvm/java-6-sun/bin/jconsole' to provide `jconsole'.
Using `/usr/lib/jvm/java-6-sun/bin/jdb' to provide `jdb'.
Using `/usr/lib/jvm/java-6-sun/bin/jhat' to provide `jhat'.
Using `/usr/lib/jvm/java-6-sun/bin/jinfo' to provide `jinfo'.
Using `/usr/lib/jvm/java-6-sun/bin/jmap' to provide `jmap'.
Using `/usr/lib/jvm/java-6-sun/bin/jps' to provide `jps'.
Using `/usr/lib/jvm/java-6-sun/bin/jrunscript' to provide `jrunscript'.
Using `/usr/lib/jvm/java-6-sun/bin/jsadebugd' to provide `jsadebugd'.
Using `/usr/lib/jvm/java-6-sun/bin/jstack' to provide `jstack'.
Using `/usr/lib/jvm/java-6-sun/bin/jstatd' to provide `jstatd'.
Using `/usr/lib/jvm/java-6-sun/bin/jstat' to provide `jstat'.
Using `/usr/lib/jvm/java-6-sun/bin/native2ascii' to provide `native2ascii'.
Using `/usr/lib/jvm/java-6-sun/bin/rmic' to provide `rmic'.
Using `/usr/lib/jvm/java-6-sun/bin/schemagen' to provide `schemagen'.
Using `/usr/lib/jvm/java-6-sun/bin/serialver' to provide `serialver'.
Using `/usr/lib/jvm/java-6-sun/bin/wsgen' to provide `wsgen'.
Using `/usr/lib/jvm/java-6-sun/bin/wsimport' to provide `wsimport'.
Using `/usr/lib/jvm/java-6-sun/bin/xjc' to provide `xjc'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/ControlPanel' to provide `ControlPanel'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/java_vm' to provide `java_vm'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/javaws' to provide `javaws'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/jcontrol' to provide `jcontrol'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/keytool' to provide `keytool'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/orbd' to provide `orbd'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/pack200' to provide `pack200'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/policytool' to provide `policytool'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/rmid' to provide `rmid'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry' to provide `rmiregistry'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/servertool' to provide `servertool'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/tnameserv' to provide `tnameserv'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/unpack200' to provide `unpack200'.
Using `/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `firefox-javaplugin.so'.
Using `/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `iceape-javaplugin.so'.
Using `/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `iceweasel-javaplugin.so'.
Using `/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `mozilla-javaplugin.so'.
pti@dynip-56-144:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

hope this helps,

Peter

---

### Post by gantww on 2007-09-05
Ok, I installed it. My commandline output looked pretty much the same as yours, except I didn't have as many things installed on the last one. How do I go about figuring out what version of java the different apps need?

---

