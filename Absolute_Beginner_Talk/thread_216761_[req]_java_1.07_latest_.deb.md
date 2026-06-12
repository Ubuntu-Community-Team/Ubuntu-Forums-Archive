---
title: "[req] java 1.07 latest .deb"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-07-16
any1 got the latest java in a .deb?? im making something that requires the user to have java in the same place so it will install this .deb then my program will run smooth so any got? i believe its something _07 for the latest

---

### Post by Perfect Storm on 2006-07-16
You can make your own if you want the latest 1.5 update 7


Download Java Runtime Environment (JRE) 5.0 Update 7: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) pick **Linux self-extracting file**. Download it to your **Desktop**.

```
cd Desktop
sudo apt-get install build-essential
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_07-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update07_i386.deb
sudo update-alternatives --config java

```
When asking for which version you want to choose pick;
```
  3        /usr/lib/j2re1.5-sun/bin/java
```

Testing;
```
java -version
```


Making a Launcher for Java Control Center;
```
sudo gedit /usr/share/applications/java.desktop
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

### Post by Ben Sprinkle on 2006-07-16
yer im just going to put the java folder mix it with my program then

cd folder

java the .class file

that should work?

itll make the whole thing heavier but i mean its not that big of a deal but ima try ur way

---

### Post by Ben Sprinkle on 2006-07-16
o btw im guesing this:

```

sudo dpkg -i sun-j2re1.5_1.5.0+update07_i386.deb

```

means depackaging it meaning installing but theres a .deb installer for ubuntu :O

---

