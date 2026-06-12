---
title: "installing software"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by leon7250 on 2007-02-12
Can anyone help with installing software with add/remove ?
Every time i try, i get an error like this.
Any help would be great!!

[http://au.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://au.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2:](http://au.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://au.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2:](http://au.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://au.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2:](http://au.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://au.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2:](http://au.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2:](http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2:](http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2:](http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out

---

### Post by ndefontenay on 2007-02-12
It seems the problem is not with the package manager. It's with your connection!

Are you writing this thread from the same computer or from a different one?

If yes, check whether a firewall is not blocking you from accessing this server.

Try to provide a little more information on your connectivity. 
I think it would help solving your problem.

---

### Post by aysiu on 2007-02-12
Does [this thread](http://www.ubuntuforums.org/showthread.php?p=1963371) help?

---

### Post by leon7250 on 2007-02-12
My connection is DSL with a ethernet connection direct to the modem.
I was using a router and thought that may have been causing the prob. so i removed and still no difference. I think the connection is working fine besause im using the comp. now.

---

### Post by leon7250 on 2007-02-12
Cheers aysiu, but it did'nt work. I tried the code but it keeps saying 
 sudo apt-get resolvconf
Password:
E: Invalid operation resolvconf

---

### Post by seshomaru samma on 2007-02-12
what happens when you run
```
sudo apt-get update
```?

---

### Post by leon7250 on 2007-02-12
Hi seshomaru samma, this is all that happens.
It gets to 24% and hangs.

sudo apt-get update
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
24% [Connecting to au.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]

and then...

Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                                         
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy Release.gpg                                                
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US                              
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/main Translation-en_US                                     
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
24% [Connecting to au.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]

---

### Post by seshomaru samma on 2007-02-13
i am not sure what is the source of your problem , but i think it might be a problem with your sources list.
can you try this:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
(this will back up your old ources list)
and then:
```
sudo gedit /etc/apt/sources.list
```
replace all your sources with this:
> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse


                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main


then 
```
sudo apt-get update
```

---

