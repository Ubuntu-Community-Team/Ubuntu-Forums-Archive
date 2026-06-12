---
title: "does ftps = sftp in gFTP?"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by towsonu2003 on 2007-02-21
I'm trying to find a nice gui for sftp... 

When I tried gFTP, one of the protocols it list is "FTPS". is that the same thing as "sftp" or is it something different? documenttion did not tell anything (or I couldn't find it)

PS. I tried krusader, but I'm having [problems with it.]("http://ubuntuforums.org/showthread.php?p=2190985#post2190985")...

---

### Post by Bachstelze on 2007-02-21
Here I only have FTP, HTTP, Local, SSH2 and FSP, I choose SSH2 for sftp.

---

### Post by jpeddicord on 2007-02-21
To put it simply, no.

FTPS is also known as FTP/SSL, and is the format of FTP used for secure connections (much like HTTP and HTTPS).

SFTP, however, is short for SSH File Transfer Protocol. It is a completely separate protocol from FTP, and uses its own transfer mechanisms. In gFTP, this is labeled simply as SSH.

And for any situation, I highly recommend SSH/SFTP over FTP/FTPS. It is faster, and generally more secure overall.

---

### Post by towsonu2003 on 2007-02-21
thanks, this helped a lot. I didn't know that in gftp: ssh = sftp while ftps ~= ftp

thanks again.

---

