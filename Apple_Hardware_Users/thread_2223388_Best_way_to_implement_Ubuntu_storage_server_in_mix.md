---
title: "Best way to implement Ubuntu storage server in mixed OSX environment?"
date: 2014-05-10
forum: Apple Hardware Users
---

### Post by putz30002 on 2014-05-10
I have built multiple Ubuntu SAMBA storage servers for Win PC's but have a heavy concentration of Mac's in my house now with mixed variants of OS in addition to a Win PC & a couple Linux machines. In the past I had been looking into implementing Netatalk in addition to SAMBA to give me the windows/OSX functionality. I had recently heard that OSX computers are actually doing just fine performance wise communicating with SAMBA machines. But I don't really trust the sources interpretation of "fine performance" nor have I had good experiences in the past. Time Machine is not a critical component of what I am trying to do either. If I implemented Netatalk I might consider setting up one iMac to use Time Machine on the storage server but primarily I am just thinking general storage. The server would be running software RAID 1. 

My question is based on the above basics and the below OS variants, what are the community recommendations for best performance and usability - SAMBA only or SAMBA & Netatalk?

iMac w/ 10.6
iMac w/ 10.8
iMac w/ 10.9
Laptop w/ Win 7

--Of less importance--

Laptop w/ Ubuntu 14.04 
Laptop w/ elementary Luna (Ubuntu 12.04 LTS base)

---

### Post by gsahli on 2014-05-10
It's been about 4 years since I even bothered to set up netatalk. I go with two setups on the server - sftp and samba. Both way easier to set up and serve me well.

---

### Post by putz30002 on 2014-05-10
> **gsahli said:**
> [COLOR=#000000]It's been about 4 years since I even bothered to set up netatalk. I go with two setups on the server - sftp and samba. Both way easier to set up and serve me well.[/COLOR]

Are the Mac's talking straight to SAMBA server or are you only using sftp for the Mac communications? I assume if talking straight (LAN) to SAMBA server there are no speed/indexing issues from your Mac(s)? OSX versions?

---

### Post by gsahli on 2014-05-11
Server - lubuntu 14.04
Macs - 10.9.2 and 10.4.11
Other PCs mix of ubuntu 12.04 and 14.04, no modern Windows, but two dual boot to WinXP
My Macs are both using Samba, not always mounted, but saved as favorite in the Go > Connect to server menu
(sftp is just an "alternate" protocol, set up for grins) 
(my Macs are both in the basement, run almost entirely using VNC)

---

