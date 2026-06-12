---
title: "Firestarter help"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by arijarot on 2007-06-02
I keep getting all these hits from people on my firewall. I'm wondering if there is a way to know if the sources are a concern or not. How do you know when these hits are a threat? I also have active connections established on ports to services that I don't even use (e.g., port 27912; service Quake); I don't understand why...

---

### Post by enopepsoo on 2007-06-02
It sounds like your firewall is taking care of it.  Maybe you have the IP of an old quake server.

---

### Post by arijarot on 2007-06-02
If the firewall is taking care of it, why would it allow connections for services that are not in use?

Also, when I used Ktorrent, firestarter allowed and established a connection to port 1999, service backdoor-g/subseven under the program Ktorrent... that doesn't sound right, does it? Edit: how do I know if I "got something" now? e.g., an infection, worm...?

Also, when I ran rkhunter it said

```
* Filesystem checks
   Checking /dev for suspicious files...                      [ OK ]
   Scanning for hidden files...                               [ Warning! ]
---------------
/etc/.pwd.lock
/etc/.java /dev/.tmp-22-0
/dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools 
---------------
Please inspect:  /etc/.java (directory)  /dev/.tmp-22-0 (block special (22/0))  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory) 

```

more info

```
[12:24:35] Added /etc/.java (directory) to list of unknown hidden files/dirs
[12:24:35] Added /dev/.tmp-22-0 (block special (22/0)) to list of unknown hidden files/dirs
[12:24:35] Added /dev/.static (directory) to list of unknown hidden files/dirs
[12:24:35] Added /dev/.udev (directory) to list of unknown hidden files/dirs
[12:24:35] Added /dev/.initramfs (directory) to list of unknown hidden files/dirs
```


and 

```
* Interfaces
     Scanning for promiscuous interfaces...                   [ OK ]
     Scanning for packet capturing applications...            [ Warning! ]
Warning! Found packet capturing application. Please use option '--createlogfile' and check the logfile.

```
what do I do/how do I inspect?

---

