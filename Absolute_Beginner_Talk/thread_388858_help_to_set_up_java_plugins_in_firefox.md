---
title: "help to set up java plugins in firefox?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by zyx on 2007-03-20
Hi, there,

I use kubuntu 6.10. I download a jre-1_5_0_11-linux-amd64.bin from [http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com)

cp jre-1_5_0_11-linux-amd64.bin /usr/java
cd /usr/java
sudo chmod a+x jre-1_5_0_11-linux-amd64.bin
sudo ./jre-1_5_0_11-linux-amd64.bin
sudo chown -R root:root /usr/java/jre1.5.0_11/
sudo ln -fs /usr/java/jre1.5.0_11/bin/java /usr/bin/java
sudo ln -fs /usr/java/jre1.5.0_11/bin/java_vm /usr/bin/java_vm                                             

however, I do not find file of libjavaplugin_oji.so and /usr/java/jre1.5.0_11/plugin/

What wrong about it?

---

### Post by zvacet on 2007-03-20
Look in usr/lib/mozilla and if you did it right it is there.

---

### Post by Efwis on 2007-03-20
you can also make sure it is working by opening Firefox and typing  about: plugins  (remove the space between the colon and "P". Had to do it this way so you could actually see the command without a smiley.) in the address bar, This will help you determine if the plugin for Firefox is recognized by Firefox. if it is listed there, then you shouldn't have to worry anymore about it.

---

### Post by zyx on 2007-03-20
java plugin does not work! I check the firefox plugins! Any clue? Thanks!

---

### Post by scxtt on 2007-03-20
something tells me that the package you used doesn't contain the plugin ... 

do: **sudo slocate -u**
then: **slocate libjavaplugin_oji.so**

and see if it's even on your system ...

if you don't absolutely need the latest version, i'd just install it from the repos ...

**sudo aptitude install sun-java5-bin sun-java5-jre sun-java5-plugin**

do that, then make a symbolic link in your ~/.mozilla/plugins to libjavaplugin_oji.so

---

### Post by Efwis on 2007-03-20
This is what I found in the wiki regarding this issue.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) 

> As of 2007-01-19, there is only one plugin that works and that is the one included with Blackdown Java 1.4.2 (see above for install instructions). Neither sun-java5-bin nor the recently released Sun Java 1.6 (Mustang), available from sun.com, contain a browser plugin for amd64. To get later versions of Java working with Firefox on amd64, you need to install the 32-bit version of Firefox and run 32-bit Java 1.5 or 1.6.

It appears you need to install the 32 bit version of java to have your plugins for Firefox with Sun java. I guess that is why they posted this on the download page you referenced in your first post.

> NOTE:
Linux x64 download: Please use the 32-bit version for Java applet and Java Web Start support.  These are your plugins!!!

---

### Post by zyx on 2007-03-20
when I set up sun-java5-bin sun-java5-jre sun-java5-plugin, I got the error as follows:

sudo dpkg --configure -a
sudo aptitude install sun-java5-bin sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
No candidate version found for sun-java5-plugin
The following NEW packages will be installed:
  sun-java5-bin sun-java5-jre
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/27.4MB of archives. After unpacking 76.7MB will be used.
Writing extended state information... Done
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
(Reading database ... 135020 files and directories currently installed.)
Unpacking sun-java5-bin (from .../sun-java5-bin_1.5.0-08-0ubuntu1_amd64.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: error processing /var/cache/apt/archives/sun-java5-bin_1.5.0-08-0ubuntu1_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Unpacking sun-java5-jre (from .../sun-java5-jre_1.5.0-08-0ubuntu1_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: error processing /var/cache/apt/archives/sun-java5-jre_1.5.0-08-0ubuntu1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java5-bin_1.5.0-08-0ubuntu1_amd64.deb
 /var/cache/apt/archives/sun-java5-jre_1.5.0-08-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

How to unlock config.dat? Thanks!

---

### Post by txhellkat138 on 2007-03-20
Easiest way I have found to get java running is right there in the kde or gnome menu's CLick on add remove. Make sure to selectr unsupported and proprietary for any platform. in the search box type in java. you should see java1.4 and java 1.4 mozilla plugin click it hit apply bam java 5 mins after install

---

### Post by scxtt on 2007-03-20
zyx, looks like you've got some other package management tool locking the database ... make sure you're not in synaptic or using some other update tool ...

i installed those 3 packages (no java before that) then made a symbolic link to the *_oji file and was good to go :)

---

