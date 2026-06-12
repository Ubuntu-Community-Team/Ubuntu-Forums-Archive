---
title: "Repositories, 403 error across the board"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by itzpapalotl on 2007-02-07
The following errors occur every time I try to use synaptic package manager. [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.35 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.35 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.35 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.35 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.35 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.35 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.35 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.35 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.35 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.35 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.35 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.35 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.35 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.35 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.35 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.38 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.38 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.38 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.38 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:) 403 Forbidden


Here is the contents of etc/apt.sources.list

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

I'd just LOVE to install some software. Heck if I can get quake2 running I might never use windows again.

---

### Post by punx45 on 2007-02-07
no clue why that is happening.   you can try out my sources.list (backup yours first)
or [check out this repository guide]("http://www.psychocats.net/ubuntu/sources") and take the sources.list from there. (make sure you copy the dapper one)

in terminal do a 'sudo aptitude update' each time you change the sources.list

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

## AUTOMATIX SCRIPT
deb http://www.getautomatix.com/apt dapper main

```

---

### Post by Quintin Riis on 2007-02-07
Look up your IP / hostname on dshield.org.

---

### Post by itzpapalotl on 2007-03-15
Okay, so No luck at all, but I did find my IP address at dshield. Now... Absolute beginner here remember, and taking a fair sized school along with me on this ride. So, what do I do with the fact that dshield knows who my provider is.  It doesn't contain any flags or warnings, just yes... this exists, and these guys run it. this 403 business is a deal breaker on a project that involves a lot people and a fair chunk of time and money. I can't run ubuntu without being able to get at the repositories. 

Anybody? Anything? Pretty please? Wild guesses even?

---

### Post by keller.baum on 2007-04-13
I have a similar error except it is only occurs with some files in a single repository;
the 386 and amd64 versions give me:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main linux-image-2.6.20-14-generic 2.6.20-14.23
  403 Forbidden [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_amd64.deb)  403 Forbidden [IP: 91.189.89.6 80]

The error seems to only be with kernel components ending in the 14.23 version, all others work fine

Not sure if these are related - might the files be temporarily locked while devs are updating?

---

### Post by STREETURCHINE on 2007-04-13
this is from a google search of the error code,
i could be wrong but since you are using the ce version it could be blocking this address


header("HTTP/1.0 403 Forbidden");
"I'm Catholic."

10.4.4 403 Forbidden

The server understood the request, but is refusing to fulfill it. Authorization will not help and the request SHOULD NOT be repeated. If the request method was not HEAD and the server wishes to make public why the request has not been fulfilled, it SHOULD describe the reason for the refusal in the entity. If the server does not wish to make this information available to the client, the status code 404 (Not Found) can be used instead.

---

### Post by TabletUbuntu on 2007-04-13
I just had the same error on the same file.  I can access other files, but not that one.

---

### Post by Seisen on 2007-04-13
Its because the kernel is broken that is why you can't download the kernel. They are working on it.

---

### Post by Seisen on 2007-04-13
Have you tried using the source list here.

[http://ubuntuguide.org/wiki/Ubuntu_dapper]("http://ubuntuguide.org/wiki/Ubuntu_dapper")

or it could be apt itself. Post what this says, this might be the problem too.

```
sudo gedit /etc/apt/apt.conf
```

---

### Post by tflanders on 2007-04-13
I get this error when running updates. I hope its fixed soon

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb)
  403 Forbidden [IP: 91.189.89.8 80]


Going to the directory ([http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/)) where that file lives shows that its there. I just can't download linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb. All other files I clicked on ask to be downloaded. Seems like a permissions issue on the website since a 403 I believe means access denied.

Is it possible they are restricting access because they fixing that kernel package? It's the only one that doesn't download for me. Bummer. It's been broke for me the last 12 hours.

---

### Post by Seisen on 2007-04-13
Its because the kernel is broke right now and they are going to fix it. Everybody that is running feisty is going to have this problem.

---

### Post by itzpapalotl on 2007-04-15
All problems with 14.23 aside... I was able to solve my original problem by switching every instance of http:// /etc/apt/sources.list to [ftp://.](ftp://.).. Now... it doesn't explain the original problem, but it does solve it... I'm pretty sure I failed to asses how persnickety the company's firewall was about the kind of stuff that makes up a .deb package, and how difficult is is to remove the filtering service from this thing. Useless for anything but teaching students how to find Proxies, and blocking Linux updates. ;)  Good luck to all y'all
=|==> 8i8

---

### Post by gordwait on 2007-04-25
Same problem, same fix for me too. 

Is there any ubuntu staff looking into why we have to switch to ftp protocol to update ubuntu?
This was working for my system, then within the last few weeks the update manager failed to update because of this. 

Is my ISP blocking http file transfers, or is the server blocking it? 

Weird.

---

### Post by itzpapalotl on 2007-04-26
I'm thinking a lot of this stuff is can be traced back to overzealous firewalls. ftp did the job....

---

