---
title: "Java Plugin Query"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by juniah on 2007-11-01
I have the newest JDK and JRE installed from Java thanks to Automatix2.  I've checked my plugins on firefox and this is what I get:

GCJ Web Browser Plugin 0.92

    File name: libgcjwebplugin.so
    The GCJ Web Browser Plugin executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	GCJ 	class,jar 	Yes
application/x-java-applet 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.3 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	GCJ 	class,jar 	Yes
application/x-java-applet;jpi-version=1.4.2_01 	GCJ 	class,jar 	Yes
application/x-java-bean 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.3 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	GCJ 	class,jar 	Yes
application/x-java-bean;jpi-version=1.4.2_01 	GCJ 	class,jar 	Yes
Java(TM) Plug-in 1.6.0_03-b05

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

for all things Java.  In Firefox both Java and Javascript are enabled, however when I try to use an applet (Like the one on Sun's Java site to make sure Java is working) nothing comes up except a grey area where the applet should be.  I can't figure out what I'm missing here.  If someone can point me in the right direction I'd be very grateful.

---

### Post by juniah on 2007-11-01
Alright, Ive tried to reinstall java, but it still isn't working.  I've tried the java test on java's website and even though Ive updated, it still says Im a version behind.

---

### Post by alienexplorers on 2007-11-01
Try from terminal
> sudo apt-get update
sudo apt-get install sun-java6-jdk
sudo update-java-alternatives  --set java6-sun

Then create a symbolic link from the plugin to your .mozilla folder if running firefox.
> ln -s /usr/lib/jvm/JAVA_VERSION/jre/plugin/i386/ns7/libjavaplugin_oji.so

---

### Post by juniah on 2007-11-01
I tired the last line of code you gave me and it didn't work.  it said that....

update-java-alternatives: directory does not exist: /usr/lib/jvm/java6-sun

Im so flumuxed I don't know what to do.

Oh everything else went smoothly, and it said I already had java6

---

### Post by alienexplorers on 2007-11-01
Leave off the java-update line and just enter the symbolic link line instead.

---

### Post by juniah on 2007-11-01
I went into the firefox error console and when I tried to access the add photos option I received a number of Unknown property 'filter's, a Error in parsing value for property 'cursor'.  All ending in Declaration Dropped.  The last error was this uncaught exception: Permission denied to call method Location.toString.

from the java test site:
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

I get unknown properties, and error in parsing values.  All ending in Declaration dropped.

to top it off, I can run bluej and compile to my hearts content.

---

### Post by juniah on 2007-11-01
ok I missed that last post before putting in mine with the error console.

Ive checked all 3 plugin folders (mozilla, firefox, mozilla-firefox) and they all have the symlink to libj avaplugin_oji.so

---

