---
title: "Manual Install"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by wtomh on 2006-07-26
I am trying to install Java as per the instructions on the firefox-addon tab download page. I download Java to my desk top.
I go to the terminal, type in "su" press enter. I put in my password and get the following message, "su: Authentication failure. sorry: What do I need to do?

---

### Post by Kobalt on 2006-07-26
Try to use "sudo" instead of "su"...

---

### Post by Perfect Storm on 2006-07-26
[http://ubuntuforums.org/showpost.php?p=1231275&postcount=5](http://ubuntuforums.org/showpost.php?p=1231275&postcount=5)

The easist way, but it's one version behind; enable multiverse in your sourcelist:
```
sudo nano /etc/apt/sources.list
```
Uncomment the lines which aren't uncomment. Save and exit.
```
sudo apt-get update
sudo apt-get install sun-java5-jre
sudo update-alternatives --config java
```

Pick:   3        /usr/lib/j2sdk1.5-sun/bin/java

```
java -version
```

Ubuntu don't use su but sudo.

---

### Post by T700 on 2006-07-26
If you have no luck doing it manually, try the Automatix link in my sig.  It will install Java, the plugins, and various codecs for you.

Paul

---

