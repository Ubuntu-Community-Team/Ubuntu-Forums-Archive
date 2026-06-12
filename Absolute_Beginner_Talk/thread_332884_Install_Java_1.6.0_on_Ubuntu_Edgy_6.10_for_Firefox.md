---
title: "Install Java 1.6.0 on Ubuntu Edgy 6.10 for Firefox"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by vcrfix on 2007-01-06
1. Download the java version from java.sun.com to your Desktop (not as root)
2. Open a terminal window, change to the Desktop directory
3. enter the command chmod a+x jdk-6-linux-i586.bin
4. enter the command ./jdk-6-linux-i586.bin (will extract java to the jdk1.6.0 directory)
5. change as root via the su command
6. change to the /usr path
7. mkdir java (this path will most likely not exist so you will have to make it)
8. mv ~home/Desktop/jdk1.6.0 . (this move the jdk path to the current location under /usr/java
9. cd /usr/lib/mozilla/plugins
10. rm libjavaplugin_oji.so (remove any previous java plugin links)
11. cd /usr/lib/firefox/plugins
12 rm libjavaplugin_oji.so (remoce any previous java plugin links)
13 cd /usr/lib/mozilla-firefox/plugins
14 rm libjavaplugin_oji.so (remove any previous java plugin lins)

when removing these previous java plugin links, if the file does not exist before attempting to remove it, do not worry, you are just ahead.

15 cd ~home/.mozilla/plugins
16 ln -s /usr/java/jdk1.6.0/jre/plugin/i386/ns7/libjavaplugin_oji.so

now you have to created a new link to the newly installed java 1.6

17 close the firefox browser completely including the download window and any extras
18 now restart the firefox browser

19 navigate to a known site with a java applet, and should load with no problem

Hope these instructions help and are detailed enough.

---

