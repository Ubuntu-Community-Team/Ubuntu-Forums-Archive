---
title: "New to Ubuntu - update problems"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Philmc on 2007-01-23
I have just installed Ubuntu edgy and got pretty much everything up and running. 

However I seem to run into a problem when I try to get updates. The same is true of the terminal and synaptics package manager. 

Here is my sources.list:


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe #Added by software-properties

# Uncomment the following two lines to add software from the 'universe'
# repository.
# N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
# team, and may not be under a free licence. Please satisfy yourself as to
# your rights to use the software. Also, please note that software in
# universe WILL NOT receive any review or updates from the Ubuntu security
# team.
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

Any help or suggestions would be appreciated.

---

### Post by taurus on 2007-01-23
What's the error message when you run this command from a terminal?

```
sudo aptitude update
```

---

### Post by meng on 2007-01-23
What problem are you getting?

---

### Post by Philmc on 2007-01-23
The error I get is:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                        
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg                                  
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                       
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.c

The problem I get is that I can't get any updates.

Thanks

---

### Post by meng on 2007-01-23
Well the problem isn't related to your sources.list. I assume your internet connection is working for everything else. I have seen a similar problem related to the installation of package anon-proxy, and solved by removing that package.

---

### Post by Philmc on 2007-01-23
From what I can see it is not installed

how should I check?

Phil

EDIT so far all I have done was the installation and set up the internet connection.

---

### Post by meng on 2007-01-23
If you didn't manually install anon-proxy, then we can assume it's not installed. But would you please confirm that your internet connection is working?

---

### Post by Philmc on 2007-01-24
Yes the internet connection is working.

---

### Post by Philmc on 2007-01-25
anyone have any Ideas as to what my problem might be.

sorry for bumping this up

Phil

---

### Post by Shatrat on 2007-01-25
What happens when you type "ping archive.ubuntu.com" in terminal?

---

### Post by Philmc on 2007-01-27
This is the result of the ping:

~$ ping archive.ubuntu.com
PING archive.ubuntu.com (195.248.90.35) 56(84) bytes of data.
64 bytes from archive.ubuntu.com (195.248.90.35): icmp_seq=1 ttl=55 time=37.6 ms
64 bytes from archive.ubuntu.com (195.248.90.35): icmp_seq=2 ttl=55 time=35.6 ms
64 bytes from archive.ubuntu.com (195.248.90.35): icmp_seq=3 ttl=55 time=42.6 ms
64 bytes from archive.ubuntu.com (195.248.90.35): icmp_seq=4 ttl=55 time=35.6 ms
64 bytes from archive.ubuntu.com (195.248.90.35): icmp_seq=5 ttl=55 time=35.8 ms
64 bytes from archive.ubuntu.com (195.248.90.35): icmp_seq=6 ttl=55 time=38.7 ms
64 bytes from archive.ubuntu.com (195.248.90.35): icmp_seq=7 ttl=55 time=44.2 ms
64 bytes from archive.ubuntu.com (195.248.90.35): icmp_seq=8 ttl=55 time=35.3 ms
64 bytes from archive.ubuntu.com (195.248.90.35): icmp_seq=9 ttl=55 time=38.2 ms
64 bytes from archive.ubuntu.com (195.248.90.35): icmp_seq=10 ttl=55 time=37.8 ms
64 bytes from archive.ubuntu.com (195.248.90.35): icmp_seq=11 ttl=55 time=35.8 ms
64 bytes from archive.ubuntu.com (195.248.90.35): icmp_seq=12 ttl=55 time=35.5 ms
64 bytes from archive.ubuntu.com (195.248.90.35): icmp_seq=13 ttl=55 time=40.5 ms
64 bytes from archive.ubuntu.com (195.248.90.35): icmp_seq=14 ttl=55 time=35.4 ms
64 bytes from archive.ubuntu.com (195.248.90.35): icmp_seq=15 ttl=55 time=35.9 ms
64 bytes from archive.ubuntu.com (195.248.90.35): icmp_seq=16 ttl=55 time=35.6 ms

--- archive.ubuntu.com ping statistics ---
16 packets transmitted, 16 received, 0% packet loss, time 15046ms
rtt min/avg/max/mdev = 35.375/37.549/44.279/2.676 ms

EDIT: Well is seems to have now resolved itself somehow. When I open Synaptic it did download some updates.

Thanks for the help.

Phil

---

### Post by moredhel on 2007-01-27
I had that problem as well, then it worked again after a few minutes. Perhaps the servers went down for a few minutes :-S

---

### Post by Philmc on 2007-01-27
I spoke to soon. Still having problems. 

sudo aptitude update:

~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg                                  
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                        
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                       
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US                 
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                 
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US       
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                   
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                   
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg                          
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US               
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US         
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US         
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US           
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                 
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources                                 
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                 
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources 
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Reading package lists... Done


