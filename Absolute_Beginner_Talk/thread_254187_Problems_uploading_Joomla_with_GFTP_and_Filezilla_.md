---
title: "Problems uploading Joomla with GFTP and Filezilla is acting quirky..."
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-09-09
Ok I previously uploaded Joomla to an FTP with GFTP but then GFTP kept freezing when I tried to move it so I installed Filezilla in wine.  Filezilla moved the folder fine but when it came time to delete the folder, it went on some crazy loop through all the directories for about 40 seconds and then crashed. 

So back to GFTP I went, now I need to upload something else.  However, when I click the arrow to upload the folder I get an error message:

> 
Error: Could not read from socket: Is a directory
Could not download /home/fatsheep/Desktop/joomla from local filesystem
Disconnecting from site look.dreamhost.com
Error: Remote site local filesystem disconnected. Will reconnect in 30 seconds


2 questions:

1.  What is this error message and how do I fix it?
2.  Are there any good native FTP programs out there that support drap and drop uploads and downloads?

---

### Post by encho on 2006-09-09
You can run Filezilla now without wine, there is linux port. There are also few multiplatform java apps and also extension for firefox: FireFTP. For KDE users things are even better, there are quite a few apps, and konqueror supports ftp protocol as well.

Search the forum for those.

---

