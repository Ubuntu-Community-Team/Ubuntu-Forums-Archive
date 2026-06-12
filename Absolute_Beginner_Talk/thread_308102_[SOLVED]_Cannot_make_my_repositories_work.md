---
title: "[SOLVED] Cannot make my repositories work"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by pulldogg on 2006-11-27
Whenever i try to add the universal n multiverse repositories it asks me to hit reload n when i do i get the following error

[http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (1.0.0.0), connection timed out
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out



my net is working fine as in all the sites r opening fine
n heres my source.list 

# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

# #deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiverse
## PLF repositories, contains litigious packages, see [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
## Freecontrib, funny packages by the Ubuntu PLF Team
deb [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) breezy free non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) breezy free non-free

pls do help,ive not been able to use ubuntu at all since installing it because of this.
much appreciated n im totally new to this so u will have to explain it to me like a 2yd old kid.

---

### Post by taurus on 2006-11-27
Does your network work at all?  Open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here.

```
ping -w 3 www.yahoo.com
```

---

### Post by pulldogg on 2006-11-27
mhatre@mhatre:~$ ping -w 3 [www.yahoo.com](www.yahoo.com)
PING [www.yahoo-ht2.akadns.net](www.yahoo-ht2.akadns.net) (209.73.186.238) 56(84) bytes of data.
64 bytes from [www.yahoo.com](www.yahoo.com) (209.73.186.238): icmp_seq=1 ttl=51 time=225 ms
64 bytes from [www.yahoo.com](www.yahoo.com) (209.73.186.238): icmp_seq=2 ttl=51 time=224 ms
64 bytes from [www.yahoo.com](www.yahoo.com) (209.73.186.238): icmp_seq=3 ttl=51 time=224 ms

--- [www.yahoo-ht2.akadns.net](www.yahoo-ht2.akadns.net) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2011ms
rtt min/avg/max/mdev = 224.457/224.877/225.382/0.544 ms
mhatre@mhatre:~$

---

### Post by taurus on 2006-11-27
I guess just try to update it again later!!!

---

### Post by pulldogg on 2006-11-27
ive been trying for the last 2-3 days ,same error,infact im posting these mssgs from the same net connection.

---

### Post by taurus on 2006-11-27
Well, you can comment those repos out by placing a # in front of those lines in /etc/apt/sources.list to see if that fixes the problem for now!!!

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by pulldogg on 2006-11-27
comment out wat all?

---

### Post by pulldogg on 2006-11-27
this is the output of ur command

mhatre@mhatre:~$ gksudo gedit /etc/apt/sources.list

(gksudo:7574): Gdk-WARNING **: locale not supported by Xlib

(gksudo:7574): Gdk-WARNING **: cannot set locale modifiers
(gedit:7575): Gdk-WARNING **: locale not supported by Xlib

(gedit:7575): Gdk-WARNING **: cannot set locale modifiers

(gedit:7575): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.
mhatre@mhatre:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg
  Could not connect to antesis.freecontrib.org:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg
  Could not connect to antesis.freecontrib.org:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release

Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release

Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
  Could not connect to antesis.freecontrib.org:80 (1.0.0.0), connection timed out
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
  Could not connect to antesis.freecontrib.org:80 (1.0.0.0), connection timed out
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
  Could not connect to antesis.freecontrib.org:80 (1.0.0.0), connection timed out
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
  Could not connect to antesis.freecontrib.org:80 (1.0.0.0), connection timed out
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Sources
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
mhatre@mhatre:~$ sudo aptitude upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by CatKiller on 2006-11-27
This > (1.0.0.0) is your problem. I've seen it come up before, but I don't know what the solution is. It's something to do with some routers not being able to find a DNS server properly, so it resolves all addresses to 1.0.0.0. Or something.

---

### Post by shin on 2006-11-27
Had same problem with my old router. And it is probably the same. Resolving some domains just didnt work properly. Get your ISP's dns servers (or any other dnses that you can ping with low latency) and put them in resolv.conf in such a way:
nameserver <ip>

e.g.
nameserver 194.204.159.1
nameserver 194.204.152.34

Right now there is probably your router ip - like nameserver 192.168.1.1
Remove it. Also to make sure that your settings wont be overwritten on reconnect - set your settings to static or comment usage of mkresolv in dhcp script. There is some info about methods how to do it on this forum, search for more details.

---

### Post by Aldoliel on 2006-11-27
I would suggest you manually set some DNS servers in Network Settings (or resolv.conf) but it seems that your problem is intermittent. It might help if you want to try it.

Just for clarification, I believe it's that some routers don't correctly pass dynamic clients (i.e. those using DHCP) the DNS addresses. I could be wrong though.

---

### Post by pulldogg on 2006-11-28
thx a ton every1 for ur time,i added some dns addresses n now it works fine.
big thx to every1.

---

