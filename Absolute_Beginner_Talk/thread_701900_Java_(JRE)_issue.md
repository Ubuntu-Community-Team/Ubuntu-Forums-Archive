---
title: "Java (JRE) issue"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by quadm on 2008-02-19
I have JRE installed according to synaptic. (packages: sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin).

And when I run java -version I get
```

$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)

```

All seems well, but whenever I access a java page in firefox I run into issues. for instance when i run Java's jre test page it says my version is 1.4.2. I've tried recreating the symbolic links in the mozilla directories but that doesn't help.

When I type about : plugins into firefox I get this
> Java(TM) Plug-in 1.6.0_03-b05

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_03

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_03 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_03 	Java 		Yes
Which also seems to say i have 1.6.0_03 installed. Any idea whats going on here?

Thanks.

---

### Post by y-lee on 2008-02-19
I'm not sure try setting the java version with 

```
sudo update-alternatives --config java
```

---

### Post by quadm on 2008-02-19
I get:

```

$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/cacao
*+        3    /usr/lib/jvm/java-6-sun/jre/bin/java

```

I have a feeling its an issue with Firefox and the plugin

---

### Post by Sinkingships7 on 2008-02-19
go back to add/remove and uninstall all those packages.

then open a terminal and paste this into it:
```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```

---

### Post by quadm on 2008-02-19
Thanks for the advice. I just "completely" removed all of those packages and reinstalled them. No luck. I also reinstalled firefox. Still no luck. I also got rid of the GCJ plugin in synaptic because i figured that might be causing interference. Maybe if I could just get to that menu that firefox displays when it first detects a java app and select Java6 it would work from there- but i have no idea to get there because now when i go to pages with java apps i just get blank squares.

---

### Post by y-lee on 2008-02-19
Hmm interestingly enough Java's jre test page says I'm also using JRE version 1.4.2_xx and I'm not.  it seems to be picking up on /usr/bin/gij-4.2 instead of what i am using /usr/lib/jvm/java-6-sun/jre/bin/java.

Java however gives me no problems. 

Not sure, I'll look into it :confused:

Sorry i couldn't be more help.

---

### Post by AndyCooll on 2008-02-19
How about removing all those and try installing Iced-Tea Java instead?

:cool:

---

### Post by y-lee on 2008-02-19
[This site ]("http://www.javatester.org/version.html")however correctly identifies my version of java.

Strange :confused:

---

### Post by quadm on 2008-02-19
Thanks for all the help!! Uninstalling Sun's Java6 and installing iced tea solved my issue. Still dont understand why java6 didn't work but oh well.

---

