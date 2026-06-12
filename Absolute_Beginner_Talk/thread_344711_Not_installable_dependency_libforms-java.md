---
title: "Not installable dependency? libforms-java"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Khepri on 2007-01-23
Hi. First time here...hope this is the correct forum...

I'm trying to install Freemind Mind Mapper via Synaptic as Synaptic I am somewhat comfortable with from using Debian with KDE installed...

When I OK the dependencies to be installed it returns this message...


freemind:
 Depends: libforms-java  but it is not installable

My question is; what is the best way to resolve this? Actually, how do I resolve this?

Am I correct in assuming that it is not installable because of a conflict with another dependency or package? If so, how do I determine what that is so I can decide if I need it or not?

I would try to install it "manually" but I'd rather use the package manager...

Thanks for any pointers and or help...

Oh...p.s.

Freemind is java based and I managed to get the blackdown version of java installed by searching these forums....and the freemind people seem to indicate they prefer teh balckdown version as well....but java -version indicates I have 1.4.2.x something or other installed....shouldn't that be 1.5.0.6 or 1.5.0.10 version of java 2?

---

### Post by mikewhatever on 2007-01-23
I think it should be 1.5.0_08. See this thread for more [http://www.ubuntuforums.org/showthread.php?t=343951](http://www.ubuntuforums.org/showthread.php?t=343951)

---

### Post by Khepri on 2007-01-23
Ah thanks...I did choose the more recent version ....

and now java -version shows;

java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

I re-ran Synaptic but I still get the same message about the dependency being uninstallable...bummer...

Thanks for trying though! :)

---

### Post by Khepri on 2007-01-23
[http://siliconchaos.blogspot.com/2006/05/setting-up-freemind-in-ubuntu-dapper.html](http://siliconchaos.blogspot.com/2006/05/setting-up-freemind-in-ubuntu-dapper.html)

Followed the instructions above on my Dapper install and it worked beau-TI-ful...:p 

I used synaptic instead of wajig or apt-get....

Downloaded the packages from their sourceforge site...

Used dpkg as instructed....fairly smooth...

Toward the end we are told to update the menus with "update-menus"....my install of Dapper did not have this command...supposedly it would put the link to the program in the Office Apps menu....not a biggie...

I used update-manager and it would not update the SVG plugin....the results of that remain to be seen as I've not used that feature yet...


I wanted Freemind because it is cross-platform being java-based....I have a quad-boot system...(glutton for punishment)...and I wanted to be able to use the same MM file not matter what OS I use....

All for naught as Freemind will not open a file on a network...:(

Perhaps in the fututre....

All in all...very cool that help was out there....

UPDATE;

I have a minor workaround for Freemind not opening a file on a network drive.....I used the File Browser to navigate to the FAT32 partiton where the MM file is kept...(that's the extention Freemind uses)....and right-clicked on the file and told it to open the file with Freemind...worked fine.

Also, I wanted to add that I wanted Freemind because it will launch executable files locally (think shell scripts.>;)....open local files...or link to and open files on the Net....just awesome...:)

It's like Midnight COmmnader but better...:-P

---

### Post by useResa on 2007-01-31
> **Khepri said:**
> []("http://siliconchaos.blogspot.com/2006/05/setting-up-freemind-in-ubuntu-dapper.html")I used update-manager and it would not update the SVG plugin....the results of that remain to be seen as I've not used that feature yet...

I initially could also not install the SVG plugin (as you can read [here](http://www.ubuntuforums.org/showthread.php?t=348920)).

I have resolved this issue by separately downloading the libbatik-java.deb file and install it by using GDEBI. As can also be read in the earlier indicated thread.

Hopes this help you to use all available plugins of FreeMind

---

