---
title: "Jre1.5"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by cclliu on 2006-07-09
I just installed Ubuntu after years struggling with Windows and its blue screen.

I am impressed with the smooth installation.  I started testing the OS by going to all my favourite websites.  One being ETRADE, I need to have at least JRE 1.5 for the apps to launch.

How can I install Sun JRE or whatever JRE?  I tried the 2 JRE listed for Linux and it does not work.

Will I be able to install the CISCO VPN Client?  I have to sourge CISCO website for it today.

Lawrence

---

### Post by linuxfan128 on 2006-07-09
Use Automatix to install it. It works great. You can find it here and other info.
[http://ubuntuforums.org/showthread.php?t=80295]("http://ubuntuforums.org/showthread.php?t=80295")

---

### Post by John.Michael.Kane on 2006-07-09
jre runtime is in the repos. 

```
**sudo gedit /etc/apt/sources.list**
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main
[B]
Then sudo aptitude update[/B]
```

the search for sun in synaptic

---

### Post by linuxted on 2006-07-09
> **cclliu said:**
> I just installed Ubuntu after years struggling with Windows and its blue screen.

I am impressed with the smooth installation.  I started testing the OS by going to all my favourite websites.  One being ETRADE, I need to have at least JRE 1.5 for the apps to launch.

How can I install Sun JRE or whatever JRE?  I tried the 2 JRE listed for Linux and it does not work.

Will I be able to install the CISCO VPN Client?  I have to sourge CISCO website for it today.

Lawrence

Automatix was helpful for me, and I suspect it will make your install of the jre simpler.  

What I'd like to know is how to get an older version of the jre (1.4) since latest one is causing me problems.

---

### Post by Kilz on 2006-07-09
> **linuxted said:**
> Automatix was helpful for me, and I suspect it will make your install of the jre simpler.  

What I'd like to know is how to get an older version of the jre (1.4) since latest one is causing me problems.
Are you getting an error from apt/synaptic? Something about java5-doc?

---

### Post by coderboi on 2006-07-09
> **cclliu said:**
> I just installed Ubuntu after years struggling with Windows and its blue screen.

I am impressed with the smooth installation.  I started testing the OS by going to all my favourite websites.  One being ETRADE, I need to have at least JRE 1.5 for the apps to launch.

How can I install Sun JRE or whatever JRE?  I tried the 2 JRE listed for Linux and it does not work.

Will I be able to install the CISCO VPN Client?  I have to sourge CISCO website for it today.

Lawrence



I installed it just by following these instructions

[http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox]("http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox")

---

### Post by Jucato on 2006-07-10
You could also install Sun's Java with these instructions:
[http://help.ubuntu.com/community/Java](http://help.ubuntu.com/community/Java)

---

