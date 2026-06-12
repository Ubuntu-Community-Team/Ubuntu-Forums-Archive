---
title: "Hellanzb problem"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by zues on 2007-07-13
I followed all the instruction's to setup hellanzb. My problem is my hellanzb-0.9 folder is locked and it's missing some folder's. It's missing daemon queue and usenet, both are very important with this program other than that it seems like it's running.

tommy@tsunami:~/hellanzb-0.9$ sudo hellanzb.py

hellanzb v0.11 (config = /usr/etc/hellanzb.conf)
(/home/tommy/) Opening 4 connections...
hellanzb - Now monitoring queue...)


 It's waiting for me to put a nzb folder into the queue but I don't have a queue. And even if i queued it it's suppossed to download to the usenet folder I don't have that one either.

---

### Post by felicity on 2007-07-13
You may want to use an updated version, it's 0.13 currently. 

Did you follow the install directions? It seems like you're trying to run it from the directory you downloaded rather than installing it first. 

In regards the /etc/hellanzb.conf file after installation, you have to edit the file to tell it where you want the queue directory to be. So you could make it your desktop (~/Desktop) or wherever you want it to monitor for new nzb files. You also have to specify a directory that you want the files downloaded to. You say it doesn't exist, but you have to give it a directory that already exists or create a new directory for it.

---

