---
title: "apt-get error?"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-10-18
Hi when I run apt-get update I get this error at the end.

```
aktiwers@HAL:~$ sudo apt-get update
Password:
Get:1 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg [189B]
Get:2 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release [9452B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Get:3 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages [1974B]
Get:4 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Get:5 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages [2585B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Get:6 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Get:7 [http://media.blutkind.org](http://media.blutkind.org) dapper Release.gpg [189B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Get:9 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release [5402B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Get:11 [http://media.blutkind.org](http://media.blutkind.org) dapper Release [5402B]
Get:12 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]
Get:13 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Ign [http://media.blutkind.org](http://media.blutkind.org) dapper/main Packages
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [74.8kB]
Ign [http://media.blutkind.org](http://media.blutkind.org) dapper/aiglx Packages
Get:15 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:16 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release [34.8kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [6446B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [13.6kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [960B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [30.2kB]
Get:21 [http://media.blutkind.org](http://media.blutkind.org) dapper/main Packages [13.4kB]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [4026B]
Get:23 [http://media.blutkind.org](http://media.blutkind.org) dapper/aiglx Packages [3582B]
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/aiglx Packages
Get:24 [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages [13.4kB]
Get:25 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release [29.6kB]
Get:26 [http://www.beerorkid.com](http://www.beerorkid.com) dapper/aiglx Packages [3582B]
Get:27 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports Release [23.3kB]
Get:28 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Packages [619kB]
Get:29 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Packages [4571B]
Get:30 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Packages [2458kB]
Get:31 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/multiverse Packages [95.2kB]
Get:32 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources [255kB]
Get:33 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources [1478B]
Get:34 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Sources [975kB]
Get:35 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources [46.5kB]
Get:36 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:37 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/main Sources [3632B]
Get:38 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Get:39 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/universe Sources [7768B]
Get:40 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/multiverse Sources [864B]
Fetched 4777kB in 18s (263kB/s)
Reading package lists... Done
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems
aktiwers@HAL:~$
```Anyone knows how to fix this?

---

### Post by opticsnake on 2006-10-18
Quick google search returned this article on the exact problem and how to fix:
[http://thinkhole.org/wp/2006/01/03/public-key-not-available/](http://thinkhole.org/wp/2006/01/03/public-key-not-available/)

Edit:
another guy says that this is the code to run to fix it:
```
sudo wget http://ftp-master.debian.org/ziyi_key_2006.asc -O - | sudo apt-key add -
```

---

### Post by geezerone on 2006-10-18
Install Automatix2 and remove Automatix (1) afterwards

---

### Post by PriceChild on 2006-10-18
There's nothing actually broken... you just might want to get the packager's public key and add it to synaptic to be availiable to verify the packages haven't been tampered with before they get to you :)

---

### Post by aktiwers on 2006-10-18
> **PriceChild said:**
> There's nothing actually broken... you just might want to get the packager's public key and add it to synaptic to be availiable to verify the packages haven't been tampered with before they get to you :)

Thanks.. can you tell me how to do that please?

Also this didint work..
> 
aktiwers@HAL:~$ sudo wget [http://ftp-master.debian.org/ziyi_key_2006.asc](http://ftp-master.debian.org/ziyi_key_2006.asc) -O - | sudo apt-key add -
--20:31:30--  [http://ftp-master.debian.org/ziyi_key_2006.asc](http://ftp-master.debian.org/ziyi_key_2006.asc)
           => `-'
Resolving ftp-master.debian.org... 140.211.166.43
Connecting to ftp-master.debian.org|140.211.166.43|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,017 (2.0K) [text/plain]

100%[====================================>] 2,017         --.--K/s

20:31:30 (113.15 MB/s) - `-' saved [2017/2017]

OK
aktiwers@HAL:~$ 

---

### Post by geezerone on 2006-10-18
Do you have automatix 2?

---

### Post by aktiwers on 2006-10-18
yes

---

### Post by PriceChild on 2006-10-18
> **aktiwers said:**
> Thanks.. can you tell me how to do that please?

Also this didint work..That's because you've got the wrong key ;)

---

### Post by geezerone on 2006-10-18
I asked about Automatix 2 as I had to update my key for that as was getting same error msg.

---

### Post by aktiwers on 2006-10-18
can anyone tell me how to get the right key?
Thanks a lot for the help :)

---

### Post by bionnaki on 2006-10-18
I having the same problem. 

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) has a solution at the end of the page, but it did not work for me.

any ideas? thanks

---

### Post by bionnaki on 2006-10-18
ok. I figured it out.

do this:

wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg)

and then open up synaptic
and go to settings>repos>authentication
and "import file key"
browse the key and click ok.

and then sudo aptitude update

---

### Post by aktiwers on 2006-10-19
Cool thanks! Fixed it for me as well :)

---

