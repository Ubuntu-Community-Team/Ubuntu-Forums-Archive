---
title: "FTP server, permition on mounted folder"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-04-21
I just created a small ftp server with a user. Now I can connect to it from my FTP client.

However I mounted this folder, to be used for this user:
/media/sda1/Mp3

But when I try to enter it from the FTP client it says 

> 250 CWD command successful
CWD /mp3 
550 /mp3: Permission denied
CWD /mp3 
550 /mp3: Permission denied

How can I fix this? Im using GProFtpd as Ftp server.

Thanks

---

### Post by aktiwers on 2006-04-21
Ups, fixed the problem.. it was only the folder that needed to be changed permition.

:)

---

