---
title: "File sharing"
date: 2010-07-23
forum: Apple Hardware Users
---

### Post by CLCompton on 2010-07-23
Im running a Ubuntu FTP server (I didnt set it up , our former IT guy did), and I need to be able to populate the ftp folders from a power Mac on the network. Iver created a folder on the linux server and can see it from the mac, but when i try to access it I get "doesnt exist.....thoughts?

---

### Post by conundrumx on 2010-07-23
Have you tried accessing the FTP server from any other computers or software?

If you do `ftp localhost` from the server, does that work?

---

### Post by CLCompton on 2010-07-23
Yep,..it works just fine, and FTP site itself works just fine,..It seems the problem has to do with drive partitions. You see  the drive is partitioned into two parts, 75gig, and 200gig. If you make a folder on the 75 gig you can see it anywhere on the network. but if you make a folder on the 200 part, you can see it but the mac says its a bad link...I should stop using the words FTP anymore. the ftp server works, and is accessible, it the file sharing on this Mac Linux network that is failing...

---

### Post by conundrumx on 2010-07-23
Okay, is the Ubuntu server sharing the files over AFP?  SMB?

---

