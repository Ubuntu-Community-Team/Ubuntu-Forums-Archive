---
title: "Automatix2 Error"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by crittertoo on 2007-07-04
Hi there,

I am a total newbie to LINUX. Just installed Automatix2. Tried to download various software via Automatix2 but I encounter the same error every time - 

Copied from the LOG :-

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  menu menu-xdg pdmenu
0 upgraded, 3 newly installed, 0 to remove and 72 not upgraded.
Need to get 466kB of archives.
After unpacking 2081kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  menu menu-xdg pdmenu
E: There are problems and -y was used without --force-yes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcompress-zlib-perl libio-zlib-perl
Suggested packages:
  libio-string-perl
The following NEW packages will be installed:
  arj lha libarchive-tar-perl libarchive-zip-perl libarchive1 libcompress-zlib-perl
  libio-zlib-perl p7zip p7zip-full rar unace unrar unzoo
0 upgraded, 13 newly installed, 0 to remove and 72 not upgraded.
Need to get 2910kB of archives.
After unpacking 7795kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  arj lha libcompress-zlib-perl libio-zlib-perl libarchive-tar-perl
  libarchive-zip-perl libarchive1 p7zip p7zip-full rar unace unrar unzoo
E: There are problems and -y was used without --force-yes
received

!!SCRIPT OUTPUT END!!
[07/04/2007 - 14:04.23] - ERRORS OR WARNINGS WHERE REPORTED
[07/04/2007 - 14:04.23] - FATAL - Debian Menu - An apt-based error occurred and installation was unsuccessful
[07/04/2007 - 14:04.23] - FATAL - Archiving Tools - An apt-based error occurred and installation was unsuccessful

Help please - thanks

---

### Post by waggygee on 2007-07-04
Try add this in you terminal "apt-get autoclean" press enter then type "apt-get update" then lastly "apt-get upgrade." I had the exact same problems when I got Ubuntu. If those commands don't work please post what response you got on the terminal. Have a look at these forums I started [http://ubuntuforums.org/showthread.php?t=461883](http://ubuntuforums.org/showthread.php?t=461883) , [http://ubuntuforums.org/showthread.php?t=438890](http://ubuntuforums.org/showthread.php?t=438890) .
I got rid of this problem but I forgot what exactly I did, so let's work on it together

---

### Post by crittertoo on 2007-07-04
thanks for the reply. Tried apt -get autoclean but it comes back with

-ubunto:~$ apt-get autoclean
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory

Learning curve for Linux is really steep.:)

Does anyone knows the default password for su or root?

I cannot recall the installation asking me for the root or su password. When I try to install rpm's...i cant't get su rights :(

thanks

---

### Post by Southtown on 2007-07-04
Try:```
sudo apt-get autoclean
```

---

### Post by alienexplorers on 2007-07-04
The default password for sudo & gksudo is your password.

---

### Post by waggygee on 2007-07-04
> **crittertoo said:**
> thanks for the reply. Tried apt -get autoclean but it comes back with

-ubunto:~$ apt-get autoclean
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory

Learning curve for Linux is really steep.:)

Does anyone knows the default password for su or root?

I cannot recall the installation asking me for the root or su password. When I try to install rpm's...i cant't get su rights :(

thanks

Try it using the root terminal

---

### Post by crittertoo on 2007-07-04
sudo apt-get autoclean, update and upgrades works.Automatix2 works now...thanks

I kinda understand what sudo does. But if i want to login as su what do i do?

Tried to go terminal. Key in su...key in the password but it fail. Any guides?

thanks.....it's a great forum to learn

---

### Post by crittertoo on 2007-07-04
got it...sudo su.

Can someone please direct me on how to obtain the lotus linux client installation file -  C93D1NA.zip

Tried IBM....search can't find that file. Tried Partnerworld....too complex to navigate for a non tech like me....

thanks

---

