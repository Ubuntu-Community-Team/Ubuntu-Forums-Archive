---
title: "Updates not working"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Ajay Ramaseshan on 2007-10-20
I tried installing updates on Ubuntu 7.04 using the command sudo apt-get update.
But it shows these errors
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
and many more similar messages.
Then it shows 
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
  307 Authorization Redirect
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
  307 Authorization Redirect
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  307 Authorization Redirect
and finally
Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://lk.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  307 Authorization Redirect [IP: 91.189.88.45 80]
E: Some index files failed to download, they have been ignored, or old ones used instead.
. 
Could you please tell me what is wrong?

---

### Post by mikeyphi on 2007-10-20
No probs - you just updated Feisty. To Upgrade use the Update Managed GUI under System/Administration....Following a 'check for updates' you should be offered the upgrade.
Read here first: [http://www.ubuntulinux.org/getubuntu/upgrading](http://www.ubuntulinux.org/getubuntu/upgrading)

---

### Post by Ajay Ramaseshan on 2007-10-27
But that 's not the problem . Its that updates on Ubuntu 7.04 itself are not working.I have not upgraded to Ubuntu 7.10

---

### Post by Maestro23 on 2007-10-27
> **Ajay Ramaseshan said:**
> But that 's not the problem . Its that updates on Ubuntu 7.04 itself are not working.I have not upgraded to Ubuntu 7.10

Post your /etc/apt/sources.list


> cat /etc/apt/sources.list

---

