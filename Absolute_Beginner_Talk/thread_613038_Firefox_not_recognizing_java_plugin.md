---
title: "Firefox not recognizing java plugin"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by steeny124 on 2007-11-14
I've been digging through the threads for a while on this one, and nothing's seeming to help.  There still may be something out there that addresses this, but I haven't been able to find it ( or at least one I can understand, seeing as I can be ubunstupid sometimes).  

Despite having installed and reinstalled sun java 6 on Gutsy 7.10, it doesn't seem like firefox OR the terminal is recognizing the java version when I write in the command  > java - version  I get this: 

> /# java - version
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

in addition to that, when I type about:plugins on firefox, java isn't recognized at all.  

I've read about making a symlink to point to the plugin, but I'm not sure how to do that.

---

### Post by TidusBlade on 2007-11-14
I think there was a package like Sun Java web start, try that if you didnt.

---

### Post by Inxsible on 2007-11-14
you have to install the mozilla plugin for Firefox to recognize java.
```
sudo apt-get install sun-java6-plugin
```also the command is with 2 dashes ```
java --version
```

---

### Post by Inxsible on 2007-11-14
> **TidusBlade said:**
> I think there was a package like Sun Java web start, try that if you didnt.Web start has nothing to do with the firefox plugin. Webstart also called JNLP, is a sun technology where in you can deploy and run java applications and applets without having to install the application in different machines. Simply accessing the jnlp file will download the app and install it in the java cache for you.

---

