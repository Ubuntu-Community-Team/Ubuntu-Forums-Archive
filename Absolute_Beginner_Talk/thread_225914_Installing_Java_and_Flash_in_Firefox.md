---
title: "Installing Java and Flash in Firefox"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by mikesena on 2006-07-30
Hi,

I am having problems installing Java and flash (these are the only two plugins I have tested).  Using the guide at ubuntuguide.org, I tried to install the firefox plugins, but I got this error:
```
meo@meo-laptop:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre
meo@meo-laptop:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
```
Does anyone know why this is happening and how I can fix it?  I am a complete linux n00b, but Windows is 100% gone now and I have to learn ;)


Other notes that may help:
   Ubuntu 6.0.6
   Firefox 1.5.0.5
   All installed extensions are up-to-date
   Other than a couple games, I have not installed anything extra.  My installation is fresh off the CD
   When I ran the command, Ubuntu Updater was not running.
   I tried with both firefox running and firefox not.


Thanks,
mEo

PS.  On a complete side note, what's the best DVD player for Ubuntu? :P

---

### Post by Perfect Storm on 2006-07-30
Did you set up your sourcelist as explained on ubuntuguide.org?

---

### Post by mikesena on 2006-07-30
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

Is that the section?

I used the source-o-matic for Hong Kong, generated a list, replaced it, updated it and it downloaded a couple of things (good sign).

However, when I went back to the guide, I saw the Easy Ubuntu tool, which I followed the instructions for and it seems to now be downloading (And then presumably) installing flash, java and a couple of other things.

---

### Post by Perfect Storm on 2006-07-30
okay, just report back if you have it working.

---

### Post by mikesena on 2006-07-30
The Easy Ubuntu worked, so I now have flash and java in Firefox :)

---

