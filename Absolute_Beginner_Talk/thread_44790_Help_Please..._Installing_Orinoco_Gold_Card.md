---
title: "Help Please... Installing Orinoco Gold Card"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by jabaman21 on 2005-06-27
Well...I dont know literally anything about linux, though I did manage to install Ubuntu without any problems...

I want to install my Orinoco Gold Card in Ubuntu on my laptop so that I can use WiFi, but I absolutely don't know how...

Could someone please help me with this....

I have my Terminal Window open in Ubuntu, and I would really appreciate some help on what exactly what commands I need to use to download the drivers (from where and how) and to install them and get my Orinoco Gold Card working in Ubuntu....

Please help..

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=jabaman21]Well...I dont know literally anything about linux, though I did manage to install Ubuntu without any problems...

I want to install my Orinoco Gold Card in Ubuntu on my laptop so that I can use WiFi, but I absolutely don't know how...

Could someone please help me with this....

I have my Terminal Window open in Ubuntu, and I would really appreciate some help on what exactly what commands I need to use to download the drivers (from where and how) and to install them and get my Orinoco Gold Card working in Ubuntu....

Please help..[/QUOTE]

Let me just say- you have a real gold card? I am jealous. These cards have the best Linux support out of any (if it is a real gold card....they sell fakes on ebay).

Just plug it in....reboot and go to "system" "administration" and "networking" to configure and activate the card. Drivers load automatically.

Following this guide will allow you to use kismet on that card:

[http://www.ubuntuforums.org/showthread.php?t=23596&highlight=kismet](http://www.ubuntuforums.org/showthread.php?t=23596&highlight=kismet)

THE BEST ACCESS POINT FINDING SOFTWARE ON THE PLANET

Let me say again I am jealous.

---

### Post by jabaman21 on 2005-06-27
Yes, I have a "real" Gold Orinoco 11b/g card...I bought it online from Dell.com

Thanks.

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=jabaman21]Yes, I have a "real" gold card...I bought it online from Dell.com

Thanks.[/QUOTE]


Nice....Nice....Nice....did my directions work?

---

### Post by jabaman21 on 2005-06-27
I am about to load up Ubuntu and try your directions....

---

### Post by jabaman21 on 2005-06-27
It worked! 

Thank you so much!

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=jabaman21]It worked! 

Thank you so much![/QUOTE]

No problem. Today you learned how great it is when you have good hardware!

---

### Post by jabaman21 on 2005-06-27
I clicked on that link above about installing kismet to use with my Orinoco Gold Card and I followed the instructions...

After I used the "wget" command to download kismet... I used the next command listed in the tutorial which is "apt-get install ethereal-common" and following commands that come next....and none of them seem to work because I get errors.... I have posted my install log below :


root@VOORHEES:~# apt-get install ethereal-common
Reading package lists... Done
Building dependency tree... Done
Package ethereal-common is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ethereal-common has no installation candidate
root@VOORHEES:~# dpkg -i kismet_2005.04.R1-1_i386.deb
(Reading database ... 58189 files and directories currently installed.)
Preparing to replace kismet 2005.04.R1-1 (using kismet_2005.04.R1-1_i386.deb) ...
Unpacking replacement kismet ...
dpkg: dependency problems prevent configuration of kismet:
 kismet depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 kismet depends on libgmp3; however:
  Package libgmp3 is not installed.
 kismet depends on ethereal-common; however:
  Package ethereal-common is not installed.
dpkg: error processing kismet (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kismet
root@VOORHEES:~# apt-get install linux-source-2.6.10 build-essential
Reading package lists... Done
Building dependency tree... Done
Package linux-source-2.6.10 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-source-2.6.10 has no installation candidate





Please help..

---

### Post by poofyhairguy on 2005-06-27
Try this first

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

then

> sudo apt-get update

>  sudo apt-get install linux-source-2.6.10 build-essential kismet

---

