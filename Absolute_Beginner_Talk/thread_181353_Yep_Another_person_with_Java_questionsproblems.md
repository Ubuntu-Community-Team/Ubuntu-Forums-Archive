---
title: "Yep Another person with Java questions/problems"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by KarmaKing on 2006-05-24
[COLOR="DarkOrange"]ok, so I thought I had Java installed before, but I guess I missed a line somewhere. 
Now it is showing this in my config file for alternatives[/COLOR]
> There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/lib/j2re1.5-sun/bin/java

[COLOR="DarkOrange"]Press enter to keep the default[*], or type selection number:
my first question is what is the cross and asteric representing? Second Question is, I altered my VM config file so the sun was at the top of the list and as described here [/COLOR]
([https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29#head-fabecb1554d75cd3116507e4da83335d4e4f8f3e](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29#head-fabecb1554d75cd3116507e4da83335d4e4f8f3e))
> # This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

/usr/lib/j2sdk1.5-sun
/usr/lib/jvm/java-gcj
/usr


[COLOR="DarkOrange"]First problem is when I go to do it for the jar and others it comes up like this[/COLOR]
> There are 2 alternatives which provide `jar'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/fastjar
*+    2        /usr/lib/jvm/java-gcj/bin/jar

Press enter to keep the default[*], or type selection number:

[COLOR="DarkOrange"]I notice that the cross is place where the asteric is on the jvm and ther is no sun option for jar, javah, javoc ect...[/COLOR]

[COLOR="DarkOrange"]second problem is when i check the version of java I am running I get this:[/COLOR]
> java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)

where options include:
    -d32          use a 32-bit data model if available

    -d64          use a 64-bit data model if available
    -client       to select the "client" VM
    -server       to select the "server" VM
    -hotspot      is a synonym for the "client" VM  [deprecated]
                  The default VM is client.

    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose[:class|gc|jni]
                  enable verbose output
    -version      print product version and exit
    -version:<value>
                  require the specified version to run
    -showversion  print product version and continue
    -jre-restrict-search | -jre-no-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions
    -esa | -enablesystemassertions
                  enable system assertions
    -dsa | -disablesystemassertions
                  disable system assertions
    -agentlib:<libname>[=<options>]
                  load native agent library <libname>, e.g. -agentlib:hprof
                    see also, -agentlib:jdwp=help and -agentlib:hprof=help
    -agentpath:<pathname>[=<options>]
                  load native agent library by full pathname
    -javaagent:<jarpath>[=<options>]
                  load Java programming language agent, see java.lang.instrument
[COLOR="DarkOrange"]is this correct or am I mising something?

last question.  I know in dapper sun is in synaptic, but should Sun java be visible in synaptic on breezy after install is complete?[/COLOR]

---

### Post by pertti on 2006-05-24
I'm not sure, but I believe that the cross is the default option in Ubuntu (gcj) and the asterisk is the currently chosen one.

As for the jar, javadoc, etc commands, I only tried javac, and it was already set when I selected the alternatives for java. Maybe this is the case for the other commands. (Can't check it now, not in Ubuntu)

And to check Sun's java version, the command you have to use is this:

```
java -version
```

which should print the first three lines of the output you posted.

---

### Post by KarmaKing on 2006-05-24
[QUOTE=pertti]

which should print the first three lines of the output you posted.[/QUOTE]
 
Hi pertti,

so the question now, if I am only supposed to get the first three lines, what is the other stuff??

And why if the cross represents the default is it not over Sun option, or does it have to be??

thanks 

KK

---

### Post by pertti on 2006-05-24
The rest of the lines are usage information. This is what the majority of command line programs output when you enter options they don't understand, so maybe you wrote something wrong (like --version instead of -version, which is the case of most programs, but not sun's java).

By default option I mean the option that comes selected with a new install of Ubuntu. Since Sun's java is not free software (free as in "free speech", not as in "free beer" ;), and gcj is, Sun's java won't be that default option (at least for a good while). But that's a "default" in the sense of "reset all my choices", not in "use this version of java". So you should be doing fine with an asterisk in Sun's java, and if "java -version" shows those three lines.

Hope this helps

---

### Post by KarmaKing on 2006-05-24
thank you pertti.

---

