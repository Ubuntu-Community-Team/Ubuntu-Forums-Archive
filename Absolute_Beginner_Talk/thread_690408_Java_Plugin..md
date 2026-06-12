---
title: "Java Plugin."
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by SusieSA on 2008-02-07
Hi

I am trying to get Java to work and I have installed the files, but I don't seem to have a plugin directory.

Previous posts said that I should:

cd ~/.mozilla/plugins

I can see the .mozilla directory, but I do not have the plugins directory.

When I try "aboutlugins" in the address line, the java stuff looks like this:

Description Suffixes Enabled
application/x-java-vm Java Yes
application/x-java-applet Java Yes
application/x-java-applet;version=1.1 Java Yes
application/x-java-applet;version=1.1.1 Java Yes
application/x-java-applet;version=1.1.2 Java Yes
application/x-java-applet;version=1.1.3 Java Yes
application/x-java-applet;version=1.2 Java Yes
application/x-java-applet;version=1.2.1 Java Yes
application/x-java-applet;version=1.2.2 Java Yes
application/x-java-applet;version=1.3 Java Yes
application/x-java-applet;version=1.3.1 Java Yes
application/x-java-applet;version=1.4 Java Yes
application/x-java-applet;version=1.4.1 Java Yes
application/x-java-applet;version=1.4.2 Java Yes
application/x-java-applet;version=1.5 Java Yes
application/x-java-applet;version=1.6 Java Yes
application/x-java-applet;jpi-version=1.6.0_03 Java Yes
application/x-java-bean Java Yes
application/x-java-bean;version=1.1 Java Yes
application/x-java-bean;version=1.1.1 Java Yes
application/x-java-bean;version=1.1.2 Java Yes
application/x-java-bean;version=1.1.3 Java Yes
application/x-java-bean;version=1.2 Java Yes
application/x-java-bean;version=1.2.1 Java Yes
application/x-java-bean;version=1.2.2 Java Yes
application/x-java-bean;version=1.3 Java Yes
application/x-java-bean;version=1.3.1 Java Yes
application/x-java-bean;version=1.4 Java Yes
application/x-java-bean;version=1.4.1 Java Yes
application/x-java-bean;version=1.4.2 Java Yes
application/x-java-bean;version=1.5 Java Yes
application/x-java-bean;version=1.6 Java Yes
application/x-java-bean;jpi-version=1.6.0_03 Java Yes

Nothing much about Java 6. What am I doing wrong?

Thanks.

---

### Post by FuturePilot on 2008-02-07
Did you install Java from the repos? The easiest way is to
```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin sun-java6-fonts
```

---

### Post by jrib on 2008-02-07
All you need to do is install the **sun-java6-plugin** package from the Mulitverse repository as explained in [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) .  I'm not sure what you meant by "I have installed the files" and why you are looking for ~/.mozilla/plugins.  Does that work for you?

---

### Post by SusieSA on 2008-02-07
Hi

OK - I did the sudo apt-get install* command and it said that the latest versions were already installed (except for the fonts).  But I'm still not having any success with running the plugin.

I'm trying to access a Bridge (card game) website that requires that I have a Java plugin installed and I just cannot open the window that needs the plugin - it gives me an error.

Also, if I go to the [www.java.com](www.java.com) site and follow the links to verify my intallation, I get the error message "Oops! You don't have the recommended Java installed."

What am I doing wrong?

Thank you!

---

### Post by FuturePilot on 2008-02-07
Try this
```
sudo update-alternatives --config java
```
Select Java6 from the list that appears.

---

### Post by koldphlame on 2008-02-07
i am running gusty and all i did was app->add/remove->    Then type in JAVA


AND PRESTO I HAD IT

:)

---

### Post by jrib on 2008-02-07
> **SusieSA said:**
> Hi
What am I doing wrong?


paste the result of this command:
```
ls -l /usr/lib/firefox/plugins
```

It may be that you have gcjwebplugin installed and need to remove it.  This command will tell us if that is the case.

---

### Post by SusieSA on 2008-02-07
I think you may be on to something Jason...  it's still not working and I've tried all the above, but there is a mention of libgcjwebplugin here - do I need to get rid of it?  how?



 ls -l /usr/lib/firefox/plugins
total 12
lrwxrwxrwx 1 root root   37 2008-01-31 14:37 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root   34 2008-02-05 18:02 libgcjwebplugin.so -> ../../classpath/libgcjwebplugin.so
lrwxrwxrwx 1 root root   39 2008-02-07 19:05 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root   36 2008-01-16 12:18 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   37 2008-01-16 12:18 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root   34 2008-01-16 12:18 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   35 2008-01-16 12:18 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root   36 2008-01-16 12:18 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   37 2008-01-16 12:18 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root   42 2008-01-16 12:18 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root   43 2008-01-16 12:18 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 9104 2007-12-04 13:01 libunixprintplugin.so

---

### Post by SusieSA on 2008-02-07
One of the other posts talked about doing the following...

/usr/lib/firefox/plugins$ ln -s /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so

I don't really understand why I'd want to do this, but I can't do it anyway because it says Permission Denied.  Could this be related to my problem?

---

### Post by FuturePilot on 2008-02-07
Did you run
```
sudo update-alternatives --config java
```
?

---

### Post by SusieSA on 2008-02-07
yes I did:

sudo update-alternatives --config java:

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/bin/cacao
          4    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 


Seems like I have a lot of Java installed (been at it for HOURS!!)

---

### Post by jrib on 2008-02-07
> **SusieSA said:**
> I think you may be on to something Jason...  it's still not working and I've tried all the above, but there is a mention of libgcjwebplugin here - do I need to get rid of it?  how?



 ls -l /usr/lib/firefox/plugins
total 12
lrwxrwxrwx 1 root root   37 2008-01-31 14:37 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root   34 2008-02-05 18:02 libgcjwebplugin.so -> ../../classpath/libgcjwebplugin.so
lrwxrwxrwx 1 root root   39 2008-02-07 19:05 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root   36 2008-01-16 12:18 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   37 2008-01-16 12:18 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root   34 2008-01-16 12:18 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   35 2008-01-16 12:18 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root   36 2008-01-16 12:18 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   37 2008-01-16 12:18 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root   42 2008-01-16 12:18 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root   43 2008-01-16 12:18 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 9104 2007-12-04 13:01 libunixprintplugin.so


do: 
```
sudo apt-get remove gcjwebplugin
``` and restart firefox

---

### Post by SusieSA on 2008-02-07
_jason - Will You Marry Me?????????!!!!!!!!!!!!!!

---

