---
title: "Java Applet"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Dragonlaw on 2008-04-05
I just installed the Sun Java 6 on Ubuntu and cannot open this website. I have been trying to install and reinstall everything. PLEASE HELP!

The website is below:
[https://internet-banking.dbs.com.sg/IB/Welcome](https://internet-banking.dbs.com.sg/IB/Welcome)

---

### Post by spiderbatdad on 2008-04-05
See the second post in this thread please: [http://ubuntuforums.org/showthread.php?t=742715](http://ubuntuforums.org/showthread.php?t=742715)

---

### Post by PointyWombat on 2008-04-05
Test java out here:

[http://www.java.com/en/download/help/testvm.xml]("http://www.java.com/en/download/help/testvm.xml")

What version does it say your browser is using?

---

### Post by Dragonlaw on 2008-04-05
Version 1.4.2

Which installer do I upgrade to?

Linux RPM (self-extracting file) filesize: 18.32 MB 	
Linux (self-extracting file) filesize: 18.83 MB 	
Linux x64 * filesize: 17.50 MB 
Linux x64 RPM

Java's free download website gives these 4. Which do I upgrade to?

---

### Post by spiderbatdad on 2008-04-05
I don't believe you need to upgrade java...just copy and paste the code (one command at a time) from my previous post to create the necessary symbolic link.

---

### Post by Dragonlaw on 2008-04-05
I'm really sorry about the trouble.

spiderbatdad the terminal says this after I type the first command it:

can't read /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so: No such file or directory

---

### Post by Dragonlaw on 2008-04-05
Thank you everyone for your help. I managed to find out the solution already from [http://ubuntuforums.org/showthread.php?p=4656212#post4656212](http://ubuntuforums.org/showthread.php?p=4656212#post4656212)

> **cinematography said:**
> type this to install the plugin:
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

and enter this to remove the plugin that conflicts with the java plugin
```
sudo apt-get remove gcjwebplugin
```

Could I ask what exactly was the problem? I could type that in but I still don't really understand what I typed.

---

