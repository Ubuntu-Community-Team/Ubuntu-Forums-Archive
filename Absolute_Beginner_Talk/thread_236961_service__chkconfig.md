---
title: "service / chkconfig"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by Mr. Brownstone on 2006-08-15
In some distros like FC I can type things like:```
service dhcpd start
chkconfig 2345 smb on
```What do I need to do to achieve the same thing in Dapper?

Thanks! :)

---

### Post by moma on 2006-08-15
Debian and its derivatives use **update-rc.d**.

Define and install a service script
$ [COLOR="Green"]sudo update-rc.d smb defaults[/COLOR]
or 
$ [COLOR="Green"]sudo update-rc.d samba start 20 2 3 4 5 . stop 20 0 1 6[/COLOR]
20 is sequence number for the script.

Remove a service script
$ [COLOR="Green"]sudo update.rc.d -f smb remove[/COLOR]

[COLOR="Red"]Study[/COLOR] 
$ [COLOR="Green"]man update.rc.d[/COLOR]
-----------------------

Howto start and stop a service ?
$ sudo /etc/init.d/servicename start|stop|restart|status 
A sample:
$ [COLOR="Green"]sudo /etc/init.d/smb start [/COLOR]
---------
Or use "BUM", Bootup and Service Manager
$ [COLOR="Green"]sudo apt-get install bum [/COLOR]
$ [COLOR="Green"]sudo bum [/COLOR]
Click Advanced and select Services tab-page.

---

### Post by Mr. Brownstone on 2006-08-15
Great, thanks for the info! 8) 

Which repository do I have to choose to install bum, though?

---

### Post by moma on 2006-08-15
Good question.

$ [COLOR="Green"]apt-cache show bum[/COLOR]
Package: bum
Section: universe/admin
....
Filename: pool/universe/b/bum/bum_2.1.5-1build1_all.deb

It's in the Universe repository.
Enable (uncomment) it in /etc/apt/sources and run 
$ [COLOR="Green"]sudo apt-get update [/COLOR]

This guide has more about the repos.
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

---

