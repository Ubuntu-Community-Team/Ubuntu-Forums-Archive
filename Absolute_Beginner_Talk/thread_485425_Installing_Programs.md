---
title: "Installing Programs"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by GLSmyth on 2007-06-26
One website I have frequented in the past uses Java.  i downloaded and opened it (jre-6u1-linux-i586-rpm.bin), but it appears that the system thinks that it is a text file since it is trying to open it with an editor (gedit).

How do I install Java?  Any help would be appreciated.

Cheers -

george

---

### Post by Nekiruhs on 2007-06-26
Dont download RPM files. Those are for a different package manager, (Red hat Package Manager, hence RPM).
Just open Synaptic, and search for Java and download it there. The best place to get software from the the repositories.

---

### Post by FleetAdmiral74 on 2007-06-26
Do a quick google search on installing java in ubuntu, since sometimes the repos don't completely cover it. Most of the time it works fine though.

---

### Post by wormser on 2007-06-26
You can install Java from Synaptic or from the command line.

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by ramjet_1953 on 2007-06-26
Thius link should help you:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox)

Thie whole document is the Bible for Ubuntu and should be able to help you with almost any issue.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Regards,
Roger :cool:

---

### Post by GLSmyth on 2007-06-27
> **Nekiruhs said:**
> Dont download RPM files. Those are for a different package manager, (Red hat Package Manager, hence RPM).
Just open Synaptic, and search for Java and download it there. The best place to get software from the the repositories.

Thank you for the responses.  I looked in Synaptic and it selected 134 packages.  Some of them are already installed but I'm not sure which one to select.  In looking at the descriptions it looks like bsh should be the right one, but it is already installed.  Do I just start installing packages until the program I am running works?  Is there a rule of thumb for doing this?

I looked at the link to the starting guide and, as mentioned in a response, tried entering:
  sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

Unfortunately, the response I got was:
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  E: Couldn't find package sun-java6-jre

I am guessing that I need to install something before running that command but am not sure what that might be.  I tried looking for sun-java6-jre in Synaptic without any luck.

Cheers -

george

---

