---
title: "Ubuntu Server &amp; File Manager"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by sin_bad on 2007-11-11
Hello ;
I have installed ubuntu server and try to manage files remotely using [COLOR="Blue"]webmin   [/COLOR]but cannot , some thing java related prevents File Manager (Applet)  working normally.
can any one recommend another way to manage file (Remotely)  also  (Download & upload)?? 
I dont want to install KDE Desktop or Gn..
 Thanks

---

### Post by Lem on 2007-11-11
Install openssh-server

You can send files using secure ftp (like ssh file tranfer)
sftp <username>@<IP address> -log in
get <filename>-copy to directory (specify path)

You can also use nautilus to connect to a server via ssh (under connect to server in places)

If you need ssh access from windows, use putty.

---

