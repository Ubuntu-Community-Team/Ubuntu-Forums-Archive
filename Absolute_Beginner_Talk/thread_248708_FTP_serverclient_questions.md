---
title: "FTP server/client questions"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Somenoob on 2006-09-01
I can log on to any variety of FTP servers, right? 

even though i'm using another OS?

And What FTP client is the most secure one?

---

### Post by Marsolin on 2006-09-01
FTP is platform indepenent so it shouldn't matter what OS you use as a client. Overall is is fairly insecure. You can require a login, but the username and password are not encrypted and can be intercepted.

The sftp protocol is more secure because it tunnels through a ssh shell. Many FTP clients support this protocol. It is even a KIO slave in KDE. [KFTPGrabber]("http://www.linuxappfinder.com/package/kftpgrabber") and [lftp]("http://www.linuxappfinder.com/package/lftp") are two clients that support sftp, but the server would need to as well.

---

