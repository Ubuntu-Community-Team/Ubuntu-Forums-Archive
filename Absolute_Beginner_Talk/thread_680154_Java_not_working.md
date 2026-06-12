---
title: "Java not working"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Emurray1122 on 2008-01-27
I've bounced around in these posts and have tried all I can think of.  SO, I need some help in getting java to work.  I go to the sun website and try the java test.  Nothing happens.

Java is enabled in Firefox | edit | preferences | content

liz@L-ITB-00FF2:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

Copyright (C) 2007 Free Software Foundation, Inc.

I've gone through Snayptic Package and loaded all java except for the developer files.

I've tried to manually download and install creating the symn link.

Still doesn't work.

HELP

---

### Post by taurus on 2008-01-27
Try installing it with

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
sudo update-alternatives --config java
```
and pick the latest one as your default version.

---

### Post by Emurray1122 on 2008-01-27
do I need to uninstall the java that shows installed?

---

### Post by taurus on 2008-01-27
Don't worry about the gij version.  Just install the Sun's version and configure your machine to use it instead of the gij.

---

### Post by Emurray1122 on 2008-01-27
I did as suggested.  Still doesn't work when I go to the JAVA test site.

---

### Post by taurus on 2008-01-27
What are the outputs of these commands from a terminal?

```
java -version
sudo update-alternatives --config java
```

p.s.  Don't forget to close your web browser first and then open it again after you installed/configured java.

---

### Post by Emurray1122 on 2008-01-27
liz@L-ITB-00FF2:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)
liz@L-ITB-00FF2:~$ sudo update-alternatives --config java
[sudo] password for liz:

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/cacao
          3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
 +        4    /usr/lib/jvm/java-gcj/jre/bin/java
*         5    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection n

---

### Post by taurus on 2008-01-27
And you did install the plugin, sun-java6-plugin?

Try rebooting your machine.

---

### Post by Emurray1122 on 2008-01-27
I followed your directions.  I have already rebooted the machine.

---

### Post by taurus on 2008-01-27
Open firefox, I assume you use firefox as your main web browser, and in the address field, type

```
about:plugins
```
Do you see java plugin on the list and which version does it say?  Post a screenshot of that if you wish.

p.s.  Which JAVA test site do you use?

---

### Post by Emurray1122 on 2008-01-27
GCJ Web Browser Plugin 0.92

    File name: libgcjwebplugin.so
    The GCJ Web Browser Plugin executes Java applets.

Not sure if I got this right.  I tried to do an attachment.  Above is what is says.  How did I get that and how do I change it?

[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

That's the test site.

Liz M

---

### Post by Emurray1122 on 2008-01-27
Not too good at forums either.  It doesn't look like it got posted completely.  SO,  here's the post again

test site:  [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

GCJ Web Browser Plugin 0.92

    File name: libgcjwebplugin.so
    The GCJ Web Browser Plugin executes Java applets.

Liz M

---

### Post by natarnsco on 2008-01-27
I am having the same problem.  Java is installed following instructions in this thread as well as others, a lot of Java plugins in Firefox about:plugins are showing up and are enabled, but no applets. 

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



I am using the test at [http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1)

In terminal running the version check produces:

java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+       2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 




Any suggestions?

---

### Post by marie@idiomatic on 2008-01-28
I am having a similar problem - perhaps the same as the user who started this thread.

Short version: I think Java installs all right, but the plugin function doesn't work, and I don't know why.

Long version:

I tried a lot of things, following advice from this thread and some other threads (using sometimes the commandline and sometimes Synaptic depending on the advice given) after first following Sun's instructions ([http://java.com/en/download/help/5000010500.xml#install]("http://java.com/en/download/help/5000010500.xml#install")), as well as browsing Synaptic's package lists more or less aimlessly and installing bits and pieces which seemed to be possibly relevant, and I am afraid I probably have a lot of unnecessary (and perhaps conflicting?) things installed by now. I don't know if I need to tidy up a bit before starting over again - and if so, how to do it (uninstall things and so on)? 

I did try deleting some java folders before trying again (everything in "/usr/java/" for instance), but I suspect a lot of other locations are also involved (just noticed the existence of the directories "/usr/lib32/" and "/usr/lib64/", for instance). I also followed the advice of deleting /usr/bin/java in [http://ubuntuforums.org/showthread.php?t=679504&highlight=jre](http://ubuntuforums.org/showthread.php?t=679504&highlight=jre) and since I did that, "java -version" yields "bash: /usr/bin/java: No such file or directory". Before I deleted /usr/bin/java, there was an output stating a version of java, but I forget what exactly it said at various stages of installing and removing and installing again,

When I type "about:plugins" in firefox, I get no java lines (except when the IcedTea plugin mentioned below was installed).

"sudo update-alternatives --config java" yields
          1    /usr/bin/gij-4.2
 +        2    /usr/lib/jvm/java-7-icedtea/jre/bin/java
          3    /usr/lib/jvm/java-6-sun/jre/bin/java
*         4    /usr/lib/jvm/ia32-java-6-sun/jre/bin/java
          5    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

When I load websites that require Java, I am offered a "click here to install missing plugins" feature at the top of the page and at the place where the applet should have been. When I click it, I get "Choose a plugin for media type application/x-java-vm:" and "The GCJ Web Browser Plugin (using IcedTea)" is suggested. After installation, when I restart firefox and load the page again, there are no more complaints of missing plugins - but also no applet. Just a grey square where it would fit in. That is why I uninstalled the IcedTea thing and tried to install Sun's Java following the instructions on [http://java.com/en/download/help/5000010500.xml#install](http://java.com/en/download/help/5000010500.xml#install)

I have tried both the 32-bit version (because the Sun instructions say I should for applet support) and the amd64 version (just in case the 32-bit version wouldn't work on my system). I have also browsed the package lists in Synaptic and installed something I found there that seemed like it could be Java (apparently version 5, I think). It didn't help, so I removed it again.

My latest attempt was installing the 32-bit version from Sun again after first removing as many Java related things as I could find on my computer. Still no applets, still no Java in "about:plugins".

I have been wondering if I was creating the symbolic link in the right folder (referred to in the installation instructions as "the plugin folder of the Mozilla installation directory"). I tried various locations and ended up believing in /usr/lib/firefox/plugins/ (but also tried /usr/lib/mozilla-firefox/plugins and /usr/lib/mozilla/plugins and even created a plugins directory under .mozilla/firefox/).

I don't know what else I may be doing wrong. But I just found a thread in this forum saying "Firefox is a great browser, unfortunately the 32 bit plugins don't work in the 64 bit version that Synaptic installs to 64 bit Dapper" (see [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)). Could this be the problem? Unfortunately, I don't really understand what is being said there, but the author talks about "setting up 32 bit Firefox and then the plugins". Is that the way to go? And if yes, could someone explain what steps I should take? Does it involve installing Firefox all over? 

I'm sorry about writing such a long and probably confusing message. It is just that I am very confused myself now, but trying even so to supply as much information as possible before I forget even more details of what I already tried.

I would be very grateful for any help.

Marie

---

### Post by marie@idiomatic on 2008-01-28
Just discovered this message when I restarted firefox from the commandline:

LoadPlugin: failed to initialize shared library /usr/java/jre1.6.0_03/plugin/i386/ns7/libjavaplugin_oji.so [/usr/java/jre1.6.0_03/plugin/i386/ns7/libjavaplugin_oji.so: wrong ELF class: ELFCLASS32]

Does that help to identify the problem?

---

### Post by natarnsco on 2008-01-30
I got mine working, even though I don't understand why.  Using Synaptic I installed several IcedTea packages, but it still didn't work.  Then I installed Java 6 JDK, and it suddenly started working.  People having trouble like me might try installing the JDK and seeing if it works.

---

### Post by marie@idiomatic on 2008-01-31
natarnsco, where did you find Java 6 JDK, and how did you install it? I just found and installed icedtea-java7-jdk via Synaptic, but that didn't help. I also installed various other packages with "java" in their name or description.

I keep getting:

LoadPlugin: failed to initialize shared library /usr/java/jre1.6.0_03/plugin/i386/ns7/libjavaplugin_oji.so [/usr/java/jre1.6.0_03/plugin/i386/ns7/libjavaplugin_oji.so: wrong ELF class: ELFCLASS32]

in the terminal after restarting firefox. 

I fear that my having deleted /usr/bin/java was perhaps a mistake, because I now get the following output from "java -version":

The program 'java' can be found in the following packages:
 * j2re1.4
 * kaffe
 * cacao
 * java-gcj-compat
 * gij-4.1
 * jamvm
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found

And I also no longer get any grey boxes in place of applets even when IcedTea is installed. It seems to me as if my various Java-like installations are not found at all by the system.

What was in /usr/bin/java, and can I restore it somehow? Should I want to try and restore it?

"sudo update-alternatives --config java" now gives me

          1    /usr/bin/gij-4.2
*         2    /usr/lib/jvm/java-7-icedtea/jre/bin/java
          3    /usr/lib/jvm/java-6-sun/jre/bin/java
          4    /usr/lib/jvm/ia32-java-6-sun/jre/bin/java
          5    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
 +        6    /usr/lib/j2se/1.4/bin/java
          7    /usr/lib/jvm/java-gcj/jre/bin/java

There is still no trace of Java when I type "about:plugins" in firefox.

I feel completely stuck now, actually, as I have no idea what I should try next. I wonder if Emurray1122 found a solution?

---

### Post by emarkd on 2008-01-31
The java6 jdk is in synaptic.  You have to enable the extra repositories, then search for sun-java6-jdk

---

### Post by marie@idiomatic on 2008-01-31
Thanks, emarkd - I found it and installed it now.

Unfortunately, applets still not working :(

Any ideas, anyone?

:confused:

---

### Post by marie@idiomatic on 2008-02-12
Just in case somebody searches this thread for solutions, what eventually solved most of my difficulties was the script provided on [http://ubuntuforums.org/showthread.php?t=202537]("http://ubuntuforums.org/showthread.php?t=202537"). My problem turned out to be that because I am an Ubuntu AMD64 user, my Firefox installation was also 64 bit, but the Java plugin from Sun only comes as 32 bit, and the 32 bit plugin apparently doesn't work in a 64 bit browser. So I installed 32 bit Firefox (which didn't affect my 64 bit Firefox install, by the way - I now simply have both), and I will then have to view sites with Java applets using that install of Firefox until a 64 bit Java plugin is released by Sun. Apparently, it is already under development.

I do still have some difficulties with Java applets on certain sites, but I will start a new thread on that in the "x86 64-bit Users" forum.

---

### Post by Miljet on 2008-02-15
I am having the same problems on my laptop. However I finally did get it installed and working on my desktop computer. After trying for 2 weeks using the instructions at the [www.java.com](www.java.com) site to no avail, I used "sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts." It worked like a charm on the desktop.

However, when I tried it on the laptop, I forgot to first enable all repositories so it couldn't find sun java. Like everyone else, I tried installing everything I could find with java in the name. I believe that something else that I installed is preventing the sun-java plugin from being properly installed.

When I type "sudo update-alternatives --config java" on both machines the laptop gives me three options: 
          1    /usr/bin/gij-4.2
          2    /usr/bin/cacao
*+        3    /usr/lib/jvm/java-6-sun/jre/bin/java

On the desktop, which is working, I get two options:
          1    /usr/bin/gij-4.2
*+      2    /usr/lib/jvm/java-6-sun/jre/binjava

I am about to the point of deleting the whole installation and starting over. I could have done that many times over during the time I have spent fighting a losing battle.

---

### Post by Miljet on 2008-02-15
If anyone is still following this thread, I finally fixed mine, and killed two birds with one stone. I went into Synaptic Package Manager, did a search for GCJ Web Browser Plugin, and completely uninstalled it. Suddenly my java applets started working.

As a side benefit, it also got rid of the annoying pop-up window that an applet was being installed.Finally!!!!!

---

### Post by ubuntu-freak on 2008-02-16
Crikey people! Be careful what you install and don't go to java.com when you want java. 
 
Just to let you know, IcedTea Java is recommended for 64-bit users as the browser plugin will work.
 
If anyone else is having issues, take a look at my [how-to](http://ubuntuforums.org/showthread.php?t=661833). It deals with streaming, java, multimedia and video playback (including commercial DVDs), video conversion and also ripping/burning of DVDs.
 
Hope that helps.
 
Nathan

---

