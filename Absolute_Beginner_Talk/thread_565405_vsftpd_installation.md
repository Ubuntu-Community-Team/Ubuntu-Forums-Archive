---
title: "vsftpd installation"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by stilwalli on 2007-10-02
Hi, 
I have recently installed Ubuntu 5.04 through VM Ware. I am trying to install FTP Daemon VSFTPD. I trie dinstalling, it but I am not able to do so.
The problems that I am facing is
1. It gives message "Package Not Found"

I even tried downloading it, then it started giving messages of dependencies. I tried updating all the dependencies but still not help...

could you please help

Shashank

---

### Post by j.bunce on 2007-10-02
5.04 isn't supported by Ubuntu anymore, so some of the packages may have been removed from the apt repository. Get yourself a copy of 7.04 (code name Feisty), then run the following.

```
sudo apt-get install vsftpd
``` 

As a personal preference, I like proftpd ;)

---

### Post by stilwalli on 2007-10-03
I am not able to get binaries of proftpd or vstftpd. By default there are not binaries when I installed. But by reading the posts, it seems that it is installed by default. I am using Ubunt 5.0.4

please help

---

