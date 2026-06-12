---
title: "Frostwire and Java problem"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by RMorris78 on 2007-04-30
I am trying to run Frostwire... but i keep getting this error

Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

im pretty sure i install sun-jre6 and stuff though.... i think i might have accidentally declined a license... how can i fix this?

---

### Post by LuisGMarine on 2007-04-30
Seems like you didn't.  To check for the java version run this in a terminal,
```
java -version
```
You should get something along the lines of,
```
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

```

If you didn't then, that means that you didn't install the latest version of Java.  If you already have the extra repos, then just go ahead and run this command,
```
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
```
This should ask you to agree to the silence and stuff, so just say yes .. obviously :)

The next thing, is download the frost wire that is provided by their official website, not the ubuntu repo version.  If you have the ubunut repo version ( used synaptics or apt-get to install ) then go ahead and remove it.  A simple
```
sudo apt-get remove frostwire
```
Should do the the trick.

So head over to the frostwire website and download their Ubuntu Linux version and the package installs with synaptics on its own I believe.

Good Luck

-LuisGMarine

---

