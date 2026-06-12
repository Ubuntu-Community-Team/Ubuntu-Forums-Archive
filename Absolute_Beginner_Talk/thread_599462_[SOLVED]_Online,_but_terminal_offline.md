---
title: "[SOLVED] Online, but terminal offline"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Lightning502 on 2007-11-01
Hi, i'm quite the newbe, but i got a lot of stuff working over the last week. Now i'm installing on another pc and i need to fake the mac-address to get a internet connection.

I know how to do it in macchanger and it works, i'm on firefox internetting right now. But the terminal has not got internet, when i do for instance: 

sudo apt-get install vlc

it just searches on this pc and finds nothing. I'm absolutely positive i'm connected to the internet.

Also , there is no internet in the SPM. So i cannot really download and install stuff, just if i download the .deb files. I also don't get the automatic update message

Am i missing something? I can't find in the forums that someone else has had troubles with this and i really would like this to function well.

I'm on Ubuntu 7.10 btw

Tnx

---

### Post by taurus on 2007-11-01
What are the outputs of these two commands from a terminal?

```
/sbin/ifconfig
ping -c 3 www.google.com
```

---

### Post by Lightning502 on 2007-11-01
daniel@daniel-desktop:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:C3:9A:XX
  
          inet addr:217.76.XX.XX  Bcast:217.76.19.255  Mask:255.255.252.0
          inet6 addr: 2002:d94c:1023:4:20e:a6ff:fec3:9a1a/64 Scope:Global
          inet6 addr: fec0::4:20e:a6ff:fec3:9a1a/64 Scope:Site
          inet6 addr: fec0::9:20e:a6ff:fec3:9a1a/64 Scope:Site
          inet6 addr: 2002:d94c:115b:9:20e:a6ff:fec3:9a1a/64 Scope:Global
          inet6 addr: fe80::20e:a6ff:fec3:9a1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7463 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20071403 (19.1 MB)  TX bytes:793748 (775.1 KB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

daniel@daniel-desktop:~$ ping -c 3 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (66.249.93.99) 56(84) bytes of data.
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=1 ttl=246 time=7.29 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=2 ttl=246 time=8.50 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=3 ttl=246 time=7.89 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 7.295/7.897/8.506/0.504 ms

replaced some parts by XX ;)

---

### Post by taurus on 2007-11-01
Post the outputs of these two commands.

```
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by Lightning502 on 2007-11-01
daniel@daniel-desktop:~$ ping -c 1 [www.tweakers.net](www.tweakers.net)
PING [www.tweakers.net](www.tweakers.net) (213.239.154.35) 56(84) bytes of data.
64 bytes from [www.tweakers.net](www.tweakers.net) (213.239.154.35): icmp_seq=1 ttl=58 time=4.37 ms

--- [www.tweakers.net](www.tweakers.net) ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 4.376/4.376/4.376/0.000 ms
daniel@daniel-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
daniel@daniel-desktop:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vlc
daniel@daniel-desktop:~$ 


so to show you i'm online, i first pingged something

---

### Post by taurus on 2007-11-01
Looks to me like you only the CD as your repo in /etc/apt/sources.list.  Post

```
cat /etc/apt/sources.list
```

---

### Post by Lightning502 on 2007-11-01
thats a big one:

daniel@daniel-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
daniel@daniel-desktop:~$

---

### Post by taurus on 2007-11-01
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of the first line to comment out the CDROM.  Then, remove the # in front of all the lines that have **deb** & **deb-src**.  

Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install vlc
```

---

### Post by Lightning502 on 2007-11-01
THANKS you are my hero!

It works now, like on every other pc :) I immediately get the new software available button. 

Now it never asks the irritating question to insert the cd again right? It just downloads everything?

---

### Post by taurus on 2007-11-01
> **Lightning502 said:**
>  

Now it never asks the irritating question to insert the cd again right? It just downloads everything?

Yip.  That's the plan.

---

### Post by Lightning502 on 2007-11-01
Cool, but if removed the # in front of the CD and kept everything the same, then it would have internet & cdrom both as sources right? Not that i want that, this is a nice tweak :) 

I allways dislike it when i have to look for the cd :P

Anyway, thanks for the very quick help, i hope it will be useful for more people

---

