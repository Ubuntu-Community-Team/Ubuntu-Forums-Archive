---
title: "Changing permission"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by larry Gaminde on 2007-07-29
I am trying to change permission to a directory or the whole drive
home/ftp or the File System
I think its a sudo command but I don't know how to use it
I looked up Understanding and Using File Permissions and don't have a clue how to use it 
I want to change permission from root to all

---

### Post by aysiu on 2007-07-29
Do not change permission to an entire drive. If you want to change permission on the /home/ftp directory (Is there such a directory? Or did you just create it?), type this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R *username:username* /home/ftp
``` where *username* is your actual username.

To understand things a bit better, read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by larry Gaminde on 2007-07-29
Ok that worked but I still cannot write to or make directory's using FTP and I have opened up most of the vsftpd.conf settings to allow this.

---

