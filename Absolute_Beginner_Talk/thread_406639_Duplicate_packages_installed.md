---
title: "Duplicate packages installed"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Radovitch on 2007-04-11
I just finished enabling both Universe and Multiverse repositories in the Package Manager of Drake for Updates, Back Ports and Security Updates and after it finished downloading I got this warning about duplicate installed security packages:

W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_multiverse_binary-i386_Packages)

Will this create any problems?
Thanx

---

### Post by justleen on 2007-04-11
you can open /etc/apt/sources.list, and remove the duplicate entries. Run a apt-get update afterwards, and you should be fine

---

### Post by Radovitch on 2007-04-11
Thanks for the tip. One small problem. I removed the duplicate files with vi and then did the apt-get update but I noticed that no security updates came down the pipeline. So I checked in the software settings of the Package Manager and discovered that the whole Security Updates panel (both source and binary), had completely disappeared. I got the binaries half back ok but need to know how to get the source part back as well. As a newbie I must have deleted too much.

---

### Post by justleen on 2007-04-11
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted multiverse universe


those should be the ones...

---

### Post by Radovitch on 2007-04-11
Got it! Thanks again

---

### Post by jacatone on 2007-04-16
When I tried the /etc/apt/sources.list, I just got a "permission denied" message.

---

### Post by RomeReactor on 2007-04-17
Hi. You must use **sudo** to open the file: In a terminal enter

```
gksudo gedit /etc/apt/sources.list
```

---

