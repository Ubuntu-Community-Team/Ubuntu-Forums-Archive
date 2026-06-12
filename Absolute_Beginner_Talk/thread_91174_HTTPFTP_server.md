---
title: "HTTP/FTP server"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by Morthane on 2005-11-16
I want to create a HTTP server that has FTP access so I can update files remotely.  I did this in Windows with GuildFTPd and IIS, but I want to explore Ubuntu.  My setup is small:

root folder with upload, programs, and users subfolders
users contains 3 subfolders

-admin account:  access to all folders, write access to all folders
-upload account: access to all folders but programs folder, write access to upload folder
-guest account: access to all but upload folder and programs folder


I know there's been other posts on this, but all the solutions seem to refer to a guide that is either intimidating or wants you to do too much (set up email server as well, etc).  Additionally, they all say "do this" without explaining WHY we are doing this or what it achieves.

Anyone have a step-by-step comprehensive guide to recommend?

---

### Post by kruz on 2005-11-16
hmm
sudo apt-get install proftpd
sudo apt-get install apache

and your gona have to do a lil configuring

btw im not sure if cerebrus is supported by linux


[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)

---

