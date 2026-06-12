---
title: "Java problem"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by djlysuc on 2006-12-02
Hi

Partypoker have recently released a play online option with no installation which is supported in Linux, I had a java not installed problem when I first went to the page but I installed what I thought was the correct java application and I don't get any message box but the browser window just hangs.

Does this work for anyone else? What do I need to do to get to to work for me?

[http://www.partypoker.com/anywhere/](http://www.partypoker.com/anywhere/)


Thanks for any help.

Andy

---

### Post by Perfect Storm on 2006-12-02
What do you get when typing this:
```
java -version
```

---

### Post by djlysuc on 2006-12-02
I get:

java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

---

### Post by Perfect Storm on 2006-12-02
Try with sun Java 1.5.xx

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

### Post by djlysuc on 2006-12-02
Fantastic, now working. Thanks Artificial Intelligence

For anyone following the above its jre update 10 now so you need to amend the code as appropiate.

---

