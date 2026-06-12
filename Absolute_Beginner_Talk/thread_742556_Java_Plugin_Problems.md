---
title: "Java Plugin Problems"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by demarshall on 2008-04-01
I have been attempting to get the Java plugin working in Ubuntu. I followed the directions on Sun's web site to make a link in the /usr/lib/firefox/plugin directory from the file as per the instructions with the following command but with that link in the Firefox plugin directory, Firefox crashes as soon as it starts up.

sudo ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so

Does anybody see anything wrong with my command or have any idea why the link causes Firefox to crash.

---

### Post by Joeb454 on 2008-04-01
Why not install Java from the Ubuntu repositories?

I know it's in there somewhere :)

---

### Post by iris-n on 2008-04-01
Please describe your attempts more thoroughly. You seldom have to make a link manually.

Have you ```
sudo apt-get install sun-java6-plugin
```?

---

### Post by ajmorris on 2008-04-01
> **demarshall said:**
> I have been attempting to get the Java plugin working in Ubuntu. I followed the directions on Sun's web site to make a link in the /usr/lib/firefox/plugin directory from the file as per the instructions with the following command but with that link in the Firefox plugin directory, Firefox crashes as soon as it starts up.

sudo ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so

Does anybody see anything wrong with my command or have any idea why the link causes Firefox to crash.

hi there,
although it is much easier to use the plugin from the ubuntu repositories, the syntax of you command is slightly incorrect.
The correct syntax is: ```
sudo ln -s <target file> <name of link>
```

AJ

---

### Post by demarshall on 2008-04-02
> **iris-n said:**
> Please describe your attempts more thoroughly. You seldom have to make a link manually.

Have you ```
sudo apt-get install sun-java6-plugin
```?

I tried that and it tells me that I already have the newest one installed. I installed Java through Synaptic but the check on Sun's site doesn't verify that I have it installed.

Here's the link:

[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

It just says that I don't have the recommended version installed.

I don't recall the site that I was trying to access when I realized the problem. I wonder if it is working but the Sun site just figures that I should have a newer version.

If you install it from their site, it says that you need to create a link in your browser's plugin directory. Is that not the case any longer?

[http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

---

### Post by iris-n on 2008-04-02
It is the case still. But not when installing from the repositories.

Your command is perfect (**ajmorris**, the system just uses the source's name when none is specified, nothing wrong with that), just note that you have to execute it while in the /usr/lib/firefox/plugin folder. But even if it where wrong, it wouldn't make firefox crash, must be some other arcane reason.

But, and that may be the cause of your problems, if you installed from more than one source, the system won't know which to use, and may use the wrong version.

Try this commands: ```
java -version
``` This tells you what version is installed, mine is:
java version "1.6.0_05"
Java(TM) SE Runtime Environment (build 1.6.0_05-b13)
Java HotSpot(TM) Client VM (build 10.0-b19, mixed mode, sharing)

It's the current version, and passes the sun test.

To make sure your system uses the correct one: ```
sudo update-alternatives --config java
``` And then select sun-java 6.

Make sure you remove your previous attempts. If it still doesn't work, paste here the results of the commands, and let's see what we can do.

---

### Post by demarshall on 2008-04-02
Here is the output of the two commands:

david@davids-computer:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
david@davids-computer:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:

iris-n I see that your java is a newer release than mine. Is that a problem?

Thanks for the assistance on this problem.

---

### Post by chris82543 on 2008-04-03
an easy way to do it is to go to a web site that requires java in firefox and it will ask you if you want to install the required programs, just follow the instructions

---

### Post by gandaran on 2008-04-03
> **demarshall said:**
> Here is the output of the two commands:

david@davids-computer:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
david@davids-computer:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:

iris-n I see that your java is a newer release than mine. Is that a problem?

Thanks for the assistance on this problem.

is your ubuntu 32-bit or 64-bit ?
if it's 32-bit and you have the sun-java6-plugin installed, then you must have somehow messed up the plugin
check /usr/lib/firefox/plugins and /usr/lib/mozilla/plugins folder, inside both should be a libjavaplugin.so file, see if that file is blocked, (some sort of symbol attached ) if that is the case I recommend to uninstall all java packages, use synaptic, choose complete removal and click apply, then look again in those two folders, if the libjavaplugin.so is still there, you must delete it, delete also the hidden .java folder if there is one on your home directory, then do a clean reinstall of the sun-java6-plugin.

if the plugin is okay, you can copy the  libjavaplugin.so file and paste on home/user/.mozilla/plugins folder, maybe firefox is looking for the plugin in the wrong folder, this way should work!

java version "1.6.0_03" is the version available in synaptic, it will not pass the java site test as there is a new version, but it'll work well on any site that uses java.

---

### Post by Menky on 2008-04-03
After looking at many threads about Java-plugin issues i ran this:

ls -l /etc/alternatives/firefox-javaplugin.so

mentor@mentoris-desktop:~$ ls -l /etc/alternatives/firefox-javaplugin.so

lrwxrwxrwx 1 root root 48 2008-04-03 00:48 /etc/alternatives/firefox-javaplugin.so -> /usr/lib/jvm/java-gcj/jre/lib/libgcjwebplugin.so

Apparently the java-gcj package was not helping and after i removed:


sudo aptitude remove java-gcj-compat

then I got:

mentor@mentoris-desktop:~$ ls -l /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root 64 2008-04-03 12:57 /etc/alternatives/firefox-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so


Now Java.com recognizes my latest version + facebook photo uploading works with Java + everything.

Hope that helps anyone

---

