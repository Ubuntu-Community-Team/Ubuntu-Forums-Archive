---
title: "Java problem in Ubuntu"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2007-01-22
I play quite a few Java games on Windows, they mostly work fine. However when i try playing these games on Ubuntu they are often too slow & jumpy to play..
How can i solve this?

(Here is an example of one [http://fallingsandgame.com/sand/pyro.html](http://fallingsandgame.com/sand/pyro.html))

---

### Post by mikewhatever on 2007-01-22
I've just played the falling stuff game, and it seemed to work fine. Do you use firefox for browsing? Is your system updated?

---

### Post by Captain Kirk76 on 2007-01-22
I am using Ubuntu Linux 6.06 with Mozilla Firefox. Its all uptodate.

I am really annoyed with this, Most CD Games don't work correctly, and now i discover the internet ones are not working correctly!

---

### Post by mikewhatever on 2007-01-22
Let's hope Java will be updated soon enough, along with flash. I'll try that sand game later in Windows, just to compare.

---

### Post by Captain Kirk76 on 2007-01-22
Thanks, I'd appreciate if you could try it in Windows and report back ,jsut to see if it is my Liux thats not working correctly.

---

### Post by bollix47 on 2007-01-22
What version of java are you using?

Open a terminal and type:

java -version

if it's not java version "1.5.0_08" then you could install the sun java runtime via Synaptic.  Search for sun-java.

You will need the multiverse repository in order to find sun-java.

You can activate it thru settings - repositories in Synaptic.

---

### Post by Captain Kirk76 on 2007-01-22
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

---

### Post by Captain Kirk76 on 2007-01-22
OK, i installed the 1.5 version, but when i go java -version it still produces

java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)
adam@Adams-Computer:~$

---

### Post by bollix47 on 2007-01-22
Open a Terminal.

Type the following:

```
sudo update-alternatives --config java
```

Choose the correct version.

---

### Post by jvc26 on 2007-01-22
Just to let you know I have no performance degradation in the falling sand game between windows and linux. You need to change your java configs with this command from terminal:
EDIT:: Apologies, hadnt read the post above, my instructions were the same.
Il

---

### Post by Captain Kirk76 on 2007-01-22
What do i press after entering the command.
(Which is correct)

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
      2        /usr/lib/jvm/java-gcj/jre/bin/java
*+    3        /usr/lib/j2se/1.4/bin/java
      4        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

---

### Post by bollix47 on 2007-01-22
4

---

### Post by mikewhatever on 2007-01-22
Yes, looks like 4 is the new one. Do you have automatic updates enabled? I know I've already asked, but since 6.06 is supposed to be LTS, there is no reason your java shouldn't have been updated.

---

### Post by bollix47 on 2007-01-22
Just in case you didn't realize it you have to also install sun-java5-plugin using Synaptic so that Firefox will pick the new version.
You can check which version Firefox is using by typing ```
about:plugins
``` in the url/address window.

Should look like:

Java(TM) Plug-in 1.5.0_08-b03

    File name: /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/plugin/i386/ns7/libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_08

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
application/x-java-applet;jpi-version=1.5.0_08 	Java 		Yes
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
application/x-java-bean;jpi-version=1.5.0_08 	Java 		Yes

---

### Post by Captain Kirk76 on 2007-01-22
> **mikewhatever said:**
> Yes, looks like 4 is the new one. Do you have automatic updates enabled? I know I've already asked, but since 6.06 is supposed to be LTS, there is no reason your java shouldn't have been updated.

Yes. An updater does regularly update things, so i do have auto updates on, so for some reason it didn't update Java. :/

---

### Post by phossal on 2007-01-22
You can always download the latest Java (version 6) yourself, using [Sun's method]("http://ubuntuforums.org/showthread.php?t=332674"). Then you can update update-alternatives and you're on your way.

---

