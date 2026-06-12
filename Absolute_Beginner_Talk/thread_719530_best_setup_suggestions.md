---
title: "best setup suggestions?"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by dbrine on 2008-03-09
I just installed 7.10 server and followed the home server setup. no gui. I want a file server for the home but i also need a ftp/ web server as well. of course security is alway important. i have 4 hard drives installed. i wasn't successful at samaba...yet. i can see the share over the network but says permissions problem. according to the howtoforge (home server) i should be able to see shares over the web browser...but can't. was thinking about using webmin but don't know. suggestions for configurations?? i know this is allot...sorry.

---

### Post by dsauxier on 2008-03-09
For Samba configuration, I've found this link to the [ "Unofficial Samba HowTo"]("http://www.oregontechsupport.com/samba/") to be an excellent source.

A couple of the key pieces of information : 
In the [global] section of /etc/samba/smb.conf make sure that "netbios name" is set to your windows pc's Workgroup

Another setting in the global section is 
guest account = smbguest
There is an smbguest user, and that user needs rights to be able to see the files you're attempting to share through shamba.

If you want to give read-only access to an entire directory structure /home/somedir : 
[INDENT]
sudo chgrp -R smbguest /home/somedir
sudo chmod -R 740 /home/somedir
[/INDENT]

---

### Post by om1 on 2008-03-09
ive heard good and bad things about webmin... but i personally used webmin to trouble shoot my test servers to learn what i was doing wrong...
a very useful website is howtoforge.net it has alot of howtos and quick setup guides

---

