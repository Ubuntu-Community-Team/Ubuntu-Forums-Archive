---
title: "Ubuntu edgy and can't install skype"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by umatix on 2008-01-25
HELLO !

Been trying since forever to inatall skype on edgy.

Can't seem to find appropriate help.

Seems I have dependancy issues I can't fix.

I have tried all solutions in  post in the forum and no luck. same result

Here is the output from the last example:


-all.deb; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu;](http://www.skype.com/go/getskype-linux-ubuntu;) sudo dpkg -i getlibs-all.deb; sudo dpkg -i --force-all skype-install.deb; sudo getlibs /usr/bin/skype; cd ~
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ia32-libs
--03:26:43-- [http://boundlesssupremacy.com/Cappy/...etlibs-all.deb](http://boundlesssupremacy.com/Cappy/...etlibs-all.deb)
=> `getlibs-all.deb'
Resolving boundlesssupremacy.com... 209.123.149.151
Connecting to boundlesssupremacy.com|209.123.149.151|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6,436 (6.3K) [text/plain]
Server file no newer than local file `getlibs-all.deb' -- not retrieving.

--03:26:43-- [http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)
=> `skype-install.deb'
Resolving [www.skype.com](www.skype.com)... 204.9.163.136
Connecting to www.skype.com|204.9.163.136|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://download.skype.com/linux/skyp...118-1_i386.deb](http://download.skype.com/linux/skyp...118-1_i386.deb) [following]
--03:26:44-- [http://download.skype.com/linux/skyp...118-1_i386.deb](http://download.skype.com/linux/skyp...118-1_i386.deb)
=> `skype-install.deb'
Resolving download.skype.com... 130.117.72.42, 130.117.72.43
Connecting to download.skype.com|130.117.72.42|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13,384,906 (13M) [application/octet-stream]

100%[================================================== ===========================>] 13,384,906 941.22K/s ETA 00:00

03:27:00 (797.59 KB/s) - `skype-install.deb' saved [13384906/13384906]

(Reading database ... 111149 files and directories currently installed.)
Preparing to replace getlibs 2.02 (using getlibs-all.deb) ...
Unpacking replacement getlibs ...
Setting up getlibs (2.02) ...
dpkg - warning: downgrading skype from 2.0.0.27-1 to 1.4.0.118-1.
(Reading database ... 111149 files and directories currently installed.)
Preparing to replace skype 2.0.0.27-1 (using skype-install.deb) ...
Unpacking replacement skype ...
dpkg: skype: dependency problems, but configuring anyway as you request:
skype depends on libasound2 (>> 1.0.12); however:
Version of libasound2 on system is 1.0.11-7ubuntu3.
skype depends on libqt4-core (>= 4.2.1); however:
Package libqt4-core is not installed.
skype depends on libqt4-gui (>= 4.2.1); however:
Package libqt4-gui is not installed.
Setting up skype (1.4.0.118-1) ...
/usr/bin/getlibs: line 574: unexpected EOF while looking for matching `''
/usr/bin/getlibs: line 594: syntax error: unexpected end of file
iman@iman-laptop:~$

Would apriciate any assistance as i really need it on my laptop and can't upgrade to feisty as its impossible to mount peripherals including CDROM and external HD

Thanks

---

### Post by tojge on 2008-01-26
Now, this may seem as (and indeed might be) a silly question, but, are you sure you don't have it installed already?

---

