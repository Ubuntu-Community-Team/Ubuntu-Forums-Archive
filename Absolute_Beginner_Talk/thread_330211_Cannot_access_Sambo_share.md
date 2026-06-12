---
title: "Cannot access Sambo share"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by bazsl on 2007-01-02
I have installed 6.10 server and configured networking. I can ping windows machines on my network from Ubuntu and I can ping the Ubuntu machine from Windows machines.

I have attempted to configure Samba by adding the following entries to the end of smb.conf.

[tmp]
	path = /tmp
	writeable = yes
	valid users = bill, root

[bill]
	path = /home/bill
	writeable = yes
	valid users = bill, root

I cannot see either share from a Windows machine on the network. When I double click the Ubuntu server in Windows explorer a password dialog appears. When I enter username and password that is valid on the Ubuntu server and click OK the password dialog reappears. There is no error message.

Clearly I have missed something that is preventing access but I am so new to Linux that I have no idea where to look or what to look for. I really need help. Thanks.

---

### Post by SyvanX on 2007-01-02
Samba manages its own passwords so you need to run smbpasswd before any users can login.

```
sudo smbpasswd -a bill

sudo smbpasswd -a root

```
and enter the passwords after each command

---

### Post by bazsl on 2007-01-02
That was it. Thanks.

---

