---
title: "32 bit java needed for 64 bit gutsy"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by darthshak on 2008-01-09
Hi

       I have a 64 bit version of Gutsy Gibbon installed on my laptop. Unfortunately, the applications I work with require 32 bit java. Firstly, I uninstalled the 64 bit version of firefox and replaced it with a 32 bit version which worked FINE. 

Next, I needed to download the java plugin for firefox. For this, I visited the Sun website and downloaded the 32 bit package( I had to do this as only the 32 bit version had Java Web Start and Java applet supported). When I downloaded and installed the package according to instructions, none of the sites using java applets worked. 

How do I make 32 bit java work on 64-bit Gutsy?

---

### Post by Perfect Storm on 2008-01-09
There is java 32 bit in the repo, so there's no need to install java from their homepage.

---

### Post by dcstar on 2008-01-09
> **darthshak said:**
> Hi

       I have a 64 bit version of Gutsy Gibbon installed on my laptop. Unfortunately, the applications I work with require 32 bit java. Firstly, I uninstalled the 64 bit version of firefox and replaced it with a 32 bit version which worked FINE. 

Next, I needed to download the java plugin for firefox. For this, I visited the Sun website and downloaded the 32 bit package( I had to do this as only the 32 bit version had Java Web Start and Java applet supported). When I downloaded and installed the package according to instructions, none of the sites using java applets worked. 

How do I make 32 bit java work on 64-bit Gutsy?

I use the IcedTea java package quite successfully in Firefox.

---

### Post by darthshak on 2008-01-10
ok.....so i 'installed' sun-java6-jre from the repository.

When i typed java -version, this is what i got : 

The program 'java' can be found in the following packages:
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * java-gcj-compat
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found

However, I did an external download of the browser plugin and that got working (used the 
following link : [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537))

Somebody PLEASE help as I have a programming contest up next week and I really need 32 bit java for my programs...

---

### Post by Perfect Storm on 2008-01-10
You can reconfigure which java the system shall use as default:

```
sudo update-alternatives --config java
```

But first you need to install

ia32-sun-java6-bin

---

