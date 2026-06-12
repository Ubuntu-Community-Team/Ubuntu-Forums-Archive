---
title: "k3b"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-06-05
```
The following filenames have an invalid encoding. You may fix this with the convmv tool:
/home/zerobinary/Desktop/music/Neon Genesis Evangelion [Flac]/Death/01. Cello - Dainichigen Ch??gen.flac
/home/zerobinary/Desktop/music/Neon Genesis Evangelion [Flac]/Death/02. Suiten f??r Violoncello Solo Nr.1 G-dur.flac
/home/zerobinary/Desktop/music/Neon Genesis Evangelion [Flac]/Death/03. Dvor??k Original Complete Version.flac
/home/zerobinary/Desktop/music/Neon Genesis Evangelion [Flac]/Death/04. Violin - Dainigen Ch??gen.flac
/home/zerobinary/Desktop/music/Neon Genesis Evangelion [Flac]/Death/05. Partita III f??r Violino solo E-dur.flac
/home/zerobinary/Desktop/music/Neon Genesis Evangelion [Flac]/Death/06. Viola - Daisangen Ch??gen.flac
/home/zerobinary/Desktop/music/Neon Genesis Evangelion [Flac]/Death/09. Matsury?? e no, Genritsu.flac
/home/zerobinary/Desktop/music/Neon Genesis Evangelion [Flac]/Death/12. Kyom?? e no, Izon.flac
/home/zerobinary/Desktop/music/Neon Genesis Evangelion [Flac]/Death/13. Jiga Ky??kai.flac
```
k3b is not working for me when i am burning data dvd help plz

---

### Post by FleetAdmiral74 on 2007-06-05
Are you sure k3b supports the format you are using?

have you found info on the convmv tool tool? its helpfull if you do some research on your own first, then be specific.

---

### Post by zerobinary on 2007-06-06
but isn't burning data dvd won't be affected my the filing type 
all i need right now is probabyly the plug in the japanese in both k3b and gnombaker so the character error will be gone but i don't know how to do it
and what is convmv tool
anyways i always get this error
> zerobinary@zerobinary:~$ sudo apt-get install convmv
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  convmv
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 18.7kB of archives.
After unpacking 90.1kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe convmv 1.10-0.1 [18.7kB]
Fetched 18.7kB in 1s (17.5kB/s)
Selecting previously deselected package convmv.
(Reading database ... 174759 files and directories currently installed.)
Unpacking convmv (from .../convmv_1.10-0.1_all.deb) ...
Setting up postgresql-8.2 (8.2.4-1~edgy1) ...
 * Starting PostgreSQL 8.2 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2007-06-05 22:01:09 PDT LOG:  could not load root certificate file "root.crt": no SSL error reported
2007-06-05 22:01:09 PDT DETAIL:  Will not verify client certificates.
2007-06-05 22:01:09 PDT LOG:  could not translate host name "localhost", service "5432" to address: Name or service not known
2007-06-05 22:01:09 PDT WARNING:  could not create listen socket for "localhost"
2007-06-05 22:01:09 PDT FATAL:  could not create any TCP/IP sockets
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.2, action "start" failed.
dpkg: error processing postgresql-8.2 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of glom:
 glom depends on postgresql-8.2; however:
  Package postgresql-8.2 is not configured yet.
dpkg: error processing glom (--configure):
 dependency problems - leaving unconfigured
Setting up postgresql-8.1 (8.1.8-1ubuntu3) ...
 * Starting PostgreSQL 8.1 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2007-06-05 22:01:11 PDT LOG:  could not load root certificate file "root.crt": No SSL error reported
2007-06-05 22:01:11 PDT DETAIL:  Will not verify client certificates.
2007-06-05 22:01:11 PDT LOG:  could not translate host name "localhost", service "5433" to address: Name or service not known
2007-06-05 22:01:11 PDT WARNING:  could not create listen socket for "localhost"
2007-06-05 22:01:11 PDT FATAL:  could not create any TCP/IP sockets
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.1, action "start" failed.
dpkg: error processing postgresql-8.1 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql-contrib-8.2:
 postgresql-contrib-8.2 depends on postgresql-8.2; however:
  Package postgresql-8.2 is not configured yet.
dpkg: error processing postgresql-contrib-8.2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-plpython-8.2:
 postgresql-plpython-8.2 depends on postgresql-8.2; however:
  Package postgresql-8.2 is not configured yet.
dpkg: error processing postgresql-plpython-8.2 (--configure):
 dependency problems - leaving unconfigured
Setting up convmv (1.10-0.1) ...
Errors were encountered while processing:
 postgresql-8.2
 glom
 postgresql-8.1
 postgresql-contrib-8.2
 postgresql-plpython-8.2
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by MrMars on 2008-06-05
'localhost' is missing from /etc/hosts

```
sudo gedit /etc/hosts
```

where you have:

```
127.0.0.1 hostname.domainname hostname localhost
```

add localhost as above and try again.

---

