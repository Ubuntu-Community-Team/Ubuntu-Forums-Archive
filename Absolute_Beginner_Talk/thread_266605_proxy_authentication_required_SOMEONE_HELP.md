---
title: "proxy authentication required SOMEONE HELP"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by cinderella on 2006-09-27
hi i'm a newbie!!! so when replying to my post please give me a [COLOR="Lime"]step by step procedure[/COLOR] on how to solve the problem as if I do not know anything.

Well here is my problem!!! I am a university student and to log on we require a username and password so I guess I'm behind a proxy.

I'm currently trying to install nfs-common. I downloaded it and manually tried to install it but it gives me the following error:

[COLOR="Red"]Error: Conflicts with installed package 'nfs-common' 
[/COLOR]
I installed the dependencies for nfs-common with ease so why is it giving this problem????

I then tried to uncomment all lines with multiverse and universe in my sources.list which looks like this:

```
deb-src http://za.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://za.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
 deb-src http://za.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb-src http://za.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://za.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
 deb-src http://za.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
 deb http://security.ubuntu.com/ubuntu dapper-security universe
 deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://archive.ubuntu.com/ubuntu/ dapper main universe restricted multiverse
```


[COLOR="Lime"]but when I saved the changes it gave me the following errors:[/COLOR]

```

bulletproof@Bulletproof:~$ sudo gedit /etc/apt/sources.list](*,) 
Password:
bulletproof@Bulletproof:~$ sudo apt-get update
Ign http://archive.ubuntu.com dapper Release.gpg
Ign http://za.archive.ubuntu.com dapper Release.gpg
Ign http://archive.ubuntu.com dapper Release
Ign http://za.archive.ubuntu.com dapper-updates Release.gpg
Ign http://archive.ubuntu.com dapper/main Packages
Ign http://za.archive.ubuntu.com dapper-backports Release.gpg
Ign http://za.archive.ubuntu.com dapper Release
Ign http://za.archive.ubuntu.com dapper-updates Release
Ign http://za.archive.ubuntu.com dapper-backports Release
Ign http://za.archive.ubuntu.com dapper/main Sources
Ign http://za.archive.ubuntu.com dapper/restricted Sources
Ign http://za.archive.ubuntu.com dapper/universe Sources
Ign http://za.archive.ubuntu.com dapper-updates/main Packages
Ign http://za.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://za.archive.ubuntu.com dapper-updates/main Sources
Ign http://za.archive.ubuntu.com dapper-updates/restricted Sources
Ign http://za.archive.ubuntu.com dapper-backports/main Packages
Ign http://za.archive.ubuntu.com dapper-backports/restricted Packages
Ign http://za.archive.ubuntu.com dapper-backports/universe Packages
Ign http://za.archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://za.archive.ubuntu.com dapper-backports/main Sources
Ign http://za.archive.ubuntu.com dapper-backports/restricted Sources
Ign http://za.archive.ubuntu.com dapper-backports/universe Sources
Ign http://za.archive.ubuntu.com dapper-backports/multiverse Sources
Err http://za.archive.ubuntu.com dapper/main Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper/restricted Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper/universe Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-updates/main Packages
  407 Proxy Authentication Required
Ign http://archive.ubuntu.com dapper/universe Packages
Err http://za.archive.ubuntu.com dapper-updates/restricted Packages
  407 Proxy Authentication Required
Ign http://archive.ubuntu.com dapper/restricted Packages
Ign http://archive.ubuntu.com dapper/multiverse Packages
Err http://archive.ubuntu.com dapper/main Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com dapper/universe Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com dapper/restricted Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com dapper/multiverse Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-updates/main Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-updates/restricted Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-backports/main Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-backports/restricted Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-backports/universe Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-backports/multiverse Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-backports/main Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-backports/restricted Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-backports/universe Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-backports/multiverse Sources
  407 Proxy Authentication Required
Ign http://security.ubuntu.com dapper-security Release.gpg
Ign http://security.ubuntu.com dapper-security Release
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://security.ubuntu.com dapper-security/universe Sources
Err http://security.ubuntu.com dapper-security/universe Packages
  407 Proxy Authentication Required
Err http://security.ubuntu.com dapper-security/universe Sources
  407 Proxy Authentication Required
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz  407 Proxy Authentication Required
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
bulletproof@Bulletproof:~$
```





