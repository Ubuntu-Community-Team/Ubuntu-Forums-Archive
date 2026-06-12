---
title: "Cannot connect to any repository"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by bentot on 2007-12-15
Hello!

I've been using Kubuntu Gutsy and have been having a hard time connecting to ANY repository. Have changed repositories and got the same problem. Please see current sources.list repository below:

-------------------------------------------------------------------------------
# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [ftp://ftp.ecc.u-tokyo.ac.jp/ubuntu/](ftp://ftp.ecc.u-tokyo.ac.jp/ubuntu/) gutsy main restricted multiverse
deb-src [ftp://ftp.ecc.u-tokyo.ac.jp/ubuntu/](ftp://ftp.ecc.u-tokyo.ac.jp/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties
deb [ftp://ftp.ecc.u-tokyo.ac.jp/ubuntu/](ftp://ftp.ecc.u-tokyo.ac.jp/ubuntu/) gutsy-updates main restricted multiverse
deb-src [ftp://ftp.ecc.u-tokyo.ac.jp/ubuntu/](ftp://ftp.ecc.u-tokyo.ac.jp/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties
deb [ftp://ftp.ecc.u-tokyo.ac.jp/ubuntu/](ftp://ftp.ecc.u-tokyo.ac.jp/ubuntu/) gutsy-security main restricted multiverse
deb-src [ftp://ftp.ecc.u-tokyo.ac.jp/ubuntu/](ftp://ftp.ecc.u-tokyo.ac.jp/ubuntu/) gutsy-security restricted main multiverse universe #Added by software-properties

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [ftp://ftp.ecc.u-tokyo.ac.jp/ubuntu/](ftp://ftp.ecc.u-tokyo.ac.jp/ubuntu/) gutsy universe
deb [ftp://ftp.ecc.u-tokyo.ac.jp/ubuntu/](ftp://ftp.ecc.u-tokyo.ac.jp/ubuntu/) gutsy-updates universe
deb [ftp://ftp.ecc.u-tokyo.ac.jp/ubuntu/](ftp://ftp.ecc.u-tokyo.ac.jp/ubuntu/) gutsy-security universe
------------------------------------------

As you can see below, I get an error when I issue the command sudo apt-get update
benny@Kubuntu-VM:~$ sudo apt-get update
Err [ftp://ftp.ecc.u-tokyo.ac.jp](ftp://ftp.ecc.u-tokyo.ac.jp) gutsy Release.gpg
  Could not connect to ftp.ecc.u-tokyo.ac.jp:21 (1.0.0.0), connection timed out
0% [Connecting to ftp.ecc.u-tokyo.ac.jp (1.0.0.0)]
benny@Kubuntu-VM:~$

I can confirm that I have a working internet connection. Immediate after the above, I ping the site and was able to get a response:

benny@Kubuntu-VM:~$ ping ftp.ecc.u-tokyo.ac.jp
PING sb.itc.u-tokyo.ac.jp (133.11.205.121) 56(84) bytes of data.
64 bytes from ftp.ecc.u (133.11.205.121): icmp_seq=1 ttl=46 time=95.9 ms
64 bytes from ftp.ecc.u (133.11.205.121): icmp_seq=2 ttl=46 time=97.1 ms
64 bytes from ftp.ecc.u (133.11.205.121): icmp_seq=3 ttl=46 time=94.8 ms
64 bytes from ftp.ecc.u (133.11.205.121): icmp_seq=4 ttl=46 time=80.4 ms
64 bytes from ftp.ecc.u (133.11.205.121): icmp_seq=5 ttl=46 time=84.6 ms

--- sb.itc.u-tokyo.ac.jp ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4007ms
rtt min/avg/max/mdev = 80.416/90.612/97.106/6.765 ms


I have been browsing the forums for a clue to what I could be doing wrong but cannot find any. I have tried different repositories as well.

Any help would be greatly appreciated!
Benny
A Kubuntu newbie

---

### Post by Zalbor on 2007-12-15
Maybe there's a problem with the tokyo mirrors? Try changing to another one, temporarily.

---

### Post by bentot on 2007-12-15
I have already tried many different repositories and got the same problem. I have not been able to connect to any repository since installation. Also, as shown above, I can ping the site.

---

### Post by Zalbor on 2007-12-15
What exactly is the error message? If you actually can't connect there but you can ping it and see web pages, it's very strange because as far as I know it's exactly the same as downloading a file with a web browser...

---

### Post by bentot on 2007-12-15
I have included the error message in the post above:

As you can see below, I get an error when I issue the command sudo apt-get update
benny@Kubuntu-VM:~$ sudo apt-get update
Err [ftp://ftp.ecc.u-tokyo.ac.jp](ftp://ftp.ecc.u-tokyo.ac.jp) gutsy Release.gpg
**Could not connect to ftp.ecc.u-tokyo.ac.jp:21 (1.0.0.0), connection timed out**0% [Connecting to ftp.ecc.u-tokyo.ac.jp (1.0.0.0)]
benny@Kubuntu-VM:~$

---

### Post by SunnyRabbiera on 2007-12-15
yeh maybe you need to change where you download from...
you can easily use a european server but if you need japanese then try anoter server in japan.

---

### Post by seventhc on 2007-12-15
are you using a proxy??? if you are, maybe try without.

---

### Post by bentot on 2007-12-15
... and no matter what repository I select, I get the same erro message. I have tried many different repositories.

Could it be that there is something wrong with my network settings? But I can browse the internet and can ping those sites.

I thread said that a firewall might be blocking my access, to check for the Firestarter program. I have already checked for this and it seems that it is not running on my system.

---

### Post by bentot on 2007-12-15
No I am not using any proxy.

---

### Post by SunnyRabbiera on 2007-12-15
maybe...
do you live in japan might I ask?

---

### Post by bentot on 2007-12-15
No I am currently in New Zealand. But as I have said I have tried many different repositories, including the one here in NZ. I get the same error in all of them. Japan repo is only one of those I have tried.

---

### Post by g2g591 on 2007-12-15
try using the contents of my sources, that work fine for me. 

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by bentot on 2007-12-15
I think I have found the problem; clues on the lines below:

As you can see below, I get an error when I issue the command sudo apt-get update
benny@Kubuntu-VM:~$ sudo apt-get update
Err [ftp://ftp.ecc.u-tokyo.ac.jp](ftp://ftp.ecc.u-tokyo.ac.jp) gutsy Release.gpg
Could not connect to ftp.ecc.u-tokyo.ac.jp:21 (1.0.0.0), connection timed out
0% [Connecting to ftp.ecc.u-tokyo.ac.jp (1.0.0.0)]
benny@Kubuntu-VM:~$

I can confirm that I have a working internet connection. Immediate after the above, I ping the site and was able to get a response:

benny@Kubuntu-VM:~$ ping ftp.ecc.u-tokyo.ac.jp
PING sb.itc.u-tokyo.ac.jp (133.11.205.121) 56(84) bytes of data.
64 bytes from ftp.ecc.u (133.11.205.121): icmp_seq=1 ttl=46 time=95.9 ms
64 bytes from ftp.ecc.u (133.11.205.121): icmp_seq=2 ttl=46 time=97.1 ms
64 bytes from ftp.ecc.u (133.11.205.121): icmp_seq=3 ttl=46 time=94.8 ms
64 bytes from ftp.ecc.u (133.11.205.121): icmp_seq=4 ttl=46 time=80.4 ms
64 bytes from ftp.ecc.u (133.11.205.121): icmp_seq=5 ttl=46 time=84.6 ms

Seems to be a problem with my DNS settings: apt-get seems to be unable to convert the name to an IP address while ping was able to.

I have an ADSL connection and am using a router modem. When I checked my DNS setting, its got the address of the router. When I added the DNS settings from my provider I was able to run apt-get successfully.

Thanks for those who replied. Hopefully the above would help others who are having a hard time with repositories.

Cheers!
Benny

---

### Post by JessT on 2007-12-20
I had a similar problem, and this solution has worked for me.

I have ADSL coming in a NetComm modem/router, which my Ubuntu box is plugged into.
After the fresh install of Gusty Gibbon (7.10), internet connections worked fine, but every repository failed with either;

Read error 113 (no route to host)

or

Connection timed out

I obtained my ISP's DNS information from my router's connection information, then went to System -> Administration -> Network -> DNS and changed the IP addresses from that of my router to those of my ISP.

Everything then worked perfectly.

Thank you for posting this information up, it was extremely helpful!

Cheers,
Jess - [http://jt0.org](http://jt0.org)

PS
I also tried the Netboot installation of 7.10 previously, but it failed with a very ambiguous error when trying to connect to security.ubuntu.com, yet it was successfully connecting to the normal archive servers.
It would appear that this is due to the same issue, so if anyone is having problem installing the netboot image, try a direct net connection, or attempt to set the DNS information during the install (impossible?).

---

