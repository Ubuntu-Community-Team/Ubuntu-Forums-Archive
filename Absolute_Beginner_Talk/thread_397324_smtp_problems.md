---
title: "smtp problems"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by rman on 2007-03-30
I recently installed ubuntu server 6.10 and Nagios 3.0a1. I managed, after much effort to get Nagios to monitor a couple of my servers and can check it via the web interface. My next step was to get email notifications to work. I'm new to Linux and dumber than a stump. I decided I needed to use Postfix and downloaded and installed the package with apt-get. I was having problems and at some point decided to remove it with apt-get. After removal, I noticed there were some files left behind in /etc/postfix and deleted them. I tried some other things and decided to go back to post fix. When I try to reinstall the package I get the following message:

[COLOR="Blue"]root@helnag:~# apt-get install postfix
Reading package lists... Done
Building dependency tree
Reading state information... Done
postfix is already the newest version.
The following packages were automatically installed and are no longer required:
  libgtk2.0-common libatk1.0-0 liblaunchpad-integration0 libxfixes3
  libx11-data scrollkeeper docbook-xml libxslt1.1 libcairo2 libfontconfig1
  fontconfig-config xml-core libpango1.0-common fontconfig libxau6
  libpango1.0-0 libgtk2.0-bin libxft2 launchpad-integration libvte9 libice6
  libxdmcp6 libxml2 libglade2-0 libxrender1 sgml-base ucf libtiff4 libpng12-0
  ttf-dejavu libjpeg62 libfreetype6 libglib2.0-0 sgml-data libx11-6 libsm6
  libxi6 libcupsys2 libxcursor1 libxinerama1 libvte-common libxext6 defoma
  libscrollkeeper0 libxrandr2 libgtk2.0-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up postfix (2.3.3-1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).[/COLOR]

Can anyone tell me how to get out of this fix? Bear in mind I am essentially Linux illiterate.

---

### Post by acormack on 2007-03-30
If you type 

sudo apt-get remove postfix 

what happens?

---

### Post by rman on 2007-03-30
Thanks for your reply! These are the messages that come up. If I do an install again, I get the errors from my first post.

root@helnag:/usr/local/nagios/etc# apt-get remove postfix
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtk2.0-common libatk1.0-0 liblaunchpad-integration0 libxfixes3 postfix libx11-data scrollkeeper docbook-xml libxslt1.1 libcairo2 libfontconfig1
  fontconfig-config xml-core libpango1.0-common fontconfig libxau6 libpango1.0-0 libgtk2.0-bin libxft2 launchpad-integration libvte9 libice6 libxdmcp6
  libxml2 libglade2-0 libxrender1 sgml-base ucf libtiff4 libpng12-0 ttf-dejavu libjpeg62 libfreetype6 libglib2.0-0 sgml-data libx11-6 libsm6 libxi6
  libcupsys2 libxcursor1 libxinerama1 libvte-common libxext6 defoma libscrollkeeper0 libxrandr2 libgtk2.0-0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  postfix
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 2494kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 20552 files and directories currently installed.)
Removing postfix ...
 * Stopping Postfix Mail Transport Agent postfix                                                                                                       [ ok ]
root@helnag:/usr/local/nagios/etc#

---

### Post by acormack on 2007-03-30
if you run 

apt-get remove postfix

then run it again immediately

apt-get remove postfix

does it say postfix is not installed?

---

### Post by rman on 2007-03-30
root@helnag:/usr/local/nagios/etc# apt-get remove postfix
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package postfix is not installed, so not removed

---

### Post by acormack on 2007-03-30
Hmmmm how about

apt-get install postfix

then

apt-get --reinstall install postfix

what is the output then?

---

### Post by rman on 2007-03-30
Essentially the same thing:

