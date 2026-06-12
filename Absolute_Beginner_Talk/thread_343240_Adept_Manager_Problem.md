---
title: "Adept Manager Problem"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-01-21
For the third time, after a failed installation with Adept, it says:
> There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. 
The first time was when I tried to install MythTV, I forgot what I tried to install the second time, this time, I tried to install jabber.

This time, I closed Adept and opened it again then it said:
> You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.
I closed and reopened Adept but the message appeared again. I rebooted my laptop but the message came out again. What could be the problem?

---

### Post by garyinok on 2007-01-21
Hi.  I had the same problem and got the same error messages updating clamav.

I found the solution in the apt handbook in Ch 7  "common errors" at the following link: 

[http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html)

"If an installation breaks in the middle of the process and you find that it's no longer possible to install or remove packages, try running these two commands: 
     
# apt-get -f install
# dpkg --configure -a

 And then try again. It may be necessary to run the second of the above commands more than once. This is an important lesson for those adventurers who use `unstable'. 
 If you receive the error "E: Dynamic MMap ran out of room" when running apt-get update, add the following line to /etc/apt/apt.conf: 
    
 APT::Cache-Limit 10000000;"

I opened a Konsole terminal, started a root session and ran the apt-get and dpkg commands and was able to start Adept without the packaging system database error.

Hope this helps,
Gary

---

### Post by wersdaluv on 2007-01-21
> **garyinok said:**
> Hi.  I had the same problem and got the same error messages updating clamav.

I found the solution in the apt handbook in Ch 7  "common errors" at the following link: 

[http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html)

"If an installation breaks in the middle of the process and you find that it's no longer possible to install or remove packages, try running these two commands: 
     
# apt-get -f install
# dpkg --configure -a

 And then try again. It may be necessary to run the second of the above commands more than once. This is an important lesson for those adventurers who use `unstable'. 
 If you receive the error "E: Dynamic MMap ran out of room" when running apt-get update, add the following line to /etc/apt/apt.conf: 
    
 APT::Cache-Limit;"

I opened a Konsole terminal, started a root session and ran the apt-get and dpkg commands and was able to start Adept without the packaging system database error.

Hope this helps,
Gary

This is what happened after I entered sudo apt-get -f install:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libmono2.0-cil libice-dev libmono-data-tds2.0-cil exim4-config
  libmono-system-data2.0-cil libxv-dev libwxgtk2.4-1 kivio-data
  x11proto-xinerama-dev x11proto-render-dev x11proto-video-dev libxi-dev
  libxrender-dev mesa-common-dev libsgutils1 libmono-cairo2.0-cil
  libxcursor-dev libmono-security2.0-cil libmikmod2 x11proto-randr-dev
  dctrl-tools libmono-sqlite2.0-cil libmono-system-web2.0-cil
  x11proto-fixes-dev libmono-sharpzip2.84-cil libmono-corlib2.0-cil
  libipoddevice0 libtiffxx0c2 libxrandr-dev libavahi1.0-cil tk8.4 grep-dctrl
  exim4-base libxfixes-dev libxinerama-dev libwv2-1c2 libid3-3.8.3c2a
  libieee1284-3-dev libmono-system2.0-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mythtv-database (0.20-0.2ubuntu2) ...
Failed to connect to database: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.20-0.2ubuntu2); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-database
 mythtv
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This is what happened after I entered # dpkg --configure -a:
```
Setting up mythtv-database (0.20-0.2ubuntu2) ...
Failed to connect to database: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.20-0.2ubuntu2); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-database
 mythtv

```

What do I do now? Sorry. I'm very new with this

---

### Post by garyinok on 2007-01-23
I am new also.  I have using kubuntu for about a week.  I have used Suse/openSuse for some time but the package management is different. I just googled around and found something that worked for me. 

[COLOR="Red"]I had to execute the second command a couple of times before the package manager started working again.  The instructions on the link mentioned that you may have to do this more than once. [/COLOR] I have also had the same error installing some other packages and had to go through the same procedure each time.  It worked each time thought I had to run the second command a couple of times once before it worked.  Specifically I had problems installing an antivirus package called clamAV and also with an intrusion detection system called SNORT.  Both encountered problems that had to do with MySQL.  I removed clamAV.

I am not sure why this happens but I think it has something to do with the dpkg encountering an error and stopping in the middle of configuring a package being installed and leaving the database locked, so you have to fix it from the command line. 

I hope this helps.  At this point I have exhausted what little I know about it.

---

