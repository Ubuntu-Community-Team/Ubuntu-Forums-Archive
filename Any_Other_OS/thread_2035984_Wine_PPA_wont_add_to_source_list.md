---
title: "Wine PPA wont add to source list"
date: 2012-07-31
forum: Any Other OS
---

### Post by Jobbo256 on 2012-07-31
When adding in the Software center, nothing happens.  I have checked the list multiple times, but every time the source doesn't show. I have also tried using the terminal, but I get this: > Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: "Launchpad PPA for Ubuntu Wine Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
Any ideas about what's wrong? I have Super OS(Ubuntu) 11.04 with wine 1.3 already installed, and so far everything else works. There is a source already in the list, but it has old outdated releases which I guess is where the current wine is from.([http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu))

---

### Post by critin on 2012-07-31
> There is a source already in the list, but it has old outdated releases

I've used SuperOS and liked it very much.  
I believe the included ppa is what that particular distro uses for their own version.   I would ask on their forum before trying to change it because some things may not work properly with their configurations.

---

### Post by oldos2er on 2012-08-01
Moved to Other OS/Distro Talk.

---

