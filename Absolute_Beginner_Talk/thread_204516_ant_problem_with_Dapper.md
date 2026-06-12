---
title: "ant problem with Dapper"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by loudking on 2006-06-27
Hello, Experts.

I have just updated my Ubuntu to Dapper, and the new java version changed from "gcj" to "sun-java-1.5". I tested "java -version" and "javac -version", and it is correct.

But I encountered a problem when compiling a project with ant. It seems as if Ubuntu is still trying to launch "gcj" instead of "sun-java-1.5", which confuses me.

My compile part in build.xml
```
     24         <!-- compile -->
     25         <target name="compile" depends="init" description="compile the source files">
     26                 <mkdir dir="${classes.dir}"/>
     27                 <javac srcdir="${src.dir}" destdir="${classes.dir}" target="1.5" source="1.5">
     28                         <classpath refid="master-classpath"/>
     29                         <compilerarg line="-source 1.5"/>
     30                 </javac>
     31         </target>
```

Error Message
=================================================================
Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/lib/tools.jar
Buildfile: build.xml

init:

compile:
    [javac] Compiling 4 source files to /home/wanghongliang/sourcecode/java/NetworkPerformance/classes

BUILD FAILED
/home/wanghongliang/sourcecode/java/NetworkPerformance/build.xml:27: Unable to find a javac compiler;
com.sun.tools.javac.Main is not on the classpath.
Perhaps JAVA_HOME does not point to the JDK

Total time: 2 seconds
=================================================================

I guess maybe I should set JAVA_HOME to somewhere, but just didn't know..............
Would you please give me hand?
Thanks

---

### Post by ubuntuuser on 2006-06-27
Have you tried ```
sudo update-alternatives --config java
```

---

### Post by loudking on 2006-06-27
[QUOTE=ubuntuuser]Have you tried ```
sudo update-alternatives --config java
```[/QUOTE]
yes

  Selection    Alternative
-----------------------------------------------
      1        /usr/lib/j2re1.5-sun/bin/java
      2        /usr/bin/gij-wrapper-4.0
      3        /usr/bin/gij-wrapper-4.1
 +    4        /usr/lib/jvm/java-gcj/jre/bin/java
*     5        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

and I select 5

---

### Post by loudking on 2006-06-27
anybody could help me?

---

### Post by ubuntuuser on 2006-06-27
Ok, I am just guessing now because I've never worked with ant. I had a problem once soon after installing java where all java links in /usr/bin were wrong. If you go to /usr/bin and type ```
ls -l java*
``` there should be some links to /etc/alternatives/. If not (which was the mistake in my case) correct them. Next, go to /etc/alternatives and use the same command to see the links here. They should all point to /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/. Can you compile regular java files? I mean, does ```
javac somefile.java
```work?

---

### Post by loudking on 2006-06-30
[QUOTE=ubuntuuser]Ok, I am just guessing now because I've never worked with ant. I had a problem once soon after installing java where all java links in /usr/bin were wrong. If you go to /usr/bin and type ```
ls -l java*
``` there should be some links to /etc/alternatives/. If not (which was the mistake in my case) correct them. Next, go to /etc/alternatives and use the same command to see the links here. They should all point to /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/. Can you compile regular java files? I mean, does ```
javac somefile.java
```work?[/QUOTE]

Well, that is the problem.
I can compile with sun-java-1.5
but when I use ant, it seems link to gcj
and I simply do not know why.....

---

