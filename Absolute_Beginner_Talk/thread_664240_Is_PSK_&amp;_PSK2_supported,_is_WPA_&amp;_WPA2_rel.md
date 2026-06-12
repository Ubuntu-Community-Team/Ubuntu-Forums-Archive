---
title: "Is PSK &amp; PSK2 supported, is WPA &amp; WPA2 related"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by iceman0304 on 2008-01-10
My router only supports WEP,PSK pers., PSK ent., PSK2 pers., PSK2 ent. no WPA..

Need to find out if ubuntu can support the PSK's

Does PSK relate to WPA?

This is a Linksys Router WRT350N

---

### Post by wieman01 on 2008-01-11
That really depends on the wireless adapter (client) you have got. This has less to do with the router. 

A lot of wireless adapters/cards do work with WPA support out of the box, but some don't. What wireless card have you got?

PSK does relate to WPA. PSK2 might mean WPA2-PSK which is an even more advanced option than WPA-PSK. This basically lets you use WPA2 by entering a "pre-shared key" which is nothing but a secred password.

Let us know what hardware you have got and what version of Ubuntu you plan to run.

---

### Post by mandrill on 2008-01-11
psk2 personal is wpa-psk2....if both your router and card support it, Ubuntu (more than likely) has the right drivers and it will work. You will have to activate the restricted drivers to do so.....System>Admin>Restricted drivers...Ubuntu will even install the drivers automatically if you tell it to activate the wireless restricted drivers.....Good Luck, let us know!

---

### Post by iceman0304 on 2008-01-11
Using a Compaq laptop with Broadcom 4306,  I just got help getting it up and working so that is a big plus,  But I use PSK2 personal for my security.

I have tried switching between WPA personal & WPA2 personal but I haven't had any luck, but of course I'm doing something thats not working.

---

### Post by Digger78 on 2008-01-11
[B]I'm glad you got the card working, Please dont do the command in this post unless somebody confirms and advices how to continue. 
[/B]
For anybody that can help iceman get his security up and running, the following post is how he got his card working  [http://ubuntuforums.org/showpost.php?p=4112637&postcount=46]("http://ubuntuforums.org/showpost.php?p=4112637&postcount=46")

am i correct in thinking that he will need to do

```
echo 'ENABLED=1' | sudo tee -a /etc/default/wpasupplicant
```

before he can use WPA?

---

### Post by iceman0304 on 2008-01-15
Ok now that I got my wireless backup,  

Router has been switched to WPA AES

I'm using WPA for my security but I can't get connected.  

Can anyone direct me to another post or show me?

Thanks

---

### Post by stchman on 2008-01-15
> **iceman0304 said:**
> My router only supports WEP,PSK pers., PSK ent., PSK2 pers., PSK2 ent. no WPA..

Need to find out if ubuntu can support the PSK's

Does PSK relate to WPA?

This is a Linksys Router WRT350N

That router supports WPA and WPA2.  I suggest using WPA2 with at least a 30 character passphrase.  WEP is pretty worthless.  Hidden SSID is also worthless.

What chipset does your wireless card have?

---

### Post by iceman0304 on 2008-01-15
currently using a broadcom 4306,

I agree I'd like to use the WPA2, but will start with the WPA...

Reason being I was using the WPA2 with no problems with WinXP.  When I upgraded the Routers firmware last week it failed, I did eventually get the firmware installed after a day or 2,  but had no luck with the wireless.  I finally got sometime to work on it today and got it back up.  With only WPA I couldn't manage to get the WPA2 working yet.  If I can't get it to work with WinXP I'm not going to bother with getting it to work with Linux.

I'm trying to get Linux to work with the wireless laptop so I have a reason to use and to learn it.

---

### Post by mandrill on 2008-01-15
> **iceman0304 said:**
> currently using a broadcom 4306,

I agree I'd like to use the WPA2, but will start with the WPA...

Reason being I was using the WPA2 with no problems with WinXP.  When I upgraded the Routers firmware last week it failed, I did eventually get the firmware installed after a day or 2,  but had no luck with the wireless.  I finally got sometime to work on it today and got it back up.  With only WPA I couldn't manage to get the WPA2 working yet.  If I can't get it to work with WinXP I'm not going to bother with getting it to work with Linux.

I'm trying to get Linux to work with the wireless laptop so I have a reason to use and to learn it.

XP is zero config...ask it to show the networks, pick yours, click connect, give the passphrase  for wpa2 and you're done. Linux defaults with samba to mshome network - unless you're using static ip, or the router doesn't see the machines, you're good to go. You may need to update your wireless card's driver, but its doubtful..... unfortunately, without actually being able to see your setup, its kinda hard to be absolute.....

---

### Post by iceman0304 on 2008-01-15
yeah I figure I'm just missing something simple just remembering, I'm just limited to the times I can work on it, don't want to disrupt the wife........

---

### Post by iceman0304 on 2008-01-16
stchman,

should I just follow the instructions on your site for the WPA etc.  ndiswrapper should already be done, I think its the WPA part is all that I'm missing.

Digger78 had done a really good job at getting me up and running, here is that posting:

[http://ubuntuforums.org/showpost.php...7&postcount=46](http://ubuntuforums.org/showpost.php...7&postcount=46)


Thanks

---

### Post by stchman on 2008-01-16
> **iceman0304 said:**
> stchman,

should I just follow the instructions on your site for the WPA etc.  ndiswrapper should already be done, I think its the WPA part is all that I'm missing.

Digger78 had done a really good job at getting me up and running, here is that posting:

[http://ubuntuforums.org/showpost.php...7&postcount=46](http://ubuntuforums.org/showpost.php...7&postcount=46)


Thanks

What I believe you are referring to is the installation of Network Manager.  NM is installed by default on Feisty and later.  What Ubuntu are you running.

Whatever version of Ubuntu you are running then follow the instructions.

For Feisty follow the instructions I have on my page for getting the ndiswrapper up and running.  For Gutsy follow these instructions:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver)

I wish that Broadcom would make Linux drivers for their cards.

Remember, Network Manager is installed by default on Feisty and later and NM is capable of connecting to WEP/WPA/WPA2 points.

---

### Post by iceman0304 on 2008-01-16
matt@matt-laptop:~$ lspci | grep Broadcom
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
matt@matt-laptop:~$ gksu gedit /etc/apt/sources.list


This is what opens: gedit

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


matt@matt-laptop:~$ deb  [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) gutsy-cafuego bcm43xx
bash: deb: command not found
matt@matt-laptop:~$

---

### Post by iceman0304 on 2008-01-16
Gutsy 7.10 32bit   Ubuntu

---

### Post by iceman0304 on 2008-01-16
Reposted to a New thread more better suited for  the question.

[http://ubuntuforums.org/showthread.php?p=4150361#post4150361](http://ubuntuforums.org/showthread.php?p=4150361#post4150361)

---

