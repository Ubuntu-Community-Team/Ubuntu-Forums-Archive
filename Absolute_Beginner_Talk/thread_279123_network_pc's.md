---
title: "network pc's"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-17
Hey.
I've got two 'puters connected to the same router (same broadcast domain). I would like to know how to transfer files back and forth between them. Is there a software tool for managing network connections?

---

### Post by jeffathehutt on 2006-10-17
Probably the easiest way is to use samba.  Check System->Administration->Shared Folders

That should work for two linux machines or a windows and linux machine.

---

### Post by saintj0n on 2006-10-18
Ok..
So what exactly does this allow me to do? Remote operation of another linux pc, network printing, file sharing maybe? Is samba a network protocol or just an app that networks computers?

---

### Post by Ozitraveller on 2006-10-18
Try here:

SettingUpSamba
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

and this includes :
What is Samba and when do I need it?
To make a long story short : Samba is a set of tools to share files and printers with computers running Windows. It implements the SMB network protocol, which is the heart of Windows networking.  etc ..................

---

### Post by Soarer on 2006-10-18
You might also need to configure the router. Its possible some ports are blocked by default, even between PCs on the same LAN.

---

### Post by saintj0n on 2006-10-18
Hmm..
I hear that I can use something called NFS. Is that an easier way to go because I can't even get SWAT to launch at this point. I cleared my router by the way and did a ping test.

---

### Post by StormNet on 2006-10-18
If you are sharing files between Linux and Windows, Samba is what you want to use, and you can get a great HOWTO at this location:
[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

If you are going to be sharing files between two Linux Machines, NFS is the way to go. Start with this link to set it up:
[https://help.ubuntu.com/ubuntu/serverguide/C/network-file-system.html]("https://help.ubuntu.com/ubuntu/serverguide/C/network-file-system.html")
and use this for more in depth information on the different configuration files (/etc/exports, /etc/hosts.deny and /ect/hosts.allow)
[http://nfs.sourceforge.net/nfs-howto/ar01s03.html#config_server_setup]("http://nfs.sourceforge.net/nfs-howto/ar01s03.html#config_server_setup")

and this for setting up the NFS client:
[http://nfs.sourceforge.net/nfs-howto/ar01s04.html]("http://nfs.sourceforge.net/nfs-howto/ar01s04.html")

---

