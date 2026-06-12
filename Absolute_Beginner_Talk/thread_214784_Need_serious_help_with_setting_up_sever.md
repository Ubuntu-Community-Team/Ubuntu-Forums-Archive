---
title: "Need serious help with setting up sever"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by Murphy11211 on 2006-07-13
G'day Guys

Ill start out by saying I have never used or even seen a linux system before I tried this. I know a fair bit about windows stuff...just bugger all about linux.

So I acquired a machine (pent3, 390MB ram) and decided to try run it up as a Ubuntu server, so I downloaded the ISO file and did all that, installed it fine.....saw the command line and nearly crapped myself. I was expecting it to be a GUI! So yeah...where do I go for some absolute basic learning for ubuntu?

Basicly my goal is to make a file server and some sort of webserver if I can....and if Im feeling extra fancy I would like to have a crack at a firewall.


So yeah, thanks for hearing me out and I can't wait to get cracking at this thing!

Regards

Murph.

---

### Post by MaximB on 2006-07-13
you need to install GUI on the server...there are some posts on the forum on how to do this just search

about server - I found a very good program you might be intersted in
it's a free open source :

[http://www.engardelinux.org](http://www.engardelinux.org)

---

### Post by tkjacobsen on 2006-07-13
You should install the server as lamp server. lamp = linux apache mysql php. This will get you a preconfigured web server. Then install ssh, nfs and samba for sftp, unix file server and windows file server. Also you can install a ftp server.

Wiki links:
lamp: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
ssh: [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
nfs: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
samba: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
ftp: [https://help.ubuntu.com/community/FtpServer](https://help.ubuntu.com/community/FtpServer)

---

### Post by 3rdalbum on 2006-07-13
Yeah, it's not clear to the casual observer that the server version doesn't install a GUI too; they should explicitly say that in a visible place.

Since you're new to Linux, I think you should install the full Ubuntu desktop package which will give you a GUI and all the desktop programs. You can still turn off the GUI whenever you want to run the computer as a server, if you wish.

In the command prompt, type:
```
sudo apt-get install ubuntu-desktop
```

That will install all the desktop stuff from the internet. Or, download the Alternative CD and install the Ubuntu Desktop system from that. When you reboot, the full Ubuntu will start up.

---

### Post by jrjr on 2006-07-13
> **3rdalbum said:**
> 

In the command prompt, type:
```
sudo apt-get install ubuntu-desktop
```

That will install all the desktop stuff from the internet. Or, download the Alternative CD and install the Ubuntu Desktop system from that. When you reboot, the full Ubuntu will start up.

So what you are saying.... install server first then follow above. The server install will result in pre-configured LAMP and the net install will install all the gui's and desktop stuff to make it easy to use.   Right?

I dabbled in Linux years ago and Apache was strictly command line back then. Is it still or is there a gui for that now too? (just doing some research before the fact :mrgreen: )

---