How do I solve this proxy authentication problem. Other threads explained to type the following:

[COLOR="Red"]Acquire::http:Proxy "http://MYDOMAIN\MYNAME:MYPASS@MY.PROXY.COM:MYPORT"
[/COLOR]
But where do I type this and what else do I do!!!!!

Please help me solve this problem in a step by step fashion. Im desperate. My entire degree depends on this project and I need this to work by tomorrow.  By the way when I press the RELOAD button in the synaptic package manager it gives me the following errors:


```
http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz: 407 Proxy Authentication Required
http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://za.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz: 407 Proxy Authentication Required
http://za.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz: 407 Proxy Authentication Required
http://za.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz: 407 Proxy Authentication Required
http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz: 407 Proxy Authentication Required
http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz: 407 Proxy Authentication Required
http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz: 407 Proxy Authentication Required
http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz: 407 Proxy Authentication Required
http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz: 407 Proxy Authentication Required
http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz: 407 Proxy Authentication Required


```
:confused: :-k ](*,)

---

### Post by petit.padavoine on 2006-09-27
I don't know about all the errors. About nfs-common, I think it's saying that it's useless to download and install it manually as it's already installed.

---

### Post by lamego on 2006-09-27
1, You should not download and install nfs manually, just use apt-get install.

2. You can set the proxy for most command line commands with:
```
export http_proxy=http://user:pass@proxy_host:port
export ftp_proxy=http://user:pass@proxy_host:port

```Then just:
```
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by petit.padavoine on 2006-09-27
The export commands should go into your ~/.bashrc to be permanent.

---

### Post by cinderella on 2006-09-27
> **petit.padavoine said:**
> The export commands should go into your ~/.bashrc to be permanent.


thanks i will try this but

how do I go into /.bashrc ???

---

### Post by annda on 2006-09-27
try ```
gedit ~/.bash.rc
``` and type/paste the commands + save the file + log in again.

---

### Post by cinderella on 2006-09-27
> **lamego said:**
> 1, You should not download and install nfs manually, just use apt-get install.

2. You can set the proxy for most command line commands with:
```
export http_proxy=http://user:pass@proxy_host:port
export ftp_proxy=http://user:pass@proxy_host:port

```Then just:
```
sudo apt-get update
sudo apt-get upgrade

```

[COLOR="Red"]This is what I did and these are the errors I get:[/COLOR]


```
bulletproof@Bulletproof:~$ export http_proxy=http://bulletproof:button@proxy.ukz n.ac.za:8080
bulletproof@Bulletproof:~$ export ftp_proxy=http://bulletproof:button@proxy.ukzn .ac.za:8080
bulletproof@Bulletproof:~$ sudo apt-get update Password:
Ign http://security.ubuntu.com dapper-security Release.gpg
Ign http://archive.ubuntu.com dapper Release.gpg
Ign http://za.archive.ubuntu.com dapper Release.gpg
Ign http://security.ubuntu.com dapper-security Release
Ign http://archive.ubuntu.com dapper Release
Ign http://za.archive.ubuntu.com dapper-updates Release.gpg
Ign http://archive.ubuntu.com dapper/main Packages
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://za.archive.ubuntu.com dapper-backports Release.gpg
Ign http://archive.ubuntu.com dapper/universe Packages
Ign http://security.ubuntu.com dapper-security/universe Sources
Ign http://za.archive.ubuntu.com dapper Release
Ign http://za.archive.ubuntu.com dapper-updates Release
Ign http://archive.ubuntu.com dapper/restricted Packages
Err http://security.ubuntu.com dapper-security/universe Packages
  407 Proxy Authentication Required
Ign http://za.archive.ubuntu.com dapper-backports Release
Err http://security.ubuntu.com dapper-security/universe Sources
  407 Proxy Authentication Required
Ign http://archive.ubuntu.com dapper/multiverse Packages
Err http://archive.ubuntu.com dapper/main Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com dapper/universe Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com dapper/restricted Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com dapper/multiverse Packages
  407 Proxy Authentication Required
