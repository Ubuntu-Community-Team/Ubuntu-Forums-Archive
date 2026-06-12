---
title: "vsftpd"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by masi mfg on 2007-07-12
Hi 
I am pretty new at this. I need to setup users that are the only ones that will be able to log into the server. What format do i use and how do i enable it as it is not in my conf file. I also need to find the address of my server so that i can connect to it externaly. Any help.

---

### Post by upbeat.linux on 2007-07-12
You setup Ubuntu-Server but you don't know the IP address?  To find your IP address open a terminal and type:

```
ifconfig
```

Look for the inet address.  That will be the IP address of your server. Make sure you have your firewall/router configured properly to allow connections.

For setting up vsftpd see this great guide:

[http://www.cyberciti.biz/faq/ubuntu-vsftpd-ftp-service-server/]("http://www.cyberciti.biz/faq/ubuntu-vsftpd-ftp-service-server/")

Depending on what version of Ubuntu you are running you may need to use this to edit the conf file:

```
gksudo gedit /etc/vsftpd.conf
```

I wouldn't worry about allowing users access to vsftpd.  As long as you create users on the system they should have access to vsftp once it is installed and configured (except of course for root).

A great alternative for secure file transfers is to use SSH:

[http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/]("http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/")

If you're clients are using Windows they can use WinSCP or SSH Secure Shell Client to upload/download files.

And of course remember that Google is your friend... :cool:

---

