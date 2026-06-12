---
title: "best program for what I am trying to do"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by solrpwr on 2006-02-23
I have Ubuntu 5.10. I am trying to create a server that I can have people log in and gain access to particular folders to download files. (I would love to have a check out system so that two people can collaborate on files, but not at the same time) DocMan2.0 (too difficult for me) My skill level is that that good yet. 

Are there any programs that I could load from Synaptic? I loaded Apache2, php support, mysql, etc. all because I was playing with installing the DocMan. 

Thanks for any assistance you may offer.

Jeffrey

---

### Post by Zahrber on 2006-02-23
It may be as simple as runnig ftp server on your computer and letting them ftp into certain folders you give access to. But they need to know how to use ftp and you need a static IP preferably.

Or you can login with ssh and get access to certain folder according to your userid.

What you are trying to do and the level your users are at makes a different.

FTP can be done quite easily (I think) and is designed for file transfer hence the name FTP(File Transfer Protocol). And since they use an FTP client it makes no different what their OS is.

---

### Post by solrpwr on 2006-02-23
Thanks, I kind of thought that might be the way to go. It doesn't give me the check out solution I am desiring, but at least it's a start.  

Do you recommend any FTP programs, or just pick one from synaptic.

Jeff

---

### Post by theturner on 2006-02-23
You need an FTP server (the term "FTP program" is generally used for clients).
proftpd is a good choice. It's in the repositories.

---

### Post by echo $USER on 2006-02-23
I use vsftpd for the same thing you are trying to accomplish.  vsftpd also supports secure sockets layer; I'm not sure if proftpd does.

---

### Post by solrpwr on 2006-02-23
Thank you for the referrals. Will either program display files in any internet browser. I.e, can my buddy in CA go to my site with firefox and log in?

Thanks! I am really digging Linux. I just need to get a little more up to speed.

---

