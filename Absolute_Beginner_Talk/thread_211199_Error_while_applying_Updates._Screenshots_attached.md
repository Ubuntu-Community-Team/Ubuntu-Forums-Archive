---
title: "Error while applying Updates. Screenshots attached."
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by 5tudent on 2006-07-07
Hi,

I am Linux newbie and I recently installed Ubuntu Dapper 6.06. 

Today when I applied the updates for Ubuntu, I received an error about a duplicate entry in my sources.list file. 

Please find enclosed a copy of my sources.list and a screenshot of the error. The files are names 5tudent_sources.list, 5tudent_screenshot.png 

Please advise. 

Thanks.

---

### Post by kd7swh on 2006-07-07
you can edit the content of sources.list with any text editor.
log in as root and remove the duplicates.

I think the sources list is in /etc/apt

---

### Post by Apple 101 on 2006-07-08
You should login normally, but in a terminal activate root priviliges.
[I]
gksudo gedit /etc/apt/sources.list[/I]

---

### Post by jan on 2006-07-08
I do sudo gedit /etc/apt/sources.list

---

### Post by richbarna on 2006-07-08
> **jan said:**
> I do sudo gedit /etc/apt/sources.list

You should use gksudo for graphical programs in gnome and kdesu in kde.
Google ICE.authority to see problems this has caused, and read this excellent guide by aysiu :- [http://www.psychocats.net/ubuntu/graphicalsudo.php](http://www.psychocats.net/ubuntu/graphicalsudo.php)

---

### Post by 5tudent on 2006-07-08
kd7swh, Apple 101, Jan, Richbarna:

Thanks for your reply. I do not understand as to which entry to correct.

The error says:
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)

However I do NOT have such lines in my sources.list file. The contents of the file are:

#########################################################################
## ChangeLog:
## Date		: 06/24/2006
## Note		: I wanted to add safe repositories. 
##		  Hence, I commented the contents of this file by prefixing each line with ##<tab>.		
##		  Then, I added new contents based on the recommendation of
##	[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)
##
##The site says that Backports and PLF repositories are unsupported and that they
##		  may contain illegal packages. To be on safer side, I have commented the lines
##		  referring to those repositories.
#########################################################################

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
##	
##	## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
##	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
##	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
##
##	## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
##	deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
##	deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free 
##	


I am a new to Linux. Hence please tell me which entry I should correct. Please tell me as to what the new entry should be. 

Thanks.

---

### Post by Apple 101 on 2006-07-08
Open Synaptic --> Find the Repositories area (in one of the menus) --> Select Universe and/or the other repositories you want --> Reload

---

