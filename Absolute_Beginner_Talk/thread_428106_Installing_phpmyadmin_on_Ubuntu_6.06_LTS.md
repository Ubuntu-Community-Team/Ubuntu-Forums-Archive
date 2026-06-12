---
title: "Installing phpmyadmin on Ubuntu 6.06 LTS"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by brz3rk on 2007-04-30
Hi. I'm trying to follow these instructions:

[http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html](http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html)

and I'm stuck on#19 - installing phpmyadmin.  It keeps saying "E: Couldn't find package phpmyadmin" and I found out that it's trying to read the cdrom drive which I thought I commented out.  Below is the source.list file:


#
## deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


## deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


I'm sure it's a real easy fix.  I've searched the forums and couldnt' find anything.  Any assistance would be greatly appreciated.

---

### Post by neouser99 on 2007-04-30
did you do an ```
apt-get update
``` after you commented the line out?

-neo

---

### Post by brz3rk on 2007-04-30
Yes, many times.  Here's what it's saying:


Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Sun Apr 29 20:59:27 2007 from 192.168.1.2
r0d@ubun2:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied  )
E: Unable to lock the list directory
r0d@ubun2:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 3B in 1s (2B/s)
Reading package lists... Done
r0d@ubun2:~$ sudo apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package phpmyadmin
r0d@ubun2:~$

---

### Post by Bachstelze on 2007-04-30
You need to use sudo...

---

### Post by brz3rk on 2007-04-30
Can you please elaborate?

I tried sudo apt-get install phpmyadmin and it's coming back with that error.

---

### Post by got_nix on 2007-04-30
uh. dude.. really just go to sourceforge and download php myadmin.. I assume you've already installed and configure php mysql and apache. if so you may just unzip your php myadmin folder in your public html dir (provided you have enabled serving from public_html in your home dir) in your apache2.conf file. after doing that

type [http://localhost/~homedirname/phpMyAdmin](http://localhost/~homedirname/phpMyAdmin) and there you go

---

### Post by az on 2007-04-30
> **got_nix said:**
> uh. dude.. really just go to sourceforge and download php myadmin.. 

Don't do that.  You will not benefit from updates and bug fixes and forget about upgrading your system


Phpmyadmin is in universe.  You need to enable that repo.


These two lines:



# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe



# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Remove the # in front of them and run

sudo apt-get update

---

### Post by brz3rk on 2007-04-30
Thanks AZ, it worked and it looks like phpmyadmin is installed :)


Now I'm getting the same error, "E: Couldn't find package phpmyadmin" on step 21, installing TorrentFlux running the command "sudo apt-get install torrentflux".  Can anyone help me with that or should I start another post? :(

---

### Post by az on 2007-04-30
In Dapper, it is only available in the dapper-backports repo

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=torrentflux](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=torrentflux)

---

### Post by brz3rk on 2007-05-01
So I've managed to download what I think the latest version is - torrentflux_2.3 and I've managed to extract it into its' directory.  My problem is installing it and I'm not really sure where or how to do that.

Do I have to install the extracted file or do I just run something that was extracted?? or... ?

---

### Post by az on 2007-05-01
Just use the version in the dapper-backports repo.  You don't want to install stuff by hand unless you know what ou are doing.

If you stick to the repos, you will not have trouble upgrading and keeping-up-to-date.

---

