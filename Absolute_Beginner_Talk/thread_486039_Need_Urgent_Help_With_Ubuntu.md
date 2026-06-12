---
title: "Need Urgent Help With Ubuntu"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by cranshinibon on 2007-06-27
Alright, I am in class right now (Network Security) and i forget how to work linux since I haven't used it in forever.

At the moment I have Ubuntu 5.10 installed and I have to do the following.

Install Linux Server operating system and have all updates installed

Perform installation of Linux servers:
1. Initial OS install completed
2. Clam Anti-Virus Installed
3. Webmin Installed
4. FTP, HTTP, NFS installed and configured

Configuring your Linux server automatic updates

Download the latest "Yum" rpm package, and configure it to auto-update your system.

1. Download Yum rpm package
2. Perform initial update through yum
3. Configure yum to auto-update daily

Right now I just installed the yum.tar.gz but for some reason I can't remember the command to start it outside of being root.

So my question is:

1. How do you start a program in Konsole without being root? (command)
2. How do you install Webmin?
3. How do you set up and configure FTP, HTTP, and NFS?
4. How do you correctly install ClamAV and Yum and configure them to be able to run?

---

### Post by ITdrummer on 2007-06-27
Version 5.10? 
wow! ever thought about upgrading?

---

### Post by FleetAdmiral74 on 2007-06-27
I agree, defiantly upgrade first.

---

### Post by cranshinibon on 2007-06-27
oops sorry i just checked and it's 7.04

---

### Post by tmatt95 on 2007-06-27
1. How do you start a program in Konsole without being root? (command)
I think the command you are looking for is "sudo"

2. How do you install Webmin?
"sudo apt-get install webmin" 
(taken from: [http://ubuntuforums.org/showthread.php?t=483220&highlight=installing+webmin](http://ubuntuforums.org/showthread.php?t=483220&highlight=installing+webmin) )

3. How do you set up and configure FTP, HTTP, and NFS?
Once webmin is installed you can set up the FTP access over the Internet. I experienced some problems getting php to work but those are all explained in this link below:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by cranshinibon on 2007-06-27
> **tmatt95 said:**
> 1. How do you start a program in Konsole without being root? (command)
I think the command you are looking for is "sudo"

2. How do you install Webmin?
"sudo apt-get install webmin" 
(taken from: [http://ubuntuforums.org/showthread.php?t=483220&highlight=installing+webmin](http://ubuntuforums.org/showthread.php?t=483220&highlight=installing+webmin) )

3. How do you set up and configure FTP, HTTP, and NFS?
Once webmin is installed you can set up the FTP access over the Internet. I experienced some problems getting php to work but those are all explained in this link below:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

First off, thank you so much for taking the time to help me.

I tried starting yum to configure the auto update and for some reason i can't get it to open up the gui for yum. i don't know the other command with "sudo yum" to get the gui to pop up.

im currently downloading webmin at the moment i will update when all goes through

also, with the same predicament as yum i can't seem to get clamav to open up in the gui. and when i try and sudo freshclam it says it's out of date and i don't know how to update it.

---

### Post by cranshinibon on 2007-06-27
Update on the following

Clam AV:

:/$ sudo freshclam

Clam AV update process started at Wed Jun 27 15:21:41 2007
WARNING! Your ClamAV installation is OUTDATED!
WARNING! Local version: 0.90.2 Recommended version 0.90.3
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cvd is up to date (version: 43, sigs: 104500, f-level: 14, builder: sven)
daily.cvd is up to date (version 3542, sigs: 26150, f-level: 16, builder :ccordes)

:/$

Webmin:

:/$sudo apt-get install webmin

Reading package lists. . .  Done
Building dependency tree
Reading state information. . . Done
Package webmin is not available,but is referred to oby another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package webmin has no installation canditate

:/$

---

### Post by cranshinibon on 2007-06-27
ok webmin works fine but one of my fellow classmates stated that you can't use yum in ubuntu that yum is for redhat/fedora distros. 

what can i use to be able to auto update my system daily

---

### Post by BlackMeTaL on 2007-06-27
For normal updates:
sudo apt-get update && sudo apt-get -y upgrade

For more serious upgrades :)
sudo apt-get update && sudo apt-get -y dist-upgrade

You can make a cron job to do it once a day. You can put a script in /etc/cron.daily

---

