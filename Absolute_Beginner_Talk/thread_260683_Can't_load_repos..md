---
title: "Can't load repos."
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by Squrdel on 2006-09-19
I have tried every way I can find to load the repos through Synaptic and usin g get-apt. They just will not load, any advice/suggestions?

---

### Post by risbac on 2006-09-19
> They just will not load, any advice/suggestions?

Yes. 

```
Sudo apt-get update 
```

in a terminal. And copy paste here the error message. We need to know more to help you.

---

### Post by Squrdel on 2006-09-19
Thanks risbac, here is the full text:

lewis@Hal:~$ sudo apt-get update
0% [Connecting to uk.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)] [Conn Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://uk.archive.ubuntu.com dapper Release.gpg
  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://www.getautomatix.com dapper Release.gpg
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Errhttp://uk.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://uk.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://uk.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/Release.gpg](http://www.getautomatix.com/apt/dists/dapper/Release.gpg)  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
lewis@Hal:~$ sudo apt-get install automatix
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package automatix
lewis@Hal:~$ sudo apt-get update
Password:
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://uk.archive.ubuntu.com dapper Release.gpg
  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://www.getautomatix.com dapper Release.gpg
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Errhttp://uk.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://uk.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://uk.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/Release.gpg](http://www.getautomatix.com/apt/dists/dapper/Release.gpg)  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by risbac on 2006-09-19
Ok, you can't reach the repos, but why.

The usual silly question:
internet is working fine on your computer?

from "Connecting to uk.archive.ubuntu.com (1.0.0.0)", it seems that you try to reach the IP "1.0.0.0", which is obviously not the good one...

So two possible solutions: your /etc/apt/sources.list is totally wrong, or you have a problem with internet. If you tell me that internet works fine, then copy paste your sources.list here plz.

---

### Post by unisol on 2006-09-19
i have a similiar problem;when i use sudo apt-get update i get this message adter connecting to the repos:Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...iverse/source/](http://archive.ubuntu.com/ubuntu/dis...iverse/source/) Sources.gz Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead. i edit my sourcws.lst and still the same message my sources.list is:

here is sources.lst: Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


##############################
### Automatix Repositories ###
##############################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

## created by automatixrepo3
deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen

---

### Post by Squrdel on 2006-09-19
The internet connection is fine, here is the sources.list file.

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

---

### Post by undertherift on 2006-09-19
I've had a similar problem which i fixed by copying someone else's sources.list over my own.  

I'd post mine, but I'm at work.  See if you can find a sources.list from somewhere online. 

Sorry!

---

### Post by DerHesse on 2006-09-19
Are you behind a Proxy? 
Then you could create an apt.conf file in /etc/apt

looks like this

APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "http://*username*:*passwd*@*Proxy_Server_Name*:*Portnumber*";

---

### Post by Squrdel on 2006-09-20
I figured out that there may be a network problem. I checked and found some discrepancies in the network setup on my router - what works for Windows didn't work here. Funny because I had no problem with my DSL connection which is through the router.

Anyway I am sorted now, thanks for your help everyone.

---

