---
title: "Looking for firewall"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by bdemers on 2008-01-25
I have 2 questions:

I want to add a FTP server to my home network, but it needs to go into a DMZ.  I do not have a static IP, so DynDNS will do the job for me.  I have had some exposure to IPCop, but was wondering if that is my most reliable choice?  

Is there a choice on FTP servers, what I'm looking at is admin functionality, either frontend or backend?

---

### Post by chippy99 on 2008-01-25
I've been using IPCOP for about 6 months and have had no problems with it. Its easy to setup and ultra reliable. Also have openvpn addon installed which works well. Never been rebooted except when I had to unplug it to sort out some cabling.

Don't know much about ftp servers I just picked proftp because it was in the packages.

---

### Post by SomethingCronic on 2008-01-25
The best ftp software I've used by far is vsftp. I've used it at home, and at a corporate level. If you want anonymous read only access to files then 


```
sudo apt-get install vsftpd 
```
will work out of the box - otherwise it's some easy configuration on the /etc/vsftpd.conf file.

---

### Post by OffAxis on 2008-01-25
If you're looking for admin functionality, you might consider running vsftp with a mysql database to hold user names. Otherwise, every ftp user will also need to be a system user of some kind.
This is for debian etch, but it parallels the ubuntu settings closely (if not completely).
[http://www.howtoforge.com/vsftpd_mysql_debian_etch]("http://www.howtoforge.com/vsftpd_mysql_debian_etch")

---

