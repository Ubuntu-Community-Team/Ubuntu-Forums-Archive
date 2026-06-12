---
title: "JAVA for frostwire"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Fittersman on 2006-10-23
frostwire seems to require java, help me out here cuz i cant find java for download. except at java.com but i odnt know what one is for me and im on ubuntu dapper

---

### Post by meng on 2006-10-23
Follow instructions here:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Fittersman on 2006-10-24
](*,) thats too hard, isnt there just a link to java download site (the one that is required for frostwire) that i can download from, click on it and say install?

---

### Post by canadianwriterman on 2006-10-24
It's not really as hard as it looks. Assuming you're using Dapper, just do this:

Go to the Applications -> Add/Remove... menu. Make sure to check the unsupported and proprietary software checkboxes. Install the j2re1.4 package.

---

### Post by strobi on 2006-10-24
Hoi,

Ik heb ook een probleem met java.Ik kan de java die ik gedownload heb niet in   de map /usr/java/ copieren vanaf de desktop.
Ik doe in de terminal cp /home/mark/desktop/java.....rpm.bin /usr/java/

Wat doe ik verkeerd??De map java kreeg ik wel gemaakt maar ik krijg java er niet in gekopierd om te installeren.

---

### Post by tronica on 2006-10-24
it doesn't get any easier than that.

[http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

---

### Post by Perfect Storm on 2006-10-24
or Installing java the "hard" way:


NB: (important) requires that you have universe/multiverse enable in your sourcelist.

Download Java Runtime Environment (JRE) 5.0 Update 9: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) pick **Linux self-extracting file**. Download it to your **Desktop**.

```
cd Desktop
sudo apt-get install build-essential
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_09-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update09_i386.deb
sudo update-alternatives --config java

```
When asking for which version you want to choose pick;
```
  3        /usr/lib/j2jre1.5-sun/bin/java
```

Testing;
```
java -version
```


Making a Launcher for Java Control Center;
```
sudo nano /usr/share/applications/java.desktop
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

Save and exit. <ctrl> + <o> | <ctrl> + <x>
You can find it now under Applications tab ---> System Tools.

---

### Post by Fittersman on 2006-10-24
thanks for all the help :D

and for that last comment what is fakeroot? the terminal thing said its not a command...?

---

### Post by blendmaster on 2006-10-24
Or the really easy way is through [automatix]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38")

It gives you several program options to decide what you want, including JRE.

---

