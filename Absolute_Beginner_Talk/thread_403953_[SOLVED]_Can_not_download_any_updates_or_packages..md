---
title: "[SOLVED] Can not download any updates or packages."
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Mahmoud Refat on 2007-04-07
I have  a prolem when i try to update the kernel. 
when i type
apt-get update
i get 
Reading package lists... Done
but nothing actually happened so when i opened the file /etc/apt/sources.list, i found it commented due to some errors, check it out:

# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

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
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


when i uncomment some urls and try to update again, i got connection failed. (time out) , does anyone knows why? this drives me crazy and i can download NOTHING..

apt-get update
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://flomertens.free.fr](http://flomertens.free.fr) dapper Release.gpg
  Could not connect to flomertens.free.fr:80 (1.0.0.0), connection timed out
Err [http://flomertens.keo.in](http://flomertens.keo.in) dapper Release.gpg
  Could not connect to flomertens.keo.in:80 (1.0.0.0), connection timed out
Err [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper Release.gpg
  Could not connect to ntfs-3g.sitesweetsite.info:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://flomertens.free.fr/ubuntu/dists/dapper/Release.gpg](http://flomertens.free.fr/ubuntu/dists/dapper/Release.gpg)  Could not connect to flomertens.free.fr:80 (1.0.0.0), connection timed out
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/Release.gpg](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/Release.gpg)  Could not connect to ntfs-3g.sitesweetsite.info:80 (1.0.0.0), connection timed out
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/dapper/Release.gpg](http://flomertens.keo.in/ubuntu/dists/dapper/Release.gpg)  Could not connect to flomertens.keo.in:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.


thank you,
Mahmoud

---

### Post by Pikestaff on 2007-04-07
I had a similar problem once; double check your connection settings to make sure your Gateway and Primary DNS aren't set to the same number.  If they are you will probably have some issues like the one you're having right now.

You can try replacing the Primary DNS with something from OpenDNS (for example, 208.67.222.222) and seeing if that helps.

---

### Post by Mahmoud Refat on 2007-04-12
Thank you so much it worked and now i can download updates and actually START using kubuntu.


thank you :o

---

### Post by FuriousLettuce on 2007-04-12
It's quite likely that your router can't handle IPv6 DNS requests - setting the DNS to open DNS fixed this. To change it permenantly in firefox, type about:config in the address bar, then type 'ipv6' (without the quotes) in the search box, and set the resulting setting to true (double click). It's then worth disabling IPv6 system wide (search blacklist ipv6 in the forum search engine).

---

