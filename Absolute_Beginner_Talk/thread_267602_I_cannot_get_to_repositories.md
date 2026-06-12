---
title: "I cannot get to repositories"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by morfy on 2006-09-28
This is what I get when i try to update and reload through synaptic: Any ideas?????????????

[http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out

---

### Post by ewl1217 on 2006-09-28
At the terminal type the following command and post its output here:
```
cat /etc/apt/sources.list
```

**EDIT:** I just tried going to those links and they worked fine (although I had to remove the colon at the end). Does anything else not work with your Internet connection?

---

### Post by orb9220 on 2006-09-28
Could be the aussie site is down? Try again later.

Ubuntu servers do go down occasionally.

---

### Post by Kateikyoushi on 2006-09-28
I can browse it, seems it's up.

---

### Post by morfy on 2006-09-28
> **ewl1217 said:**
> At the terminal type the following command and post its output here:
```
cat /etc/apt/sources.list
```

**EDIT:** I just tried going to those links and they worked fine (although I had to remove the colon at the end). Does anything else not work with your Internet connection?

here is the info:

# Line commented out by installer because it failed to verify:
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)]/ dapper main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted

---

### Post by ewl1217 on 2006-09-28
Your sources.list seems fine. All I can imagine is that it's a firewall / Internet connection issue. I can't really help you there.

---

### Post by hyper7 on 2006-09-28
All of your repositories are accesible for me.  

I can't see how this would be a firewall issue, but perhaps it's related.  Might be a good idea to post your firewall setup(if you have one).

These being blocked by your ISP seems unlikely.

---

