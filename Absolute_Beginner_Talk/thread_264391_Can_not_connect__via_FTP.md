---
title: "Can not connect  via FTP"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by chymo on 2006-09-24
I have apache2/mysql/php5/phpmyadmin all installed and working.  I can access the path /var/www/ through my LAN via HTTP.  I now am trying to use FileZilla to FTP into that box so I can upload content.  I'm getting a generic ftp - unable to connect - error.  I'm using the root login for FTP along with the /var/www/ path in the FTP client.  

Any thoughts on how I can get FTP to work?  Is there some apache2 config setting I'm missing?  Thanks.

---

### Post by chymo on 2006-09-24
I think I may be stuck on this step...

```
Edit Apache Configuration

You may want your current user to be the PHP pages administrator. To do so, edit the Apache configuration file :
 
** $ gksudo "gedit /etc/apache2/apache2.conf" **

Search both the strings starting by "User" and "Group", and change the names by the current username and groupname you are using. Then you'll need to restart Apache. (look at the next chapter concerning apache commands)

Configuration options relating specifically to user websites (accessed through localhost/~username) are in /etc/apache2/mods-enabled/userdir.conf. 
```

Not sure what needs to be done exactly in the apache.conf... Can someone explain?

reference this doc: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by chymo on 2006-09-24
anyone been through this doc before?

---

### Post by Regord on 2006-09-24
I used [THIS GUIDE]("https://help.ubuntu.com/community/SSHHowto") to set up a SSH server that let's me connect via Secure FTP.  If you are connecting from a Windows box, you can d/l WinSCP which is a free SFTP client.  If you are connecting from another Ubuntu box that page has info on how to do it.

Keep in mind, Ubuntu has a firewall installed when you install the OS.  You need to install firestarter, then try to connect to you Ubuntu box and firestarter will show you the connection attempt (port number and IP address).  Then simply go to the policy tab in firestarter and create an inbound policy allowing connections from that computer on that port number.  It's also a good idea to open up port 80 (the default HTML port).  

I hope that helps.

---

### Post by jrcmuniz on 2006-09-26
I used the guide below... just perfect!

[http://www.ubuntuforums.org/showthread.php?t=79588&page=4&highlight=configuring+server](http://www.ubuntuforums.org/showthread.php?t=79588&page=4&highlight=configuring+server)

cheers

---

