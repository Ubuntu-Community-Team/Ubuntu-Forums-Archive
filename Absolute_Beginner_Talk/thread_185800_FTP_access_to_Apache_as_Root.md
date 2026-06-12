---
title: "FTP access to Apache as Root?"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by colemanc on 2006-06-01
Hi,

Fairly new to Linux, (Fedora and now Ubuntu in a desktop enviroment),totally new to administering my own server. I installed apache on an old box that will function as a server in a small office. Assigned the apache box its own IP address on the LAN and wish to acesss it via FTP to build and maintain a simple web page.

I am running gFTP on the client side, and wu-ftp on the server side. 

I am able to FTP connect to the server when logging in as a regular user on the server and can see the /var/www directory, but it will not allow me to upload files.

I then attempt to log in to the server via FTP using root as the uname and the root password, but access is denied.

So I guess my question would be: Is there a way to log in as root via FTP so that I can write to the /var/www directory OR can I change the permissions to allow a routine user who is logged into the server the ability to write into the /var/www/ directory. If neither of these is a solution, then please tell me what else I can do.

Thanks in advance for any assistance

---

### Post by adwait on 2006-06-01
If you configure the ftp server correctly, you can login as any user on that system and you will have access to all the files that user has access to.

---

### Post by colemanc on 2006-06-01
[QUOTE=adwait]If you configure the ftp server correctly, you can login as any user on that system and you will have access to all the files that user has access to.[/QUOTE]

I switched FTP servers from wu-ftpd to proftpd to see if maybe the situation would resolve itself.

I didnt edit the .conf file or any other file at all assuming that remaining unaltered, the server would allow, as you said, any user access to any files the user normally has acess to. There were only two users created on the machine : root and uname. uname connects fine via ftp, but root will not connect, with gFTP giving the following error:

USER root

331 Password required for root.
PASS xxxx
530 Login incorrect.
Disconnecting from site 192.168.0.20

This message is in spite of the fact that the correct password is entered. 

Any ideas?

---

### Post by colemanc on 2006-06-01
I figured it out. Simply had to change the permissions on the directory so that I could write to it as uname. :mrgreen: 

Thanks

---

