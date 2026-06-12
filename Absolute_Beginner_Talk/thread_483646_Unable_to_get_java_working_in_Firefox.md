---
title: "Unable to get java working in Firefox"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by virgilnilson on 2007-06-25
Hello, it seems I am having trouble getting java to run in firefox.

I have followed the directions in several guides and executed this command

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

I have also installed the Blackdown edition as it wasn't working, so I didn't think it could cause any harm. Everything seemed to go without a hitch, however whenever I try to load a page with a java game in it, I simply get a gray box, occasionally it will tell me something along the lines of "error loading applet".

Doing java -version in terminal produces this output

```
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

```

And about:plugins in firefox produces this

```
Java(TM) Plug-in Blackdown-1.4.2-02

    File name: libjavaplugin_oji.so
    Blackdown Java-Linux Java(TM) Plug-in 1.4.2

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
application/x-java-applet;jpi-version=1.4.2 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_01 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_02 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_03 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_04 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_05 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_06 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_07 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_08 	Java 		Yes
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
application/x-java-bean;jpi-version=1.4.2 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_01 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_02 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_03 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_04 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_05 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_06 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_07 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_08 	Java 		Yes
```

Whenever I try to load a page with an applet on it, it asks me whether I want to trust the applet. Also, when loading [http://www.java.com/en/download/help/testvm.xml]("http://www.java.com/en/download/help/testvm.xml") the applet DOES load, but it tells me that I am using an older version of Java.

Doing sudo apt-get update doesn't seem to pick anything up, and rerunning that original install command says everything is up to date.

I've restarted Firefox several times, and I've even logged out and logged back in, however it still will not work.

Any clues?

---

### Post by w4ett on 2007-06-25
Check out this Wiki for the Java non-free install method:

[http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation](http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation)

---

### Post by virgilnilson on 2007-06-25
> **w4ett said:**
> Check out this Wiki for the Java non-free install method:

[http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation](http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation)

Maybe I'm daft but I can't find anything on there that seems as if it would change the installation.

Also, I'm not sure if this means anything but occasionally some of the applets seem to load the first frame of animation/whatever, but then its just frozen like that, as an image. Some times my cursor will change when going over it, sometimes not. Either way any interaction is impossible at that stage. More often however it just stays gray.

It may be worth noting that this applet also works, as java's version detecting applet, both are gray boxes for about 5 seconds then finally give me an output. I have a feeling this is all because I'm on version 1.4.2, and there is supposed to be a 1.6 out now, no?

Update: I have set the default version to sun's 1.6 java via this menu:```
sudo update-alternatives --config java

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
          2    /usr/lib/jvm/java-gcj/jre/bin/java
*         3    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        4    /usr/lib/j2se/1.4/bin/java
          5    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 

```

As you can see, 3 is set as the default now.

Also, now java -version produces this output:

```
java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

```

However in about:plugins, firefox continues to display 1.4.2 as the highest version. I'm thinking that I may have to uninstall these previous versions for it to use 1.6. Am I wrong? Also how would I go about doing that?

---

### Post by virgilnilson on 2007-06-25
SOLUTION: I had to remove all of the other java versions, everything now works.

---

