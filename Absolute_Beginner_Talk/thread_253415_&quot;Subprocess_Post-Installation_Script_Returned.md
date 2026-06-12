---
title: "&quot;Subprocess Post-Installation Script Returned Error, Exit Status 1&quot;?"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by martinfierro on 2006-09-08
Hi all from an Ubuntu nUUb;

The Updates feature had been working fine for me on Ubuntu 6.06 until this week.

Now when I'm notified of updates I click on the orange Updater button, choose "Download package files" and am told that ubuntu is "Installing Software."

But then I get the following error message: 

"E: NDAS-Admin Subprocess Post-Installation Script Returned Error, Exit Status 1"

But then when I acknowledge this message, Ubuntu appears to check the installation and indicates everything is OK.

I also got this error message when using Synaptic to try & install a TV driver on my ATI video card (TV driver didn't fully install).

Help! How to correct this error message?

---

### Post by davmac on 2006-09-08
Hi,

If you open up a terminal window (Applications/Accessories/Terminal) and type "sudo apt-get update" and "sudo apt-get upgrade" without the quotes, what response do you get?

Dave Mac

---

### Post by martinfierro on 2006-09-08
> **davmac said:**
> Hi,

If you open up a terminal window (Applications/Accessories/Terminal) and type "sudo apt-get update" and "sudo apt-get upgrade" without the quotes, what response do you get?

Dave Mac

Typing sudo apt-get update yields:

Password:
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Fetched 32B in 1s (18B/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_dapper_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


Typing sudo apt-get upgrade yields:

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? [YES]
Setting up ndas-admin (1.0.2-24) ...
 System startup links for /etc/init.d/ndas already exist.
Starting NDAS: failed to load sal module
 Report this problem with the following messages at [http://code.ximeta.com/cgi-bin/trac.cgi/newticket](http://code.ximeta.com/cgi-bin/trac.cgi/newticket)
==============================================================================
Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
ls: /lib/modules/*/kernel/drivers/block/ndas/*: No such file or directory
/etc/init.d/ndas: line 88: gcc: command not found
==============================================================================
dpkg: error processing ndas-admin (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ndas-admin
E: Sub-process /usr/bin/dpkg returned an error code (1)


What does all this mean in nUUb? :confused: :)

---

### Post by davmac on 2006-09-09
Hi,

It looks like a problem with ndas-admin. No idea what this is but after a bit of googling I found [http://code.ximeta.com/trac-ndas/ticket/147](http://code.ximeta.com/trac-ndas/ticket/147) which describes exactly the same problem.

According to this thread it is because ndas-admin requires the 686 kernel (for a modern processor) whereas ubuntu comes with a kernel for 386 as standard.

Assuming that you have a 686 chip in your machine you can correct this by typing "sudo apt-get update" followd by "sudo apt-get install linux-image-2.6.15-26-686". You'll need to restart your system for changes to take effect.

Please make sure you've got your system backed up before you start this though.

Hope this helps,

Dave Mac

---

### Post by Derspankster on 2006-12-09
I have a similar problem with Samba. Can't seem to reinstall and it appears that samba was never fully installed. Here's my output - **sudo apt-get upgrade**

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  automatix2
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 205kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main automatix2 1.1-2.3-6.10edgy_i386 [205kB]
Fetched 205kB in 2s (95.5kB/s)     
(Reading database ... 98097 files and directories currently installed.)
Preparing to replace automatix2 1.1-2.2-6.10edgy_i386 (using .../automatix2_1.1-2.3-6.10edgy%5fi386_i386.deb) ...
Unpacking replacement automatix2 ...
Setting up samba (3.0.22-1ubuntu4) ...
 * Starting Samba daemons...                                                     [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Setting up automatix2 (1.1-2.3-6.10edgy_i386) ...
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by chillicrab on 2007-02-12
I had the same problem with the msg "Starting NDAS: failed to load sal module". Problem seems to be because NDAS I installed requires the 2.6.17_10 kernel whereas I actually booted with the 2.6.17_11 kernel. A reboot with the 2.6.17_10 kernel helped and I could install the ndas_admin package.

cheers

---

### Post by borris.morris on 2007-02-17
same here with samba.

---

