---
title: "mount network place as a directory"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by bigodines on 2006-04-06
this is probably an easy question (I swear I did a search and tried many sugestions before posting) but I would like to access a remote directory (in the same network) as a local directory... I've seen a couple sugestions to use smbmount and stuff but it seems that ubuntu doesn't have this...

i'm lost ](*,) 


thanks in advice
matheus

---

### Post by pbaehr on 2006-04-06
Have you looked at this yet?

[http://www.ubuntuguide.org/#mountunmountnetworkfolders](http://www.ubuntuguide.org/#mountunmountnetworkfolders)

---

### Post by karthik085 on 2006-04-06
You have to install samba, smbfs...to use smbmount.
Also, if you go to the menu, you can go to Places -> Connect to Server. to connect to the network drive.

---

### Post by bigodines on 2006-04-06
[QUOTE=pbaehr]Have you looked at this yet?

[http://www.ubuntuguide.org/#mountunmountnetworkfolders](http://www.ubuntuguide.org/#mountunmountnetworkfolders)[/QUOTE]

yes, I did. Once password is not needed, I tried using:
sudo mount //10.1.1.17/music /home/lambari/net/mp3/

and it returned:
> mount: wrong fs type, bad option, bad superblock on //10.1.1.17/virus_lib,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


---

### Post by mccyron on 2006-04-06
I have problmes with that form of samba mounting too. Even though I specify a username and password it asks for the password again. It refuses to accept the correct password and doesn't mount what I wanted. On other systems I use - 

mount -t smbfs //username@Server/share /mount-pt

...but Ubuntu doesn't seem to know about smbfs file system type. Why is this? 

The built in facility under the Places/Network_Servers menu works in a fashion but is dreadfully slow. I'm still trying to figure out what's going on with all the id and password checking along the way when logging onto a Windows server share.

Any ideas?

---

