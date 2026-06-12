---
title: "Java"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by i-am-me on 2007-02-28
I need (or actually want) to install Java on Kubuntu. I went to the download site:

[http://java.com/en/download/linux_manual.jsp]("http://java.com/en/download/linux_manual.jsp")

I really don't know which one to download and what to do afterwards.... Help?

---

### Post by FyreBrand on 2007-02-28
Sun's Java 6 is in the repositories and can be installed with apt-get.

Since you are using Edgy all you need to do is enable your multiverse repositories and then:
```
sudo apt-get update && sudo apt-get install sun-java6-bin sun-java6-plugin sun-java6-jdk
```This is will install the runtime environment (JRE), the browser plugin, and the Java Development Kit (JDK).  If you only need to run Java then only install the sun-java6-bin and the sun-java6-plugin.  Only install the sun-java6-jdk if you need to write and compile Java programs.

Once you have them installed you wanted to configure the system to use them instead of gcj (the default gnu java). So from the Konsole:
```
sudo update-java-alternatives -s java-6-sun
```
There you have it.  Java installed.  In Konqueror you might have to allow Java to be enabled in the settings.  Go to the Settings ->Configure Konqueror -> Java and enable Java with the checkbox if it isn't already checked.

---

### Post by GrantShoe on 2007-03-04
Do i have to be connected to the internet to run this?  I'm not.  in fact, i need jdk to compile a program to connect me to the university's network... anyways, when i run this on a fresh kubuntu install, it says:
> Couldn't find package sun-java6-bin

---

### Post by FyreBrand on 2007-03-04
Yes to connect to the repositories you must be connected to the internet.  You must also enable the multiverse repository.  If you would like to manually install Java there is a HowTo by phossal here: [**Installing Java**]("http://phossal.com/thread?view=702216931").

---

