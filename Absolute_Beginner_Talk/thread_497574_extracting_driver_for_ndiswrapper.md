---
title: "extracting driver for ndiswrapper"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-07-10
I want to use a Linksys driver for a USB wireless 'net connection.

I have the driver from Linksys.

I have used Automatix to install the "archive" or "compressed files" software.

When I highlight the .exe (MS-mess) and right-click, I'm not offered a means to "extract" the .inf and other relevant files into a directory.

I looked through the debian menu in Applications/Debian but there is only File Roller. A/X did mention that there wasn't a menu entry for these archiving tools, but I am lost as to how to execute (does that mean KILL in microsoft-speak?) the compressed driver download.

Help!

---

### Post by Mark_in_Hollywood on 2007-07-10
I found that 

unzip filename

did the trick. 

Yet, please know that I stumbled across this from documents much 'out of date'. Viz:

[http://linuxgazette.net/issue82/tag/1.html](http://linuxgazette.net/issue82/tag/1.html)

with a date of 2002. 

Glad it worked, however. To any moderators: 

the unzip portion needs to be added to the ndiswrapper or Wireless/WiFi how-tos. Thanks.

---

### Post by dmfield on 2007-07-10
having unzipped the driver, there will be somewhere in the directory stucture you just unzipped a drivers folder, possibly under that an XP folder, the file you are looking for will end in .inf usually..

Once you find this type in

> su

and enter the super user password, did you say you were using debian? if its ubuntu you are using just append sudo to the beginning of each command

> ndiswrapper -i ***<filename>***.inf

Where file name is the filename you found earlier..

this will load the windows drivers in Linux..

Having done that type

> ndiswrapper -l

this will check the driver is loaded.

then

> ndiswrapper -m
> ndiswrapper -ma
> ndiswrapper -mi

if you want it to load at boot time


then a 

> modprobe ndiswrapper 

should get you working

then 

> iwlist scan

will show if you can see any networks

---

