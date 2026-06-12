---
title: "cannot install mysql-server-5.0"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Nikhil Gohil on 2008-03-27
hi, im trying to install mythtv, but everytime i try, it just stops at getting headers. i tried individual packages and found i could not install mysql-server-5.0 or mysql-server. this is what happens everytime:```
sudo apt-get install mysql-server-5.0 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  tinyca mysql-doc-5.0
Recommended packages:
  mailx
The following NEW packages will be installed:
  mysql-server-5.0
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 26.8MB of archives.
After unpacking 84.5MB of additional disk space will be used.
Err http://archive.ubuntu.com gutsy/main mysql-server-5.0 5.0.45-1ubuntu3
  Connection failed [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-server-5.0_5.0.45-1ubuntu3_i386.deb  Connection failed [IP: 91.189.88.31 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

What is the problem? if i type the address in the firefox addressbar, it starts downloading.
apt-get update and --fix-missing do not help.

---

### Post by kellemes on 2008-03-27
You seem to have no working internet connection.. or the mirror is down.
Can you confirm this?

---

### Post by Nikhil Gohil on 2008-03-27
sorry i forgot to mention that no other package(that i know of) has any problems. ive been trying now and then for about a week now so i dont htink the mirror is down and ias i said, if i paste the url into firefox, it starts downloading, but only for a while(just tried it now). it reaches somy arbitrary percentage completion and just stops............

---

### Post by Nikhil Gohil on 2008-03-27
i just tried downloader for x and it is currently stuck at 17% for like the past 10 minutes..........i got aroung 15-16KBps for the 17% that it did download, and it just dosent start from the terminal or synaptic..........

---

### Post by northern lights on 2008-03-27
It's beyond the shadow of a doubt your comp - the mirror is not down as of now...

```
pille@jobuntu:~$ sudo apt-get install mysql-server-5.0
[sudo] password for pille:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl
  mysql-client-5.0
Suggested packages:
  dbishell libcompress-zlib-perl mysql-doc-5.0 tinyca
Recommended packages:
  mailx
The following NEW packages will be installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl
  mysql-client-5.0 mysql-server-5.0
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.3MB of archives.
After unpacking 105MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com gutsy/main libnet-daemon-perl 0.38-1.1 [45.9kB]
Get:2 http://archive.ubuntu.com gutsy/main libplrpc-perl 0.2017-1.1 [35.0kB]
Get:3 http://archive.ubuntu.com gutsy/main libdbi-perl 1.57-1 [791kB]
Get:4 http://archive.ubuntu.com gutsy/main libdbd-mysql-perl 4.004-2 [136kB]
Get:5 http://archive.ubuntu.com gutsy-updates/main mysql-client-5.0 5.0.45-1ubuntu3.3 [7494kB]
Get:6 http://archive.ubuntu.com gutsy-updates/main mysql-server-5.0 5.0.45-1ubuntu3.3 [26.8MB]
Fetched 35.3MB in 2m30s (235kB/s)                                              
Preconfiguring packages ...
Selecting previously deselected package libnet-daemon-perl.
(Reading database ... 130382 files and directories currently installed.)
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.38-1.1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2017-1.1_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.57-1_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.004-2_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.45-1ubuntu3.3_i386.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.45-1ubuntu3.3_i386.deb) ...
Setting up libnet-daemon-perl (0.38-1.1) ...
Setting up libplrpc-perl (0.2017-1.1) ...
Setting up libdbi-perl (1.57-1) ...
Setting up libdbd-mysql-perl (4.004-2) ...
Setting up mysql-client-5.0 (5.0.45-1ubuntu3.3) ...

Setting up mysql-server-5.0 (5.0.45-1ubuntu3.3) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

```

---

### Post by Nikhil Gohil on 2008-03-27
yes i understand that.......the mirror couldnt be down for a whole week.....but what is wrong with my comp?? i really wanted to try mythtv.........

---

### Post by Nikhil Gohil on 2008-03-27
no ideas anyone???

---

### Post by Nikhil Gohil on 2008-03-27
bump

---

### Post by Nikhil Gohil on 2008-03-27
is there any place where i can get the mysql-server deb and try to install?

---

### Post by kellemes on 2008-03-28
Are you behind a proxy server maybe?

---

### Post by Nikhil Gohil on 2008-03-28
no, im not behind a proxy. could this line ```
0 upgraded, 11 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
``` point to something?

---

### Post by Nikhil Gohil on 2008-03-28
This happens when i try to get the package using wget

```
--04:49:38--  http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-server-5.0_5.0.45-1ubuntu3_i386.deb
  (try: 9) => `mysql-server-5.0_5.0.45-1ubuntu3_i386.deb'
Connecting to security.ubuntu.com|91.189.88.37|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Retrying.
```

---

