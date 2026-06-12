---
title: "apt-get woes"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by ibtexn on 2006-06-15
I cant seen to get aptget to do anything?
i posted the content of the terminal window and my apt.conf.  
thanks in advance
----------------------------------------------------------------
rchrane@100N-05:~$ sudo apt-get update
Password:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (85.133.25.8), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could  not connect to archive.ubuntu.com:80 (85.133.25.8), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used  instead.
rchrane@100N-05:~$

------------------------------------------------------------
content of apt.conf

Acquire::10.202.4.10:8002 "false";

---

### Post by shof2k on 2006-06-15
Can you connect to the internet using your pc?  If so, open a terminal using APPLICATIONS-ACCESSORIES-TERMINAL and type "ping archive.ubuntu.com".  That should so if your network is ok or not.

---

### Post by ibtexn on 2006-06-16
yes I can get on the internet and No I cant ping archive.unbunto.com

---

