---
title: "Firefox Plugin Java Runtime Environment"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by Gyrotwister on 2006-07-15
Several times over the past couple of weeks I've attempted to install Java.  It's just not working for me.  I've followed a few different recipies and failed each time.  Now I'm beginning to wonder if I might have broken something.  

Can anyone point me towards the most common and reliable method of installing Java?

---

### Post by catlett on 2006-07-15
Make sure you have the extra repositories enabled. [http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)
Then issue this command ```
sudo apt-get install sun-java5-jre sun-java5-plugin
``` That is the easiest and surest way. It will install runtime 1.5 with update 6 and install the firefox plugin.
There is a way to update to uypdate 7 but first make sure it can install.

---

### Post by kenweill on 2006-07-15
[http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

---

### Post by Gyrotwister on 2006-07-15
I believe already I have all the extra repositories enabled.  
Here's what happens in terminal

```
r@Robert:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre
r@Robert:~$

```

Any suggestions?

---

### Post by adam.tropics on 2006-07-15
> **Gyrotwister said:**
> I believe already I have all the extra repositories enabled.  
Here's what happens in terminal

```
r@Robert:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre
r@Robert:~$

```

Any suggestions?

Worth checking your sources though, you need multiverse enabled.

---

### Post by catlett on 2006-07-15
Your missing the repository that holds the package. You can copy and paste Aysiu's list or enable the esxtra repos by the wiki method [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Gyrotwister on 2006-07-16
I thought I had already enabled all reporitories but when I checked just now they wheren't all ticked/checked.  
So using Synaptic I ticked all the boxes and then selected reload.  

this error message came up  

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg:](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg:) Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

What's causing this?

---

