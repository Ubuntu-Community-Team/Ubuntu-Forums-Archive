---
title: "Error in synaptic"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-12-11
I try to download a file on synaptic, but it gives me the following error:

```

W: Failed to fetch http://ar.archive.ubuntu.com/ubuntu/pool/main/c/compiz-fusion-plugins-main/compiz-fusion-plugins-main_0.5.2+git20070928-0ubuntu2_i386.deb
  404 Not Found

```

What can it be?

---

### Post by PmDematagoda on 2007-12-11
Do:-
```

sudo apt-get update
```

And post the result.

---

### Post by Fixman on 2007-12-11
```

martin@Ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release
Hit http://security.ubuntu.com gutsy-security/main Packages
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Ign http://ar.archive.ubuntu.com gutsy Release.gpg
Ign http://ar.archive.ubuntu.com gutsy/main Translation-en_US
Ign http://ar.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://ar.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://ar.archive.ubuntu.com gutsy/multiverse Translation-en_US
Ign http://ar.archive.ubuntu.com gutsy-updates Release.gpg
Ign http://ar.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://ar.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://ar.archive.ubuntu.com gutsy-updates/universe Translation-en_US      
Ign http://ar.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US    
Ign http://ar.archive.ubuntu.com gutsy Release                                 
Ign http://ar.archive.ubuntu.com gutsy-updates Release                         
Ign http://ar.archive.ubuntu.com gutsy/main Packages                           
Ign http://ar.archive.ubuntu.com gutsy/restricted Packages                     
Ign http://ar.archive.ubuntu.com gutsy/main Sources                            
Ign http://ar.archive.ubuntu.com gutsy/restricted Sources                      
Ign http://ar.archive.ubuntu.com gutsy/universe Packages                       
Ign http://ar.archive.ubuntu.com gutsy/universe Sources                        
Ign http://ar.archive.ubuntu.com gutsy/multiverse Packages                     
Ign http://ar.archive.ubuntu.com gutsy/multiverse Sources
Ign http://ar.archive.ubuntu.com gutsy-updates/main Packages
Ign http://ar.archive.ubuntu.com gutsy-updates/restricted Packages
Ign http://ar.archive.ubuntu.com gutsy-updates/main Sources
Ign http://ar.archive.ubuntu.com gutsy-updates/restricted Sources
Ign http://ar.archive.ubuntu.com gutsy-updates/universe Packages
Ign http://ar.archive.ubuntu.com gutsy-updates/universe Sources
Ign http://ar.archive.ubuntu.com gutsy-updates/multiverse Packages
Ign http://ar.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://ar.archive.ubuntu.com gutsy/main Packages
Hit http://ar.archive.ubuntu.com gutsy/restricted Packages
Hit http://ar.archive.ubuntu.com gutsy/main Sources
Hit http://ar.archive.ubuntu.com gutsy/restricted Sources
Hit http://ar.archive.ubuntu.com gutsy/universe Packages
Hit http://ar.archive.ubuntu.com gutsy/universe Sources
Hit http://ar.archive.ubuntu.com gutsy/multiverse Packages
Hit http://ar.archive.ubuntu.com gutsy/multiverse Sources
Hit http://ar.archive.ubuntu.com gutsy-updates/main Packages
Hit http://ar.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://ar.archive.ubuntu.com gutsy-updates/main Sources
Hit http://ar.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://ar.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://ar.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://ar.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://ar.archive.ubuntu.com gutsy-updates/multiverse Sources
Fetched 1B in 18s (0B/s) 
Reading package lists... Done

```

---

### Post by PmDematagoda on 2007-12-11
Now try installing Compiz-fusion again.

---

### Post by Fixman on 2007-12-11
The server is down - I pinged it, and I got no answer. Im downloading from another server now, throught, so thanks anyway.

---

