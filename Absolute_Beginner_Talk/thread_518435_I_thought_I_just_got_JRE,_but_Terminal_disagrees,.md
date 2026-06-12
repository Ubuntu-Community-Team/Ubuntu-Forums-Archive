---
title: "I thought I just got JRE, but Terminal disagrees,"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-08-05
Hey folks. I just did a custom install of Dapper, and thought that I had installed Java. I installed Frostwire afterward, and tried to run it. It didn't initiate, so I tried through Terminal. In that, it told me that I need to install JRE 1.5 or higher. I'm not sure what I missed, but if someone could simply give me the command to apt-install, I'd be well on my way. I tried looking for it, but I only ever find trouble-shooting subjects, and not the original d/l commands. 
Thanks a lot.

---

### Post by alienexplorers on 2007-08-05
I downloaded JRE from the java site.  You need the Linux version of the download.  It is a bin file and there are directions on that site and in the forums on how to load it.

---

### Post by talby on 2007-08-05
I assume you installed java similiar to [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Java_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox")?
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```
I have not tried frostwire but some java apps need the java config set so try this:
```
sudo update-alternatives --config java
``` and select the one you installed.

---

