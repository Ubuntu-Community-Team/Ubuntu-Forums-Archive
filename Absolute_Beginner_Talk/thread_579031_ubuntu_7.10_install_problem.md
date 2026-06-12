---
title: "ubuntu 7.10 install problem"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-10-17
just now ,i tried to upgrade  Gutsy Gibbon from ubuntu 7.04
i see below link , and follow the instruction 
  [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)
  
in terminal  
  >sudo apt-get update
  System>Administration>Update Manager
 
  after pressing 'check' button ,i did't not get "New Distribution 7.10 is available" bar....

so i tried like this 
  >sudo nano /var/lib/update-manager/meta-release(this file is not available....so )
  >locate /update-manager/meta-release
  /old1/var/lib/update-manager/meta-release
  >sudo nano /old1/var/lib/update-manager/meta-release 
  
after that i add these in last line

Dist: gutsy
Name: Gutsy Gibbon
Version: 7.10
Date: Thu, 18 Oct 2007 12:00:00 UTC
Supported: 0
Description: This is the 7.10 release
Release-File: [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release)
ReleaseNotes: [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/ReleaseAnnouncement](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/ReleaseAnnouncement)
UpgradeTool: [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz)
UpgradeToolSignature: [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz.gpg)



after save 'meta-release'
>sudo apt-get update
>gksudo "update-manager -c -d"
now "Update Manager" is open and "New Distribution 7.10 is available" .
i click 'Upgrade' button

"Distribution upgrade window" was opened
now all are going smoothly...
after some time in "Upgrading ubuntu to version 7.20" popup window error occured  ,see below
 
Preparing the upgrade                  -->ok
Modifying the software channels -->error occured
Fetching the upgrades                  
Installing the upgrades
Cleaning Up
Restarting the system

at error time "Error during update" popup window was opened, below is that details
-----------------------------------------------------------------------------------------------------
Error during update(this is title...)
    #heading is.....
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
   #the error message inside the text area ....
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
---------------------------------------------------------------------------------------
             #this is the terminal output
tide@my-UBUNTU704:~$ gksudo "update-manager -c -d"
warning: could not initiate dbus
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
extracting '/tmp/tmp2Az5TG/gutsy.tar.gz'
authenticate '/tmp/tmp2Az5TG/gutsy.tar.gz' against '/tmp/tmp2Az5TG/gutsy.tar.gz.gpg' 
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
tide@my-UBUNTU704:~$

i tried 3 times same error occurred at all time...
any help ....


thank you

---

### Post by alienexplorers on 2007-10-17
You should do a complete install from scratch.  I tried upgrading and ended up with a OS I could not use.  Went and did the full install from scratch and now everything works.

---

### Post by antharr on 2007-10-18
I tried the install from scratch on my system and it didn't work. My system will take a Feisty install....no problem but will not accept a Gusty install.

---

### Post by ronald.higgins on 2007-10-18
The installer is failing to retrieve the necessary packages.

Did you have connectivity at the time of the update?

Can you ping the host in.archive.ubuntu.com ?

PING in.archive.ubuntu.com (91.189.88.31) 56(84) bytes of data.
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=0 ttl=49 time=157 ms

---

### Post by mokkai on 2007-10-19
i tried after sometime, it was connected .
now ubuntu7.10 is installed.
thank you everyone

---

