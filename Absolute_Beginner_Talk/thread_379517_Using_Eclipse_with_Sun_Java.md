---
title: "Using Eclipse with Sun Java"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-03-08
I would like to use Eclipse with Sun's latest JDK release, (1.6.0).
If I use the instructions as seen here: [http://phossal.com/thread?view=702216931](http://phossal.com/thread?view=702216931), will Eclipse use it automatically? Will all other applications that use java, use it automatically?

---

### Post by phossal on 2007-03-08
I'm biased, but I think so. ;) If you haven't made any major configuration changes, those instructions typically work. Besides, if you find yourself in trouble, helping you out of it is something I'm willing to do. 

Regards.

---

### Post by FesterHead on 2007-03-08
The following phossal.com articles worked well for me to get Eclipse and Sun's Java playing together nicely:

Installing Java's JDK on Ubuntu Edgy
[http://phossal.com/thread?view=702216931](http://phossal.com/thread?view=702216931)

Installing eclipse IDE on Ubuntu Edgy
[http://phossal.com/thread?view=702216932](http://phossal.com/thread?view=702216932)

---

### Post by noorez on 2007-03-10
I also found a tutorial on this website for installing java. What would be the difference from the ones you have me and this one?
[http://blog.agileware.net/index.php/archives/2005/09/30/how-to-install-java-on-ubuntu-linux/](http://blog.agileware.net/index.php/archives/2005/09/30/how-to-install-java-on-ubuntu-linux/)

---

### Post by phossal on 2007-03-10
Using Sun's .bin file is the fastest, easiest, most direct option. I only viewed the link you posted briefly, but it appears the other would have you build a package first. That's just an unnecessary step.

---

### Post by noorez on 2007-03-10
I tried the manual way (the one with update-alternatives) and it all seems to be working. But I was wondering if I could have an explanation of what each command is doing. The man entries don't seem to give much of an explanation.

sudo update-alternatives --install /usr/bin/java java /usr/lib/Java6/bin/java 300
sudo update-alternatives --auto java

and with eclipse:

sudo ln -s /usr/lib/eclipse/eclipse /usr/bin/eclipse 
sudo ln -s /usr/lib/eclipse/startup.jar /usr/bin/startup.jar

---

### Post by phossal on 2007-03-10
> **noorez said:**
> sudo update-alternatives --install /usr/bin/java java /usr/lib/Java6/bin/java 300 **[COLOR="RoyalBlue"]#1[/COLOR]**
sudo update-alternatives --auto java **[COLOR="RoyalBlue"]#2[/COLOR]**

and with eclipse:

sudo ln -s /usr/lib/eclipse/eclipse /usr/bin/eclipse **[COLOR="RoyalBlue"]#3[/COLOR]**
sudo ln -s /usr/lib/eclipse/startup.jar /usr/bin/startup.jar **[COLOR="RoyalBlue"]#4[/COLOR]**


Overview: update-alternatives is a system for managing symbolic links. Here is the man information:

>        update-alternatives  creates,  removes, maintains and displays informa&#8208;
       tion about the symbolic links comprising the Debian  alternatives  sys&#8208;
       tem.

       It  is  possible  for  several  programs fulfilling the same or similar
       functions to be installed on a single system at  the  same  time.   For
       example,  many  systems  have  several  text editors installed at once.
       This gives choice to the users of a system, allowing each to use a dif&#8208;
       ferent editor, if desired, but makes it difficult for a program to make
       a good choice of editor to invoke if the user has not specified a  par&#8208;
       ticular preference.

       Debian&#8217;s  alternatives  system  aims  to solve this problem.  A generic
       name in the filesystem is shared by all files providing interchangeable
       functionality.   The  alternatives  system and the system administrator
       together determine which actual file  is  referenced  by  this  generic
       name.

**[COLOR="RoyalBlue"]#1[/COLOR]** Installs a symbolic link at /usr/bin/java referenced by the command name "Java" that points to /usr/lib/Java6/bin/java. It sets the priority to 300.
**[COLOR="RoyalBlue"]#2[/COLOR]** Sets the status of links to "java" managed by update-alternatives to auto, meaning that it will use the one with the highest priority, rather than one selected by the user. (The high priority of 300 assures it will choose the one we want).
**[COLOR="RoyalBlue"]#3[/COLOR]** Creates a symbolic link from the *eclipse* startup script to /usr/bin, so that we can launch eclipse from the menu or command line. An alternative would be adding our new eclipse folder to our PATH environment variable.
**[COLOR="RoyalBlue"]#4[/COLOR]** Creates a symbolic link to the startup.jar, which is called by the startup script.

---

### Post by noorez on 2007-03-10
It seems that
 sudo ln -s /usr/lib/Java6/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins 

did not add the plugin to firefox properly, as know when I go to an applet website, firefox  freezes

---

### Post by phossal on 2007-03-10
Are you using something like Beryl, or 64bit Ubuntu? Maybe you need to try Edit -> Preferences -> Enable Java from within Firefox? Have you restarted, or restarted Firefox? 

I'm not 100% convinced that anything works 100% of the time on Ubuntu. My *method* of installing Java may not use a package, but the way Firefox interacts with Java is pretty straight-forward. Perhaps you're using a 64bit browser or something? Otherwise, I can't think of reason it wouldn't work.

---