root@helnag:/usr/local/nagios/etc# apt-get --reinstall install postfix
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtk2.0-common libatk1.0-0 liblaunchpad-integration0 libxfixes3 libx11-data scrollkeeper docbook-xml libxslt1.1 libcairo2 libfontconfig1
  fontconfig-config xml-core libpango1.0-common fontconfig libxau6 libpango1.0-0 libgtk2.0-bin libxft2 launchpad-integration libvte9 libice6 libxdmcp6
  libxml2 libglade2-0 libxrender1 sgml-base ucf libtiff4 libpng12-0 ttf-dejavu libjpeg62 libfreetype6 libglib2.0-0 sgml-data libx11-6 libsm6 libxi6
  libcupsys2 libxcursor1 libxinerama1 libvte-common libxext6 defoma libscrollkeeper0 libxrandr2 libgtk2.0-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up postfix (2.3.3-1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Stopping Postfix Mail Transport Agent postfix                                                                                                       [ ok ]
 * Starting Postfix Mail Transport Agent postfix                                                                                                              postfix: fatal: /etc/postfix/postfix-script: No such file or directory
                                                                                                                                                       [fail]
invoke-rc.d: initscript postfix, action "restart" failed.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@helnag:/usr/local/nagios/etc#

When I mess things up, I do a good job, huh?

---

### Post by acormack on 2007-03-30
Very interesting!

I am sure the clue must be the deleting of the /etc/postfix dir.  Was that the only directory you deleted?

Please try running these commands on your computer and comparing the output with mine shown below:


**sudo ls -ld /etc/postfix**
drwxr-xr-x 3 root root 4096 2006-12-01 10:56 /etc/postfix

**sudo ls -l /etc/postfix**
total 72
-rw-r--r-- 1 root root   318 2006-11-26 04:42 dynamicmaps.cf
-rw-r--r-- 1 root root  1148 2006-11-26 04:42 main.cf
-rw-r--r-- 1 root root  4011 2006-11-26 04:42 master.cf
-rw-r--r-- 1 root root 17562 2006-06-08 09:22 postfix-files
-rwxr-xr-x 1 root root  6836 2006-06-08 09:22 postfix-script
-rwxr-xr-x 1 root root 22018 2006-06-08 09:22 post-install
-rw------- 1 root root  1024 2006-12-01 10:56 prng_exch
drwxr-xr-x 2 root root  4096 2006-06-08 09:22 sasl



Alec

---

### Post by rman on 2007-03-30
This is my output:

root@helnag:/etc/init.d# sudo ls -ld /etc/postfix
drwxr-xr-x 3 root root 4096 2007-03-30 15:26 /etc/postfix


root@helnag:/etc/init.d# sudo ls -l /etc/postfix
total 16
-rw-r--r-- 1 root root  318 2007-03-26 11:02 dynamicmaps.cf
-rw-r--r-- 1 root root 1227 2007-03-30 11:53 main.cf
-rw-r--r-- 1 root root 3968 2007-03-26 11:02 master.cf
drwxr-xr-x 2 root root 4096 2006-09-10 05:48 sasl

It appears I am missing the following:
postfix-files
postfix-script
post-install
prng_exch

The /etc/postfix directory was the only thing I deleted. Leave it to me to foul things up.

---

### Post by acormack on 2007-03-30
Try unzipping this in the directory

---

### Post by rman on 2007-03-30
I used pftp to upload it to my server directory. I hate to admit it, but I don't know how to unzip it now that it's there. I one of those gasp! Windows people who doesn't know much but point and click.

---

### Post by acormack on 2007-03-30
cd /etc/postfix
sudo unzip {zipfilename}

---

### Post by rman on 2007-03-30
Yes - figured it out while I was waiting for your reply. I did an apt-get install postfix and received no errors.


root@helnag:/etc/postfix# unzip pfix.zip
Archive:  pfix.zip
  inflating: post-install
  inflating: postfix-script
  inflating: postfix-files
 extracting: prng_exch
root@helnag:/etc/postfix# apt-get install postfix
Reading package lists... Done
Building dependency tree
Reading state information... Done
postfix is already the newest version.
The following packages were automatically installed and are no longer required:
  libgtk2.0-common libatk1.0-0 liblaunchpad-integration0 libxfixes3 libx11-data scrollkeeper docbook-xml libxslt1.1 libcairo2 libfontconfig1
  fontconfig-config xml-core libpango1.0-common fontconfig libxau6 libpango1.0-0 libgtk2.0-bin libxft2 launchpad-integration libvte9 libice6 libxdmcp6
  libxml2 libglade2-0 libxrender1 sgml-base ucf libtiff4 libpng12-0 ttf-dejavu libjpeg62 libfreetype6 libglib2.0-0 sgml-data libx11-6 libsm6 libxi6
  libcupsys2 libxcursor1 libxinerama1 libvte-common libxext6 defoma libscrollkeeper0 libxrandr2 libgtk2.0-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up postfix (2.3.3-1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Stopping Postfix Mail Transport Agent postfix                                                                                                       [ ok ]
 * Starting Postfix Mail Transport Agent postfix 
root@helnag:/etc/postfix#

That seems to have done it. Thank you so much for your help. You have no idea how much I appreciate it. I'm a Windows Server Administrator for a large state agency and much of what I do seems really easy and routine. This Linux/Nagios project has been a real challenge, but it's been fun so far also. Thanks a million!:) :)

---

### Post by acormack on 2007-03-30
Glad it worked.  It is well worth the effort of learning LINUX.   There is some great free software out there!

Depending what your eventual need for the email server is I would also consider Scalix as a mail server.  It is a complete replacement for Exchange.

Postfix is excellent for just smtp mail though!!

Alec

---

### Post by rman on 2007-03-30
I don't need too much in the way of a mail server. The Nagios application uses a small client piece called nsclient++ that is installed on each Windows server. It uses smtp mail to send notifications when it detects a problem with a Windows Server host. I don't even really need to receive mail. Since the Linux server is behind our firewall, I should be able to configure it so it will send emails directly to me and other members in the admin group through our Lotus Notes mail server.

I have to agree with you on the great free software. Nagios, when it's properly configured, is a great package for monitoring Windows as well as other OSs. We have a working version that was set up by a young guy who used to work here. It works great, but was installed on an old pc that is short on resources. It's also running old versions of the OS (Fedora Core 4) and a fairly old version of Nagios.  The guy who set it up left for greener pastures and I felt like I needed to install it on a real server and update everything. I didn't have much luck with Fedora Core 6 and decided to try Ubuntu. Other than a little different directory structure that has given me fits at times, I like it a lot.

Again,  I really appreciate all your help. I've tried to do this all on my own by Googling all my questions. For the most part, that has worked well. This PostFix thing really stumped me though. Hopefully I won't make the same mistake again!

---

