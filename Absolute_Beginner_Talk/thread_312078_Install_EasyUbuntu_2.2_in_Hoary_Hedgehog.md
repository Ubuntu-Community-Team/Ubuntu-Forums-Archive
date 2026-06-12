---
title: "Install EasyUbuntu 2.2 in Hoary Hedgehog"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by fossmule on 2006-12-03
Hi,
I'm a real newbie with Linux. I installed Ubuntu Hoary Hedgehog on my computer and I'm trying to setup EasyUbuntu 2.2. However, I'm experiencing some difficulties.

I was able to download the application to my desktop using the following link.
[http://applications.linux.com/article.pl?sid=06/03/23/1653209&tid=47](http://applications.linux.com/article.pl?sid=06/03/23/1653209&tid=47)

Next I opened up terminal and typed the following two commands (no problems here)

cd Desktop
tar -zxf EasyUbuntu-2.2beta.tar.gz

Next I tried to run the following command

sudo ./EasyUbuntu.sh

Next I am asked for my password - i enter the password and I get the following message "command not found"

I think that the program is supposed to start when I put in my password but i'm not sure why it won't work. (i also used the command "sudo passwd root" to reset my password so i'm sure that I"m entering it correctly)

any help or advice would be very much appreciated

thanks in advance,

fossmule

---

### Post by dbd on 2006-12-04
I'm not sure, but I don't think that Easy Ubuntu supports Hoary, it doesn't mention it here:
[http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)
Hoary is very old (over 20 months) and is no longer supported, it may be worth upgrading to the latest version of Ubuntu, to find out how look here:
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)
(Be sure to read carefully).

Currently you have to upgrade one version at a time, so to get the latest version you'd have to upgrade from Hoary to Breezy, Breezy to Dapper and Dapper to Edgy. So it may be worth just doing a new clean install from a Edgy CD, just make sure you don't have any data you want to keep on the partitions it formats.

Good luck

dbd

---

### Post by fossmule on 2006-12-04
dbd,

thanks for your advice- i am using hoary because i happened to have an old copy- haven't had a chance to get the latest version- hopefully when i upgrade it will work-

thanks again,
fossmule

---

