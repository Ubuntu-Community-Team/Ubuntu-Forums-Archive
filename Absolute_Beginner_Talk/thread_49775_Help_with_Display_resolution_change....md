---
title: "Help with Display resolution change..."
date: 2005-07-17
forum: Absolute Beginner Talk
---

### Post by eads1234 on 2005-07-17
1. I installed Linux (HH504) today. My display screen after installation was set at 640x480 (default?).
2. I want the resolution to be 1024x768.
3. When I go to System/Preferences/Screen Resolution  --- I cannot change anything. In fact, 640x480 appears to be the only (probably default) resolution available.

Can someone give me an assist here. I can think of a lot of reasons why this situation (resolution at default resolution only) is like it is, but my lack of Linux/Unix/etc. knowledge doesn't permit me to take a corrective action.  THANK YOU FOR ANY HELP!

---

### Post by evilghost on 2005-07-17
Check out [http://ubuntuforums.org/showthread.php?t=49260](http://ubuntuforums.org/showthread.php?t=49260) and remember be sure to use the search feature for instant solutions :)

---

### Post by poofyhairguy on 2005-07-17
Hello friend. Put this command:

sudo dpkg-reconfigure xserver-xorg

in the regular (not root) terminal

---

### Post by aysiu on 2005-07-17
[http://ubuntuforums.org/showthread.php?t=48761&highlight=vertrefresh](http://ubuntuforums.org/showthread.php?t=48761&highlight=vertrefresh)

---

### Post by varunus on 2005-07-17
Also, if your video card is an intel integrated graphics card, follow this howto: [http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029)

It fixes some problems that buggy bioses have with reporting screen resolutions to the OS.

---

### Post by eads1234 on 2005-07-17
Thanks to everyone who gave me information. My display resolutions are now all supported. Again, I thank everyone!

---

