---
title: "XP downloads fast ... Ubuntu Slow"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by Dinerty on 2006-07-19
**Ubuntu:**

 >Fast HTTP downloads e.g web pages load fast, drivers download fast Programs download fast e.g java

 >Fast Ubuntu updates

 >Fast downloads in terminal

 >VERY SLOW FTP and IM e.g Kopete transfers, couple of kb/s a second

**Windows**

 >Fast FTP and IM transfers

To test this theory, If I download the exact data from same FTP in Windows its fast as hell, if I download the exact same data from the same FTP in Ubuntu, it is slow as hell

It seems alot of people are having this problem, hopefully there is a fix for it soon :(

---

### Post by Kurt` on 2006-07-19
Have you tried using a different FTP client? Mozilla Firefox can act as an FTP client as well.

e.g. [ftp://ftp.mozilla.org/pub/mozilla.org/](ftp://ftp.mozilla.org/pub/mozilla.org/)

---

### Post by kdragon on 2006-07-19
Ubuntu hasn't any strong transfering data in net than WIn
I almost download by Firefox download manager in Ubuntu,but XP which has many choice :Internet download manager,Flashget.Download accelebrate plus,....

download by FTp appz so slow,even if u use in win or Linux,the best sollution is copy link in FTP and then paste.Download manager do better than any FTP transfering appz

---

### Post by Brunellus on 2006-07-19
turn off IPv6 in ubuntu?

---

### Post by Dinerty on 2006-07-19
> **Kurt` said:**
> Have you tried using a different FTP client? Mozilla Firefox can act as an FTP client as well.

e.g. [ftp://ftp.mozilla.org/pub/mozilla.org/](ftp://ftp.mozilla.org/pub/mozilla.org/)

Thanks mate, my download speed is maxed via this fireftp, but why dont they go fast in gFTP?

> **Brunellus said:**
> turn off IPv6 in ubuntu?

Thanks for this, i looked round my system but not sure the location of this?, I'm using KDE

Thanks again

---

### Post by drtvasudevan on 2006-07-19
> **Dinerty said:**
> 
Thanks for this, i looked round my system but not sure the location of this?, I'm using KDE

Thanks again

ipv6 is disabled in the firefox browser via about:config in the url box

---

### Post by Kurt` on 2006-07-19
> **Dinerty said:**
> 
Thanks for this, i looked round my system but not sure the location of this?, I'm using KDE
To completely disable IPv6 (system-wide, including the IPv6 over v4 tunnel),:

# sudo gedit /etc/modprobe.d/aliases

(Replace 'gedit' with your preferred editor.)

Replace "alias net-pf-10 ipv6" with "alias net-pf-10 off" and reboot. After that, 'ifconfig' should no longer show any scary looking hex-notated IP addresses. ;)

---

### Post by Dinerty on 2006-07-22
> **Brunellus said:**
> turn off IPv6 in ubuntu?

Thanks for the tip !

> **Kurt` said:**
> To completely disable IPv6 (system-wide, including the IPv6 over v4 tunnel),:

# sudo gedit /etc/modprobe.d/aliases

(Replace 'gedit' with your preferred editor.)

Replace "alias net-pf-10 ipv6" with "alias net-pf-10 off" and reboot. After that, 'ifconfig' should no longer show any scary looking hex-notated IP addresses. ;)

WOOOOOOOOOOOO HOOOOOOOOOOOOOOOOOO Thank you sir, EVERYTHING  is fast as hell !!!,  thank you soooooooooooooooooooooooooooo much !!

---

### Post by orb9220 on 2006-07-22
Is there a reason that it is On ?

---

