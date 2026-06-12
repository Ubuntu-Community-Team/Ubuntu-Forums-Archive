---
title: "64 Bit Java Woes"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by groucho_marx on 2007-12-05
To my knowledge I have the latest version of Java, yet I am still having issues. 

java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)

Also when I do about: plugins, everything is enabled. I've seen many a thread devoted to Java issues  and some even addressing 64 bit Ubuntu + Java problems, but mine is never solved by the threads conclusion. Hopefully this will be specific and not too painful. Thanks in advance.

---

### Post by GSF1200S on 2007-12-05
> **groucho_marx said:**
> To my knowledge I have the latest version of Java, yet I am still having issues. 

java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)

Also when I do about: plugins, everything is enabled. I've seen many a thread devoted to Java issues  and some even addressing 64 bit Ubuntu + Java problems, but mine is never solved by the threads conclusion. Hopefully this will be specific and not too painful. Thanks in advance.

Which plugin are you using? Are you using firefox? Please post the reults of ```
about:plugins
``` just so we can see what it says.

You really have 2 options. Install a 32bit firefox as an alternate to use, or run swiftweasel (an optimal build of Firefox) and use the Blackdown Java plugin, available in add/remove. I have 64bit and I know mine works. Blackdown Java is not perfect, and occasionally pages will not work, but Sun has said they will include a 64bit plugin for Firefox with the release of JRE7, so that should make it all the easier.

---

### Post by groucho_marx on 2007-12-05
Yes I'm using firefox.
GCJ Web Browser Plugin (using IcedTea) 1.4

    File name: gcjwebplugin.so
    The GCJ Web Browser Plugin (using IcedTea) executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.7 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.7.0_00 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.7 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.7.0_00 	IcedTea 	class,jar 	Yes

---

### Post by GSF1200S on 2007-12-05
> **groucho_marx said:**
> Yes I'm using firefox.
GCJ Web Browser Plugin (using IcedTea) 1.4

    File name: gcjwebplugin.so
    The GCJ Web Browser Plugin (using IcedTea) executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.7 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.7.0_00 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.7 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.7.0_00 	IcedTea 	class,jar 	Yes

DO NOT USE GCJ JAVA PLUGIN!!! REMOVE IT IMMEDIATELY! GCJ doesnt have a security monitor, so if a website put the java code to say, FORMAT YOUR ENTIRE HARD-DRIVE, it will run it without asking questions. It makes me angry that its in the repos- this plugin should not be included IMHO.

Open Add/Remove and remove that plugin (or use synaptic). If you want to use a 64bit browser, go here:

[http://downloads.sourceforge.net/swiftweasel/swiftweasel-2.0.0.11_athlon64-64bit_ubuntu-AMD64.deb?modtime=1196597723&big_mirror=0](http://downloads.sourceforge.net/swiftweasel/swiftweasel-2.0.0.11_athlon64-64bit_ubuntu-AMD64.deb?modtime=1196597723&big_mirror=0)

This will download Swiftweasel. After installing, go into the repos and install the Blackdown java plugin and RE (see screenshot).

Alternatively, run a 32 bit firefox and use the 32bit plugins (do a quick forum search for that).. Ill help you every step of the way.. I understand its a little frustrating, but its the only toughie left in the 64bit linux world (windows 64 is far worse)..

---

### Post by groucho_marx on 2007-12-06
Okay, I got Swiftweasel and thought I got Blackdown all installed correctly. Now when I try a Java site my whole browser just closes. What'd I do :confused:? BTW I have Gutsy, not sure if that matters for this purpose.

---

### Post by groucho_marx on 2007-12-06
You guys are smarter than this.

---

### Post by GSF1200S on 2007-12-07
> **groucho_marx said:**
> You guys are smarter than this.

Well, I dont know about me, but yes, we are smarter than this. The browser closing happens to me ONCE IN A WHILE, like 3 or 4 times total.. but with all java sites? Im trying to figure out whats going on with your setup... I must be missing something... I might suggest you try a 32bit firefox install if you need java. I dont know why, but my Blackdown seems to work fine...

---

