---
title: "Java help!"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by gatordoc on 2008-02-11
Hello all. I recently tried to upgrade my java and in doing so have messed it up royally
I am using Ubuntu GG 7.10 and firefox 2.0.

The problem started when I installed icedtea and i went to the test page (after rebooting to be safe) and it kept reading the blackhawk 1.4.2 and telling my my software was too old to use certain java applications. So I uninstalled icedtea thinking it didnt work, reinstalled, got same problem, uninstalled, installed sunjava6, same problem uninstalled and now i cannot install any java application because it fails to install. I try and use synaptic and its says I am need .jre in order for it to work, i check the .jre and it says i need the .bin to work..etc and none install at all.

what do i do to get it back to square 1 apart from redoing everything (everything apart from java is fine)

thanks all

---

### Post by drtre on 2008-02-11
try:
```
sudo apt-get install sun-java6-jre
```
post the result.

---

### Post by gatordoc on 2008-02-11
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jre set to manual installed.
The following packages were automatically installed and are no longer required:
  libfreebob0 libjack0 classpath-gtkpeer classpath-common cacao classpath
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.


[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by gatordoc on 2008-02-11
I typed in no <enter> and the following appeared:


Abort installation of JDK documentation
dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script returned error exit status 1
Setting up sun-java6-bin (6-03-0ubuntu2) ...
Error: could not open `/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/jvm.cfg'
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-03-0ubuntu2); however:
  Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on sun-java6-bin (= 6-03-0ubuntu2) | ia32-sun-java6-bin (= 6-03-0ubuntu2); however:
  Package sun-java6-bin is not configured yet.
  Package ia32-sun-java6-bin is not installed.
dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-jdk:
 sun-java6-jdk depends on sun-java6-jre (= 6-03-0ubuntu2); however:
  Package sun-java6-jre is not configured yet.
dpkg: error processing sun-java6-jdk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-fonts:
 sun-java6-fonts depends on sun-java6-jre (>= 6-03-0ubuntu2); however:
  Package sun-java6-jre is not configured yet.
dpkg: error processing sun-java6-fonts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-javadb:
 sun-java6-javadb depends on sun-java6-jdk (= 6-03-0ubuntu2); however:
  Package sun-java6-jdk is not configured yet.
dpkg: error processing sun-java6-javadb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-source:
 sun-java6-source depends on sun-java6-jdk (>= 6-03-0ubuntu2); however:
  Package sun-java6-jdk is not configured yet.
dpkg: error processing sun-java6-source (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-doc
 sun-java6-bin
 sun-java6-plugin
 sun-java6-jre
 sun-java6-jdk
 sun-java6-fonts
 sun-java6-javadb
 sun-java6-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by drtre on 2008-02-11
```
sudo update-alternatives --config java
```
make sure the jre you want is selected. then check out if it works.

---

### Post by Tyke91 on 2008-02-11
I've had this same problem before. for some reason, the javadoc stuff in synaptic doesn't work properly. if you're not a java programmer, you shouldn't need to have it.

to get your java running, go to synaptic and search java.

mark all of the ones shown in this screenie

[[IMG]http://img138.imageshack.us/img138/3365/screenshotci0.th.png[/IMG]](http://img138.imageshack.us/my.php?image=screenshotci0.png)

make sure that javadoc is NOT marked.

---

### Post by gatordoc on 2008-02-11
There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/gij-4.1
          3    /usr/bin/cacao
 +        4    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 4
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.


I next went to

[http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1)

to test my java and

The page should refresh and display your environment within 10-60 sec.
If it is taking longer, your browser may not be using the latest JRE or there is a problem with your installation. 

mine just kept refreshing with no change, also none of the plugins on these pages work even though I have installed them as well. When I click on the install plugin it tells me that its already installed and when i try the GCJwebplugin it says it cannont enable the universe?

thanks for helping, but no luck so far =)

---

### Post by Tyke91 on 2008-02-11
hehe, you ninja'd me

funny thing, i wound up re-installing ubuntu before I figured this out the first time :P we should really put this in bug report.

---

### Post by drtre on 2008-02-11
well i think i know what the problem is. first of all tell me you have 32-bit or 64-bit ubuntu?
if you have 64-bit ubuntu there is no firefox plugin in sun-java packages except java 1.4 which is pretty obsolete. so you should install iced tea 7 which provides the plugin but i dont know if it works fine or not. but if you have 32-bit ubuntu there should be no problem installing the plugin.
for the error it's becuz you have not enable the une repo. to do this go system>administration>synaptic package manger
and in settings menu click on repositories. and make sure all the repositories are checked in the ubuntu software tab.

---

### Post by gatordoc on 2008-02-11
I have 32Bit, I use this cpu for my work stuff mostly

I had all of this stuff installed at one point and now i cannot uninstall or install it (or reinstall) I have all the stuff checked in the synaptic manager.

I will try some of these other suggestions

---

### Post by gatordoc on 2008-02-11
java -version
java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory


I get this error when i am checking my version.

also I cannot install any plugins because the dependencies are all whacked even though synaptic says they are all installed.

right now, however, i went to a test page and it read that i was using 1.4.2 GNU version of java again... it wasnt even working before trying everything associated with this page...weird

---

### Post by drtre on 2008-02-11
why don't you just use synaptic and uncheck all those java stuffs? try checking .bin files it will remove dependencies too.

---

### Post by gatordoc on 2008-02-12
it wont let me reinstall anything anymore, or install. Thats been the problem. I think by uninstalling/reinstalling too many times trying to troubleshoot has caused some bad issues with java applications.

---

### Post by gimfred on 2008-03-19
gatordoc, I just found out (5 minutes ago) if you copy the archived file over and chown it, the package will install.
```
$ cp /the_folder(s)_you_downloaded_to/jdk-6-doc.zip /tmp
$ sudo chown root:root /tmp/jdk-6-doc

```
and the bloddy thing installs! Argh!

---

