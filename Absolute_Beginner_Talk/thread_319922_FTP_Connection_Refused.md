---
title: "FTP Connection Refused"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by HeavyEddie on 2006-12-16
I've installed Dapper on my wife's PC and so far she if very happy with her new OS.  I'm happy because I don't have to buy her a new PC :)

I've setup an FTP server on her machine using [this tutorial]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#FTP_Server").  It works great as long as I connect directly via IP.  However, when I try to connect through the Internet I get "Connection Refused" every time.  

I don't think it is an issue with the dynamic DNS, firewall or port forwarding on the router since I'm able to connect to the web page I'm hosting on this machine using Apache.  BTW... I am forwarding port 21 in the router for FTP.

---

### Post by Bachstelze on 2006-12-16
I definitely don't recommend using FTP to connect to the machine since the password will be transmitted in clear text. Rather, install *openssh-server*, forward port 22 and connect using FTP via SSH (also called SFTP sometimes).

---

### Post by HeavyEddie on 2006-12-16
> **HymnToLife said:**
> I definitely don't recommend using FTP to connect to the machine since the password will be transmitted in clear text. Rather, install *openssh-server*, forward port 22 and connect using FTP via SSH (also called SFTP sometimes).

If I use this method, will I be able to easily use a standard FTP client to connect?  Is there a tutorial you can suggest on this method?

---

### Post by Bachstelze on 2006-12-16
Yes, most standard FTP clients support this (FileZila in Windows does, and in Linux I use GFTP). Just be sure to specify you want to use SFTP.

Plus, SSH will also allow you to login remotely to the box if you need to do something more complex than just transferring some files.

---

