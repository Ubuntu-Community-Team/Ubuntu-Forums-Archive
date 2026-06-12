---
title: "gcc no ubuntu"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by tponte on 2006-08-23
Hi,


I just installed ubuntu 6.06 64 bits, and I am trying to install gcc, but with no sucess.

I tried apt-get install gcc, but it says "Couldn't find package gcc". Does anyone have a idea of how to install gcc?


Thanks

---

### Post by Qrk on 2006-08-23
The package name is "g++"

---

### Post by bensexson on 2006-08-23
sudo aptitude install build-essential

---

### Post by aysiu on 2006-08-23
What's the output of these two commands? ```
sudo aptitude update
cat /etc/apt/sources.list
```

---

### Post by tponte on 2006-08-23
I tried g++ and aptitude install build-essential
Neither worked :(

The second one printed
"Coundn't find any package whose name or description matched 'build-essential'"

Any other suggestion?

Thanks

---

### Post by aysiu on 2006-08-23
Instead of trying to summarize the output, can you copy and paste exactly what was in the terminal? I don't see how *cat /etc/apt/sources.list* could possibly have anything to do with *build-essential*.

For example, this is what I get as output: ```
username@ubuntu:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Get:3 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Ign http://packages.freecontrib.org dapper Release.gpg
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.canonical.com dapper-commercial Release
Get:5 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://archive.ubuntu.com dapper Release
Ign http://packages.freecontrib.org dapper Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.canonical.com dapper-commercial/main Packages
Ign http://packages.freecontrib.org dapper/free Packages
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Ign http://packages.freecontrib.org dapper/non-free Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Ign http://packages.freecontrib.org dapper/free Sources
Ign http://packages.freecontrib.org dapper/non-free Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Get:6 http://archive.ubuntu.com dapper-updates/restricted Packages [14B]
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://packages.freecontrib.org dapper/free Packages
Get:7 http://archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get:8 http://archive.ubuntu.com dapper-backports/main Packages [14B]
Get:9 http://archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get:10 http://archive.ubuntu.com dapper-backports/universe Packages [14B]
Get:11 http://archive.ubuntu.com dapper-backports/multiverse Packages [14B]
Hit http://packages.freecontrib.org dapper/non-free Packages
Hit http://packages.freecontrib.org dapper/free Sources
Hit http://packages.freecontrib.org dapper/non-free Sources
Fetched 89B in 1s (52B/s)
Reading package lists... Done
username@ubuntu:~$ cat /etc/apt/sources.list
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

deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free
username@ubuntu:~$
```

---

### Post by tponte on 2006-08-23
Hi,

I figured out what the problem was. When I was updating the aptitude, nothing was happening, because my /etc/apt/sources.list was pointing to br.archive.ubuntu.com, and this server doesn't exist. Once I changed it to archive.ubuntu.com everything worked out and I cound install build-essential

Thanks a lot for the help, I'm sure I wouldn't be able to figure this out on my own. :)

Thiago

---

### Post by sotdem on 2006-08-24
You could use the Synaptic Package Manager, just write gcc in the search area and then click the Apply. :wink:

---

