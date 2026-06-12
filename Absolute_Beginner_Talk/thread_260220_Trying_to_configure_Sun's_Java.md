---
title: "Trying to configure Sun's Java"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by isleib on 2006-09-18
I installed sun's java as per [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

When I try to configure it as my default however, java-1.5.0-sun is not one of my choices...

```

isleib@isleib-laptop:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
*+    2        /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number:
```

Any ideas on why the sun alternative is not showing up?  Also, when I config jar, javac, javadoc, javah, javap and javaws the sun alternative is the selected choice, if not the only one.

Thanks

---

### Post by Perfect Storm on 2006-09-18
Try this one (you also get the latest and makes you a nice .deb file out of it):

Download Java Runtime Environment (JRE) 5.0 Update 8: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) pick **Linux self-extracting file**. Download it to your **Desktop**.

```
cd Desktop
sudo apt-get install build-essential
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_08-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update08_i386.deb
sudo update-alternatives --config java

```
When asking for which version you want to choose pick;
```
  3        /usr/lib/j2sdk1.5-sun/bin/java
```

Testing;
```
java -version
```


Making a Launcher for Java Control Center;
```
gksudo gedit /usr/share/applications/java.desktop
```

fill in;

[b]
[Desktop Entry]
Name=Java Control Center
Comment=Java Options & Configuration.
Exec=sh /usr/lib/j2re1.5-sun/bin/ControlPanel
Icon=
Terminal=false
Type=Application
Categories=Application;System;
[/b]

Save and exit.
You can find it now under Applications tab ---> System Tools.

---

### Post by isleib on 2006-09-18
Excellent that worked, Thanks!

---

### Post by moma on 2006-09-18
Re-run this command
$ [COLOR="Green"] sudo apt-get install --reinstall sun-java5-bin[/COLOR]

And your "/var/lib/dpkg/alternatives/java" file should be similar to this (with 3 java alternatives).

$ [COLOR="Green"]cat /var/lib/dpkg/alternatives/java[/COLOR]
```
manual
/usr/bin/java
java.1.gz
/usr/share/man/man1/java.1.gz

[COLOR="Indigo"]/usr/bin/gij-wrapper-4.1[/COLOR]
41
/usr/share/man/man1/gij-wrapper-4.1.1.gz
[COLOR="Indigo"]/usr/lib/jvm/java-gcj/jre/bin/java[/COLOR]
1041
/usr/lib/jvm/java-gcj/man/man1/java.1.gz
[COLOR="Indigo"]/usr/lib/jvm/java-1.5.0-sun/jre/bin/java[/COLOR]
53
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/man/man1/java.1.gz
```
Update-alternatives command reads that file.
--------------------------------------------------------------------

Alternatively, let Automatix script install support for Sun's Java.
Browse to this page: [http://www.futuredesktop.org/](http://www.futuredesktop.org/)
and look for step 5) "Finalization script".

---

