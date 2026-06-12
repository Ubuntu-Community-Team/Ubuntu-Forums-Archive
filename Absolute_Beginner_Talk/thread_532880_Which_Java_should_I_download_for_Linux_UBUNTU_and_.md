---
title: "Which Java should I download for Linux UBUNTU and how do I install ?"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by HaemoLacria on 2007-08-23
[http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp) From these

Can somebody explain how to install Java? Im completely new to Ubuntu

---

### Post by gashcrumb on 2007-08-23
The easiest way would be:

sudo apt-get install sun-java6-jdk sun-java6-plugin sun-java6-fonts sun-java6-jre

assuming you want both the JRE and JDK.  You can download the self-extracting script from java.sun.com, but when you run it it'll be extracted in the current directory, you'd need to manually add it to your PATH/LD_LIBRARY_PATH etc.  Using the packages in Ubuntu's apt repository is a little nicer, as it'll set up symlinks in /usr/bin for you.

The actual JVM is installed into /usr/lib/jvm

---

### Post by jspangler on 2007-08-23
To use the plugin with firefox, you need to create a symlink in the firefox directory with:

```
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins
```

and make sure java is enabled in firefox.

---

### Post by gashcrumb on 2007-08-23
This step should be done already by "apt" as part of installing sun-java6-plugin.  The easiest way to tell is to do "ls -la /etc/alternatives | grep javaplugin", should show up like:

firefox-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

as /usr/lib/firefox/plugins/libjavaplugin.so should point to the soft link in /etc/alternatives:

ls -la /usr/lib/firefox/plugins/

shows:

libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

---

### Post by jspangler on 2007-08-23
And to think I've been wasting my time with an extra command! OK, good to know :)

---

### Post by gashcrumb on 2007-08-23
Heh heh, no problem!

---

### Post by sailor2001 on 2007-08-23
sun-java 6 et al is in synaptics.

---

### Post by HaemoLacria on 2007-08-29
Ok, but which one should I pick of this list. Im using ubuntu

---

### Post by gashcrumb on 2007-08-29
I'd install sun-java6-bin, sun-java6-fonts, sun-java6-jre and sun-java6-plugin at least, if you're looking to do java development also install sun-java6-jdk, sun-java6-source and maybe sun-java6-demo to get the demos...

---

### Post by HaemoLacria on 2007-08-29
But the site doesn't says that it runs on Ubuntu only on other Linux platforms. Or do you have a link ?

---

### Post by russell.h on 2007-08-29
Read the posts above, don't download it from Sun's Java site, use the command line (or the graphical package manager if you prefer, but the command line is easier) and just copy and paste the command he gave you.

Edit:
In other words, open a command prompt (Its something like Applications > Accessories > Command Prompt), and enter:
```
sudo apt-get install sun-java6-jdk sun-java6-plugin sun-java6-fonts sun-java6-jre
```
You will be prompted for your password, so type that in, press enter, and wait for stuff to stop happening. Then it is installed.

Edit 2:
Do non-free repos have to be enabled for that to work?

---

### Post by por100pre1 on 2007-08-29
> **russell.h said:**
> Read the posts above, don't download it from Sun's Java site, use the command line (or the graphical package manager if you prefer, but the command line is easier) and just copy and paste the command he gave you.

Agree, read the posted answers, it will be better and easier if you do so.

---