And when I try to reload from Synaptics I get this error:

ttp://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg: Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)

---

### Post by leg on 2007-01-27
> **Philmc said:**
> anyone have any Ideas as to what my problem might be.

sorry for bumping this up

Phil

try changing system > network > dns to match the contents of resolv.conf this fixed this issue for me. I think it may be this because the address you get in the error message is 1.0.0.0 If this is not set are you using a router if so copy the ip address of your dns server on the router to both /etc/resolv.conf & system > network > dns

---

### Post by Philmc on 2007-01-27
The contents of the resolve.conf and system > network > dns already match. it is the address of my router.

EDIT

I have changed it to the DNS addresses from my router.

Here are the new results from aptitude update and upgrade:

~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources
Fetched 573B in 1s (527B/s)
Reading package lists... Done
phil@phil-desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  app-install-data-commercial avahi-daemon capplets-data dbus dbus-1-utils 
  evince firefox firefox-gnome-support gdm gimp gimp-data gimp-python 
  gnome-applets gnome-applets-data gnome-control-center gnome-games 
  gnome-games-data gnome-netstatus-applet gnome-panel gnome-panel-data 
  gnome-system-tools gnupg info language-pack-en language-pack-gnome-en 
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core4 
  libavahi-glib1 libc6 libc6-i686 libdbus-1-3 libgimp2.0 
  libgnome-window-settings1 libgnomeprintui2.2-0 libgnomeprintui2.2-common 
  libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra 
  libgsf-1-114 libgsf-1-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common 
  libgtop2-7 libgtop2-common libkrb53 libmagick9 libmono-cairo1.0-cil 
  libmono-corlib1.0-cil libmono-data-tds1.0-cil libmono-security1.0-cil 
  libmono-sharpzip0.84-cil libmono-sqlite1.0-cil libmono-system-data1.0-cil 
  libmono-system-web1.0-cil libmono-system1.0-cil libmono0 libmono1.0-cil 
  libnspr4 libnss3 libpanel-applet2-0 libpng12-0 libpoppler1 
  libpoppler1-glib libsoup2.2-8 libtotem-plparser1 linux-headers-2.6.17-10 
  linux-headers-2.6.17-10-generic linux-image-2.6.17-10-generic 
  linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common mono-common mono-gac mono-jit 
  mono-runtime openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-default openoffice.org-style-industrial 
  openoffice.org-writer poppler-utils python-uno screen 
  system-tools-backends tar totem totem-gstreamer totem-mozilla 
  ttf-opensymbol tzdata vino w3m x11-common xbase-clients xorg xserver-xorg 
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-video-all xutils 
113 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 178MB of archives. After unpacking 4055kB will be used.
Do you want to continue? [Y/n/?] y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main libc6 2.4-1ubuntu12.3           
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main tar 1.15.91-2ubuntu0.3        
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main libc6-i686 2.4-1ubuntu12.3
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libdbus-1-3 0.93-0ubuntu3.1   
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main x11-common 1:7.1.1ubuntu6.2     
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libpng12-0 1.2.8rel-5.1ubuntu0.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main language-pack-en 1:6.10+20061130
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libavahi-common-data 0.6.13-2ubuntu2.4
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main language-pack-gnome-en 1:6.10+20061201
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libavahi-common3 0.6.13-2ubuntu2.4
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main openoffice.org-style-industrial 2.0.4-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libavahi-client3 0.6.13-2ubuntu2.4
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main openoffice.org-style-default 2.0.4-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libavahi-glib1 0.6.13-2ubuntu2.4
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libkrb53 1.4.3-9ubuntu1.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main dbus 0.93-0ubuntu3.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main openoffice.org-calc 2.0.4-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main python-uno 2.0.4-0ubuntu4       
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main openoffice.org-writer 2.0.4-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main screen 4.0.2-4.1ubuntu5.6.10
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main openoffice.org-impress 2.0.4-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main xserver-xorg-core 1:1.1.1-0ubuntu12.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main openoffice.org-draw 2.0.4-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main gnupg 1.4.3-2ubuntu3.2        
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main openoffice.org-java-common 2.0.4-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main info 4.8.dfsg.1-1ubuntu0.1    
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main openoffice.org-base 2.0.4-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main libgtk2.0-common 2.10.6-0ubuntu3
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main libgtk2.0-bin 2.10.6-0ubuntu3
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main libgtk2.0-0 2.10.6-0ubuntu3
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main w3m 0.5.1-4ubuntu2.6.10       
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main openoffice.org-gtk 2.0.4-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libavahi-core4 0.6.13-2ubuntu2.4
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main libgnomevfs2-extra 2.16.1-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main avahi-daemon 0.6.13-2ubuntu2.4
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main libgnomevfs2-0 2.16.1-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main dbus-1-utils 0.93-0ubuntu3.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main libgnomevfs2-common 2.16.1-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libpoppler1-glib 0.5.4-0ubuntu4.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main openoffice.org-gnome 2.0.4-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libpoppler1 0.5.4-0ubuntu4.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main openoffice.org-evolution 2.0.4-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main evince 0.6.1-0ubuntu1.2
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main openoffice.org-math 2.0.4-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main firefox-gnome-support 2.0.0.1+0dfsg-0ubuntu0.6.10
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main openoffice.org 2.0.4-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libnspr4 2:1.firefox2.0.0.1+0dfsg-0ubuntu0.6.10
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main ttf-opensymbol 2.0.4-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libnss3 2:1.firefox2.0.0.1+0dfsg-0ubuntu0.6.10
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main openoffice.org-core 2.0.4-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main firefox 2.0.0.1+0dfsg-0ubuntu0.6.10
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main openoffice.org-common 2.0.4-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main gdm 2.16.1-0ubuntu4.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main xserver-xorg-video-all 1:7.1.1ubuntu6.2
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libgtop2-common 2.14.4-0ubuntu1.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main xserver-xorg-input-all 1:7.1.1ubuntu6.2
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libgtop2-7 2.14.4-0ubuntu1.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main xutils 1:7.1.1ubuntu6.2
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libgsf-1-common 1.14.1-2ubuntu1.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main xbase-clients 1:7.1.1ubuntu6.2
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libgsf-1-114 1.14.1-2ubuntu1.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main xserver-xorg 1:7.1.1ubuntu6.2
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libmagick9 7:6.2.4.5.dfsg1-0.10ubuntu0.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main tzdata 2006p-0ubuntu6.10
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main mono-runtime 1.1.17.1-1ubuntu7.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main app-install-data-commercial 6.3
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main gnome-control-center 1:2.16.1-0ubuntu4.2
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main libgnome-window-settings1 1:2.16.1-0ubuntu4.2
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main capplets-data 1:2.16.1-0ubuntu4.2
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main mono-gac 1.1.17.1-1ubuntu7.1  
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main mono-jit 1.1.17.1-1ubuntu7.1  
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main mono-common 1.1.17.1-1ubuntu7.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libmono0 1.1.17.1-1ubuntu7.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main gimp 2.2.13-1ubuntu3
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libmono-corlib1.0-cil 1.1.17.1-1ubuntu7.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main gimp-data 2.2.13-1ubuntu3
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libmono-cairo1.0-cil 1.1.17.1-1ubuntu7.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main libgimp2.0 2.2.13-1ubuntu3
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libmono-system1.0-cil 1.1.17.1-1ubuntu7.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main gimp-python 2.2.13-1ubuntu3
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libmono-security1.0-cil 1.1.17.1-1ubuntu7.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main libpanel-applet2-0 2.16.1-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libmono-data-tds1.0-cil 1.1.17.1-1ubuntu7.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main gnome-applets 2.16.1-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libmono-sharpzip0.84-cil 1.1.17.1-1ubuntu7.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main gnome-applets-data 2.16.1-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libmono-system-data1.0-cil 1.1.17.1-1ubuntu7.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main gnome-panel 2.16.1-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libmono-sqlite1.0-cil 1.1.17.1-1ubuntu7.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main gnome-panel-data 2.16.1-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main gnome-games 1:2.16.1-0ubuntu3
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main gnome-games-data 1:2.16.1-0ubuntu3
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main gnome-netstatus-applet 2.12.0-5ubuntu7
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main libgnomeprintui2.2-0 2.12.1-4ubuntu2
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main libgnomeprintui2.2-common 2.12.1-4ubuntu2
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main libgnomevfs2-bin 2.16.1-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libmono-system-web1.0-cil 1.1.17.1-1ubuntu7.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libmono1.0-cil 1.1.17.1-1ubuntu7.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libsoup2.2-8 2.2.96-0ubuntu2.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main linux-headers-2.6.17-10 2.6.17.1-10.34
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main linux-headers-2.6.17-10-generic 2.6.17.1-10.34
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main linux-image-2.6.17-10-generic 2.6.17.1-10.34
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted linux-restricted-modules-common 2.6.17.7-10.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main libtotem-plparser1 2.16.2-0ubuntu3
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted linux-restricted-modules-2.6.17-10-generic 2.6.17.7-10.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main gnome-system-tools 2.15.5-0ubuntu5
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main poppler-utils 0.5.4-0ubuntu4.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main system-tools-backends 1.9.7-0ubuntu5
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main totem-gstreamer 2.16.2-0ubuntu3
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main totem 2.16.2-0ubuntu3
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main totem-mozilla 2.16.2-0ubuntu3
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main vino 2.16.0-0ubuntu2.4
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main xorg 1:7.1.1ubuntu6.2
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)

---

### Post by Philmc on 2007-01-28
It seems that whenever I try to update or install anything the IP address in the terminal, synaptic, add/remove comes back as 1.0.0.0

---

