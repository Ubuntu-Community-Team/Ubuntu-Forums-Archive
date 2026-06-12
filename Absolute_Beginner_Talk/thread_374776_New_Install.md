---
title: "New Install"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by gugglix on 2007-03-02
Hi,

I just finished installing Ubuntu 6.06 and got this error when I logged in for the first time and tried to download updates:

'COULD NOT DOWNLOAD ALL REPOSITORY INDEXES'. What does this mean? Is it critical? As a result I cannot dowload any updates.

When I select 'Community Maintained' from Software preferences the option of installing 'non-authenticated' updates is given to me. Are these safe?

Cheers, Michael.

---

### Post by taurus on 2007-03-02
Open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here.

```
cat /etc/apt/sources.list
```

---

### Post by gugglix on 2007-03-02
WOW!! thanks for the quick reply!!!

This is the response that I got
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by taurus on 2007-03-02
Okay, edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
sudo cp /etc/apt/sources.list  /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list
```
and remove the # in font of all the lines with deb at the beginning and remove the **au.** from those repos/lines as well.

Save the changes and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by gugglix on 2007-03-02
Ok, did what you suggested, and the FSTAB file didn't have any of the lines in it. So I edited the file /etc/apt/sources.list and removed the bits you said and ran the commands you suggested and the response after the first command was either ERR or IGN and the response after the second command was No packages will be installed, upgraded or removed.

Thanks again for the quick responses!!!!!

---

### Post by taurus on 2007-03-02
Can you post the complete output after you run the first command?

```
sudo aptitude update
```

---

### Post by gugglix on 2007-03-02
Ok, here you go....
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 91.189.89.6 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 91.189.89.6 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Connection failed [IP: 91.189.89.6 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
  Connection failed [IP: 91.189.89.6 80]
Reading package lists... Done

---

### Post by taurus on 2007-03-02
Is your network working at all?  Are you behind a proxy or something?  I didn't have any problem pinging that repo.

```

ping -c 3 91.189.89.6
PING 80 (0.0.0.80) 56(124) bytes of data.

--- 80 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

osprey:/home/50/n00010150:% ping -c 3 91.189.89.6 
PING 91.189.89.6 (91.189.89.6) 56(84) bytes of data.
64 bytes from 91.189.89.6: icmp_seq=0 ttl=46 time=113 ms
64 bytes from 91.189.89.6: icmp_seq=1 ttl=46 time=113 ms
64 bytes from 91.189.89.6: icmp_seq=2 ttl=46 time=113 ms

--- 91.189.89.6 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 113.242/113.330/113.433/0.285 ms, pipe 2

```

---

### Post by gugglix on 2007-03-02
Well, I assume it's working ok - I can post here and browse to other sites. I have a small netgear router, but that's only filtering a couple of ad sites. Pings worked....

I have to go out now, so don't get too worked up about it. I'll check back here in about 2 hours.

Thanks again, Michael.

---

### Post by Kateikyoushi on 2007-03-03
You could try to change http to ftp in the sources list, some people reported that helped.

---

### Post by gugglix on 2007-03-03
BINGO!!!

Everything seems ok now.

I cannot thank you enough for your quick responses - AWESOME!!!!

Cheers, Michael.

---