Ign http://za.archive.ubuntu.com dapper/main Sources
Ign http://za.archive.ubuntu.com dapper/restricted Sources
Ign http://za.archive.ubuntu.com dapper/universe Sources
Ign http://za.archive.ubuntu.com dapper-updates/main Packages
Ign http://za.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://za.archive.ubuntu.com dapper-updates/main Sources
Ign http://za.archive.ubuntu.com dapper-updates/restricted Sources
Ign http://za.archive.ubuntu.com dapper-backports/main Packages
Ign http://za.archive.ubuntu.com dapper-backports/restricted Packages
Ign http://za.archive.ubuntu.com dapper-backports/universe Packages
Ign http://za.archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://za.archive.ubuntu.com dapper-backports/main Sources
Ign http://za.archive.ubuntu.com dapper-backports/restricted Sources
Ign http://za.archive.ubuntu.com dapper-backports/universe Sources
Ign http://za.archive.ubuntu.com dapper-backports/multiverse Sources
Err http://za.archive.ubuntu.com dapper/main Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper/restricted Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper/universe Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-updates/main Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-updates/restricted Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-updates/main Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-updates/restricted Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-backports/main Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-backports/restricted Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-backports/universe Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-backports/multiverse Packages
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-backports/main Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-backports/restricted Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-backports/universe Sources
  407 Proxy Authentication Required
Err http://za.archive.ubuntu.com dapper-backports/multiverse Sources
  407 Proxy Authentication Required
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/P ackages.gz  407 Proxy Authentication Required
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe /binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i3 86/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe /source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary- i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary- i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sou rces.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper/restricted/sour ce/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper/universe/source /Sources.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/bi nary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/restric ted/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/so urce/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/restric ted/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/ binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/restr icted/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/unive rse/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/multi verse/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/ source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/restr icted/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/unive rse/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/multi verse/source/Sources.gz  407 Proxy Authentication Required
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used  instead.
bulletproof@Bulletproof:~$


```

---

### Post by cinderella on 2006-09-27
> **annda said:**
> try ```
gedit ~/.bash.rc
``` and type/paste the commands + save the file + log in again.

when u say log in again do u mean that I should reboot and log in again??? what should I do?? 

sorry i'm a bit too new to linux....i'm just learning the absolute basics so please bear with me

---

### Post by cinderella on 2006-09-27
Sorry !!!! 

I did not write anything in the bashrc file but I did type the "export" commands in the command window and I was able to obtain an upgrade:) 

BUT

I when I click on the RELOAD button I still get the errors that I showed in my first post in this thread....(407 Proxy Authentication Required)


Can anyone help with this

---

### Post by andriansah on 2006-09-28
Try to change your repo address.
I have the same problem, but when i switch the repo address it works

---

### Post by Leeghoofd on 2006-09-28
> **lamego said:**
> 1, You should not download and install nfs manually, just use apt-get install.

2. You can set the proxy for most command line commands with:
```
export http_proxy=http://user:pass@proxy_host:port
export ftp_proxy=http://user:pass@proxy_host:port

```Then just:
```
sudo apt-get update
sudo apt-get upgrade

```

Alternativly try:

sudo gedit /etc/apt/apt.conf
( if you don't know what you're doing backup the apt.conf first )

---

### Post by ian.l on 2006-09-28
Have you tried setting the proxy under System-->Preferences-->Network Proxy?
Do that and then try apt-get or Synaptic.

---

### Post by cinderella on 2006-09-28
> **ian.l said:**
> Have you tried setting the proxy under System-->Preferences-->Network Proxy?
Do that and then try apt-get or Synaptic.

thanks i finally installed nfs-kernel-server with form the synaptic package manger and now it does not give me the proxy authentication error


BUT I want to install these packages on my pc at home which does not have any
internet access so I can I install packages on my home pc and how can I activate mulitverse and universe repositories without accessing the net!!!!!

---

### Post by tech9 on 2007-10-23
> **cinderella said:**
> thanks i finally installed nfs-kernel-server with form the synaptic package manger and now it does not give me the proxy authentication error


BUT I want to install these packages on my pc at home which does not have any
internet access so I can I install packages on my home pc and how can I activate mulitverse and universe repositories without accessing the net!!!!!

you can't... you need a connection to the internet

---

