---
title: "JAVA -- jive"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-11-07
I don't get it.

I've asked both Automatix and EasyUbuntu to install Java. Ah! those were separate install of ubuntu. On the same hdd however.

Both report Java as installed.

EasyUbuntu even added 

Sun Java Plugin Control Panel

and

Sun Java Policy Tool 

into System/Preferences.

But when I surf over to: [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

I learn that my Java ain't working.

I've seen numerous posts about Java/Ubuntu. What gives? Why is this so crushingly difficult in Linux?

Do I now have to sudo apt-get remove java? and start over?

---

### Post by catlett on 2006-11-07
First try running the update alternative to see if it is installed and maybe it isn't chosen as your java app
```
sudo update-alternatives --config java
```
Java is also in the repositories. I don't remember if you need to enable extra repositories but if you have automatix's repository list, then you will have the extra repositories. In that case enter this if the update alternative doesn't work, enter this in the terminal to get java and the firefox plugin.
```
sudo apt-get install sun-java5-jre sun-java5-plugin
```
If you want update 9, the edgy guide has a how to (as well as the command I just gave you) The edgy guide has all the apps and the commands you need if automatix isn't wqorking for you. [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

---

### Post by Mark_in_Hollywood on 2006-11-08
Following your instruction

sudo update-alternatives --config java

returned:

mark@Lexington:~$ sudo update-alternatives --config java
Password:

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
*     3        /usr/local/jre1.5.0_06/bin/java
      4        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:

What does the + mean? It's available? Which do I chose?

Sorry to be such a noob, but I'm lost.

---

### Post by catlett on 2006-11-08
I've never seen the + sign before but I just ran the command again and I got this 
```
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
 +        2    /usr/lib/j2re1.5-sun/bin/java
*         3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
```
Seeing this, I would assume the + means the version I am using and the * is the default choice. Meaning (I think) you are using + but * is the default chjoice.
What does this mean to you? You have java installed but I would bet, you don't have the java plugin installed for firefox so when you go to the java site to verify it says 'not installed' because it isn't installed in your browser.
Try installing the java plugin and then go to the site for verification.
```
sudo apt-get install sun-java5-plugin
```I always installed the browser plugin at the same time I installed java so I don't know if the plugin needs the java package from the package manager. If you get a dependency type of error, run it again with the command to install java 
```
sudo apt-get install sun-java5-jre sun-java5-plugin
``` Then check the website. Remember to close firefox and restart it after installing. I doubt you will have to reboot but you may have to.

---

