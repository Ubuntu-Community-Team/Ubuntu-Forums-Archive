---
title: "Share folder with Mac?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by DaveGiant on 2008-03-30
I have set up a simple shared folder. I have set the folder as smb.

I want to connect to it with my Mac. I connected to smb://192.168.1.23

This brought up a login box. I cannot log in as guest adn I cannot figure out the username/password that it wants.

What do I need to do?

---

### Post by mivo on 2008-03-30
Have you tried your normal user name and password? The ones you use to log into Ubuntu.

Also, [this guide]("http://www.moixo.com/es/sharing-files-folders-from-ubuntu-to-mac-os-x") may be useful. :)

---

### Post by DaveGiant on 2008-03-30
Tried the guide, samba restart did sweet FA.

Apparently Leopard doesn't have Run "NetInfo Manager"

---

### Post by DaveGiant on 2008-03-30
All I want to do is allow guest access, I don't want to faf around with passwords. All I want to do is transfer media between 2 computers. I don't see why this is so difficult.

---

### Post by DaveGiant on 2008-03-30
If I can't share the folder with my mac, any ideas how I can get my mac to appear on the network screen of my ubuntu install?

---

### Post by cosborn72 on 2008-03-30
There are several routes you can take.

One, on the Mac, go to system preferences-> Sharing
Click on Personal files sharing, then window's file sharing.

In ubuntu, you should be able to access the samba share (assuming you have SMB running), at the following address:  \\<mac i.p>/<mac username>

For example, mine is \\192.168.0.100\chris

This should allow you to mount your OSX home folder in Ubuntu.  You will need to know your Mac OSX user password to do this.

Alternately, you can choose FTP access and connect through a FTP client or browser.

---

### Post by surfer63 on 2008-06-12
To connect from your mac box to your ubuntu box

edit your smb.conf in /etc/samba on your Ubuntu box

Your global section should say something like:
[global]
  workgroup = MyWorkgroup
  printcap name = cups
  printing = cups
  security = share
  disable spoolss = Yes
  show add printer wizard = No
  wins support = yes
  domain master = no
  local master = yes
  preferred master = yes
  os level = 65
  name resolve order = wins lmhosts


Create a read-only share "entry"
[MyshareRO]
comment = RO form of Myshare
path=/<path_to>/Myshare
read only = yes
guest ok = yes
nt acl support = No

Create a read-write share entry
[MyshareRW]
comment = RW form of Myshare
path=/<path_to>/Myshare
writable= yes
guest ok = yes
nt acl support = No

(NOTE: THIS RW SHARE IS HIGHLY UNSECURE! YOU'D BETTER NOT USE IT WITH GUEST ACCOUNT LIKE THIS. But hey, you asked.)

Save it. Restart samba.

On your OSX-box, open Finder, menu "Go"->Go to server.

In the popup enter in the server address box:
smb://<servername or ip-address>/MyshareRO

or
smb://<servername or ip-address>/MyshareRW

---

