---
title: "Frostwire not working"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by Malice007 on 2007-08-17
Frostwire was working just a few days ago. And now when I click on the icon it does nothing. I then went into the terminal and this is what I got:

:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

Next I went to Synaptic Package Manager and looked

I have installed:

Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)
Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
The Java(TM) Plug-in, Java SE 6

I then reinstalled these 3, rebooted. Tried and nothing and I get the same error msg's.

Like I said before this program was working a few days ago just fine.

---

### Post by ThrobbingBrain66 on 2007-08-17
Type this into a terminal and see if that helps
```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by Malice007 on 2007-08-17
Yes that fixed it. Thank you very much. 

Can you tell me why this fixed it and how you knew this might be my problem? I am still learning :)

Thanks again.

---

### Post by ThrobbingBrain66 on 2007-08-17
That's the error that seemingly always spits out when the java-alternatives aren't set correctly.  Basically, Frostwire didn't know where to look for your java installation.  With that command, you told it where to look.

---

### Post by rne1223 on 2007-08-18
I typed "sudo update-java-alternatives -s java-6-sun" in the terminal but now this appears:

```
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/java-rmi.cgi
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/xjc
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
No alternatives for firefox-javaplugin.so.
No alternatives for iceape-javaplugin.so.
No alternatives for iceweasel-javaplugin.so.
No alternatives for mozilla-javaplugin.so.

```

I do have java-6 installed...at least that is what I think. Please help

---

### Post by rne1223 on 2007-08-18
Never mind...somehow it just started working :). Weird but I'm happy.

---

### Post by ThrobbingBrain66 on 2007-08-19
Yeah, I think all that error is saying is that you don't have any other java alternatives installed so there was nothing for it to do.

Glad it's working for you.

---

### Post by Lithium17 on 2007-08-19
Frostwire is the worst filesharing program imaginable, look into bittorrent clients for Ubuntu, the best I know of is Deluge

---

### Post by Patrissimo on 2007-08-21
that worked for me, too. thanks throbbing

---

