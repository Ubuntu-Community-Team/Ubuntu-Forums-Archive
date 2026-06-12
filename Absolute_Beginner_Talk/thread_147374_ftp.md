---
title: "ftp"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by ice.man on 2006-03-20
what is the best ftp program to use, which is easy to setup

---

### Post by paulipe on 2006-03-20
gftp is very easy to use. Just go to synaptic package manager and search for gftp and gftp-common and install.

if you want to start an ftp server on your own machine (so that others can connect to your machine) you can try vsftpd also available through synaptic package manager. Setting this up requires editing the /etc/vsftpd.conf file which may not be as easy.

---

### Post by ice.man on 2006-03-20
well i want to so my other linux box can connect to this on just to get little files off it every so often

---

### Post by halfvolle melk on 2006-03-20
Don't know about which is best, but there's a HowTo in the Wiki for Pure FTP:
[https://wiki.ubuntu.com/PureFTP](https://wiki.ubuntu.com/PureFTP)
So there's your server. On your other machine any client will do. gFTP comes with a default Breezy install.

---

### Post by OffHand on 2006-03-20
I like GFTP

---

### Post by starpause on 2006-03-30
lftp client was already installed in Breezy Badger ... it acts a lot like the terminal, and you can type "help" in the client if you need to get your bearings!

---

### Post by izmaelis on 2006-03-30
[QUOTE=ice.man]well i want to so my other linux box can connect to this on just to get little files off it every so often[/QUOTE]
To upload/download files from another Linux box you don't need ftp, actually. Just check if sshd is running on that computer. It is possible to transfer files through SSH2 in more secure manner then FTP.

---

### Post by johnnymac on 2006-03-30
I agree with the above post...if you going Linux to Linux don't bother with FTP just SCP the stuff down.  But, if you must do ftp the simplest method is just do it command line.

from terminal:
bash# ftp [www.blah.com](www.blah.com)

when you there type help..common commands are get and put.

---

