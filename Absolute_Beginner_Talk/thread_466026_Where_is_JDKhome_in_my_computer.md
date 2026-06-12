---
title: "Where is JDKhome in my computer?"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by cdiem on 2007-06-06
I'm using ubuntu feisty on i386 configuration. There is a program that I'm trying to run, which uses NetBeans, but it keeps telling me, that "JDK 5.0 or newer cannot be found on your machine". I have installed the following packages from synaptic: sun-java5-jdk, sun-java5-jre, j2re1.4 and some other related to java. Other applications for java (but not using NetBeans) run just fine. There's an option in the .conf file of the program, saying that:
> # default location of JDK/JRE, can be overridden by using --jdkhome <dir> switch
#jdkhome="/path/to/jdk"

If I know where the jdkhome is, I can uncomment this and run the program. But where is this?

From the synaptic, here are the installed files for the package sun-java5-jdk:
> /.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/sun-java5-jdk
/usr/share/doc/sun-java5-jdk/README.html
/usr/share/doc/sun-java5-jdk/README.alternatives
/usr/share/doc/sun-java5-jdk/copyright
/usr/share/doc/sun-java5-jdk/changelog.Debian.gz
/usr/share/java-1.5.0-sun-1.5.0.11
/usr/share/applications
/usr/share/applications/sun-java5-jconsole.desktop
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/sun-java5-jdk
/usr/share/doc-base
/usr/share/doc-base/sun-java5-jdk-readme
/usr/share/menu
/usr/share/menu/sun-java5-jdk
/usr/lib
/usr/lib/jvm
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/lib
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/lib/i386
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/apt.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/extcheck.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/idlj.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/jar.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/javac.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/javadoc.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/javah.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/javap.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/jconsole.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/jdb.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/jinfo.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/jps.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/jsadebugd.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/jstack.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/jstat.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/jstatd.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/rmic.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/serialver.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/appletviewer.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/jarsigner.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/jmap.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/man1/native2ascii.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/apt.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/extcheck.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/idlj.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/jar.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/javac.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/javadoc.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/javah.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/javap.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/jconsole.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/jdb.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/jinfo.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/jps.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/jsadebugd.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/jstack.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/jstat.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/jstatd.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/rmic.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/serialver.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/appletviewer.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/jarsigner.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/jmap.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/man/ja/man1/native2ascii.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/javac
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/javadoc
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/apt
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/javah
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/idlj
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/jarsigner
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/java-rmi.cgi
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/jar
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/appletviewer
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/rmic
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/javap
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/native2ascii
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/serialver
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/jps
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/jstat
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/jstatd
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/jinfo
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/jmap
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/jstack
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/jsadebugd
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/jconsole
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/extcheck
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/jdb
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/HtmlConverter
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/include
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/include/jni.h
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/include/linux
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/include/linux/jni_md.h
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/include/linux/jawt_md.h
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/include/jvmdi.h
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/include/jvmpi.h
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/include/jvmti.h
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/include/jawt.h
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/include/jdwpTransport.h
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/lib
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/lib/jconsole.jar
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/lib/sa-jdi.jar
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/lib/orb.idl
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/lib/ir.idl
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/lib/dt.jar
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/lib/htmlconverter.jar
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/lib/tools.jar
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/README.html
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/COPYRIGHT
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/LICENSE
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/THIRDPARTYLICENSEREADME.txt

---

### Post by Skrynesaver on 2007-06-06
I'm far from a Java expert but I'd try 
/usr/share/java-1.5.0-sun-1.5.0.11
and if that didn't work 
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/
and if were still failing I'd try
/usr/java/

---

### Post by Seisen on 2007-06-06
Check to see if its located in 

```
/usr/lib
```

---

### Post by cdiem on 2007-06-06
Thanks, but none of these seem to be the one. In these cases, it gives me the following: 
> Cannot find java.exe
Neither /usr/java\jre\bin\java.exe nor /usr/java\bin\java.exe exists
The program that I'm trying to run is aiotrade. It runs fine under windows on my other machine, but as it uses java, I think it should run fine under linux as well.
Edit: the other paths give messages, similar to the described one. It seems to me, as if it is searching an .exe file (odd).

---

### Post by Seisen on 2007-06-06
Did you type this or copy it?

```
/usr/java\jre\bin\java.exe nor /usr/java\bin\java.exe 
```

Try looking in 

```
/usr/lib/jvm
```

---

### Post by cdiem on 2007-06-06
I typed this the same way as it looks, when the window with the error message comes. I know it looks odd (at least to me it seems so). The path "/usr/lib/jvm" gives me a similar error message:
> Cannot find java.exe. Neither /usr/lib/jvm\jre\bin\java.exe nor /usr/lib/jvm\bin\java.exe exists.

I cannot copy this, because it comes out from a window (I think it is a prompting window of wine; I have to use wine to open the program, as it uses an .exe file).

---

### Post by Dieg oTrazzi on 2007-10-30
I just installed Gutsy, and unfortunately I get the same error message when I try to open Aiotrade. I have no idea what else to try.

---

### Post by Dieg oTrazzi on 2007-10-30
Ok, I found the JDK home folder.
I you want to run Aiotrade from Gutsy with java1.5 type: 


```
./aiotrade  --jdkhome /usr/lib/jvm/java-1.5.0-sun
```

---

