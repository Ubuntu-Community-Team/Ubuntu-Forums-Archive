---
title: "sudo apt-get update problem"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by dwoodnz on 2007-11-30
hey all

im trying to update my system and the following is coming up..

```

justin@justin-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_NZ
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_NZ
Err http://nz.archive.ubuntu.com gutsy Release.gpg                             
  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Err http://nz.archive.ubuntu.com gutsy/main Translation-en_NZ                
  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Err http://nz.archive.ubuntu.com gutsy/restricted Translation-en_NZ
  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Err http://nz.archive.ubuntu.com gutsy/universe Translation-en_NZ
  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Err http://nz.archive.ubuntu.com gutsy/multiverse Translation-en_NZ
  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Err http://nz.archive.ubuntu.com gutsy-updates Release.gpg
  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Err http://nz.archive.ubuntu.com gutsy-updates/main Translation-en_NZ
  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Err http://nz.archive.ubuntu.com gutsy-updates/restricted Translation-en_NZ
  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Err http://nz.archive.ubuntu.com gutsy-updates/universe Translation-en_NZ
  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Err http://nz.archive.ubuntu.com gutsy-updates/multiverse Translation-en_NZ
  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_NZ
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_NZ
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_NZ
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_NZ
Hit http://security.ubuntu.com gutsy-security Release
Hit http://security.ubuntu.com gutsy-security/main Packages
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Fetched 1B in 2s (0B/s)  
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_NZ.bz2  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_NZ.bz2  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_NZ.bz2  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_NZ.bz2  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_NZ.bz2  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_NZ.bz2  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_NZ.bz2  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_NZ.bz2  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
justin@justin-desktop:~$ 

```

im very new to linux so any ideas slash help would be greatly appreciated!
thanks for your time

---

### Post by TNakos on 2007-11-30
I beleive those were the updates they blocked. but im not sure. just unmark them.

---

### Post by dwoodnz on 2007-11-30
i wouldnt know..

how do you unblock them if im trying to do it through a terminal if that is the problem?
wouldnt it be best to get all this is to offer when updating though? must be some way of working it out :S?

---

### Post by fineas on 2007-11-30
Check this out and tell us what happens:
Go to system>administration>synaptic package manager.Then settings>repositories. 
Have you enabled the "extra" repositories in the first tab?
Tick every option available in second and third tab (third party software and updates). Now you should be able to unblock them.

---

### Post by Pumalite on 2007-11-30
It seems your errors correspond to 'Translation-en_NZ' only. Maybe changing the server will help. Not sure.

---

### Post by paulita on 2007-11-30
I recomend you to download the cd image from a Torrent. That way you can be sure you have everything. Once I tried to update as you are doing and maybe some important package didn't download properly. Then i couldn't even turn on my computer and had to start all over again with the cd somebody lent me.

---

### Post by dwoodnz on 2007-11-30
ooo thanks guys, it worked when i changed the server to main rather than new zealand :)
so far so good

---

