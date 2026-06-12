---
title: "apt update can't resolve security.ubuntu.com"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by tim.n9puz on 2006-12-21
My Ubuntu 6.06.1 LTS installation is getting an error when I run the command "sudo apt-get update".

The error reads:

Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
   Temporary failure resolving security.ubuntu.com

The contents of /etc/apt/sources.list are as follows:

# 
# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

## deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe



This is the only error I get when doing "sudo apt-get update". Everything else seems to be found and checked normally.

Ideas on what could be wrong?

Thanks,

Tim

---

### Post by bapoumba on 2006-12-21
> **tim.n9puz said:**
> 
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

Hi, you should uncomment these two ones, ie remove the # in front of the line  ;)

**sudo nano -B /etc/apt/sources.list**
The -B option will make a backup copy of the file with an ~ extension.
Edit the file, CTRL o to save (save name) and CRTL x to exit.

The run **sudo apt-get update again**.

---

### Post by scrooge_74 on 2006-12-21
Probably a server side problem or DNS problem, I few weeks ago some people had problems updating from servers in the US if they took out the "us" part from the server name they could update using other ubuntu servers

---

### Post by tim.n9puz on 2006-12-26
Thanks folks. The errors occurred today again but I won't panic yet since everything is running smoothly.

I did try using a web browser on the same network and I can look at the directories where apt says it can't open the files.

Tim

---

### Post by tim.n9puz on 2007-01-22
This is a followup post regarding the symptoms and the actual problem. Hopefully it will save someone else a little grief.

The original problem where apt could not always resolve the hosts was nothing to do with the machine itself or the repositories. Other periodic issues led me to track it down to a Linksys WRT-54G router where the nameserver addresses are stored. For reasons I don't understand other than the router is flaky it does not always translate the DNS server addresses properly.

Editing resolv.conf to explicitly add the nameservers of our ISP bypassing the router addresses has cured the problem and apt is working perfectly now.

Thanks to all who offered suggestions!

Tim

---

### Post by bapoumba on 2007-01-23
Thanks to you for posting your solution to this :)

---

