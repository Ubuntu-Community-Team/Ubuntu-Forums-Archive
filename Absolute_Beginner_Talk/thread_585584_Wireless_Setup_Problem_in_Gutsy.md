---
title: "Wireless Setup Problem in Gutsy"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by iAppleuser on 2007-10-21
I'm trying to configure wireless for my macbook core 2 Duo, but my system stops the installation. Please Help!

> iappleuser@ubuntu:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
iappleuser@ubuntu:~$ wget [http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz](http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz)
--17:12:52--  [http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz](http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz)
           => `madwifi-trunk-current.tar.gz.1'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,050,799 (3.9M) [application/x-gzip]

100%[====================================>] 4,050,799     79.16K/s    ETA 00:00

17:13:45 (76.23 KB/s) - `madwifi-trunk-current.tar.gz.1' saved [4050799/4050799]

iappleuser@ubuntu:~$ tar -zxvf madwifi<tab>
bash: syntax error near unexpected token `newline'
iappleuser@ubuntu:~$ cd madwifi<tab>
bash: syntax error near unexpected token `newline'
iappleuser@ubuntu:~$ make
make: *** No targets specified and no makefile found.  Stop.
iappleuser@ubuntu:~$ sudo make install

---

