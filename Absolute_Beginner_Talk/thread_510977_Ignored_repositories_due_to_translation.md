---
title: "Ignored repositories due to translation?"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by synd7 on 2007-07-27
I'm no newbie to linux but i anticipate a stupid/obvious answer :p
Heres the output from an repo update
```
ben@ben-desktop:~$ sudo aptitude update && sudo aptitude upgrade
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070718.1) gutsy/main Translation-en_AU
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070718.1) gutsy/restricted Translation-en_AU
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]              
Ign http://security.ubuntu.com gutsy-security/main Translation-en_AU      
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_AU
Get:2 http://archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy/main Translation-en_AU
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_AU
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_AU
Hit http://security.ubuntu.com gutsy-security Release
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_AU
Ign http://archive.ubuntu.com gutsy/universe Translation-en_AU
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_AU
Get:3 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_AU
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_AU
Hit http://security.ubuntu.com gutsy-security/main Packages
Get:4 http://archive.ubuntu.com gutsy Release [65.9kB]
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Get:5 http://archive.ubuntu.com gutsy-updates Release [32.4kB]
Get:6 http://archive.ubuntu.com gutsy/main Packages [1078kB]
Get:7 http://archive.ubuntu.com gutsy/restricted Packages [7213B]               
Get:8 http://archive.ubuntu.com gutsy/main Sources [300kB]                      
Get:9 http://archive.ubuntu.com gutsy/restricted Sources [1840B]                
Get:10 http://archive.ubuntu.com gutsy/universe Packages [3990kB]               
Get:11 http://archive.ubuntu.com gutsy/universe Sources [1220kB]                
Get:12 http://archive.ubuntu.com gutsy/multiverse Packages [157kB]              
Get:13 http://archive.ubuntu.com gutsy/multiverse Sources [56.3kB]              
Get:14 http://archive.ubuntu.com gutsy-updates/main Packages [14B]              
Get:15 http://archive.ubuntu.com gutsy-updates/restricted Packages [14B]        
Get:16 http://archive.ubuntu.com gutsy-updates/main Sources [14B]               
Get:17 http://archive.ubuntu.com gutsy-updates/restricted Sources [14B]
```

What i'm wondering is why a bunch of them are being ignored with the translation information at the end.
Are they really being skipped? Does it matter?


Not a major problem, but its been bugging the crap out of me since i noticed it :D

---

### Post by mikewhatever on 2007-07-27
Do you run Feisty with Gutsy's repositories? Did you know Gutsy is still an alpha?

---

### Post by Majorix on 2007-07-27
I believe he is already on 7.10?

---

### Post by davidjmayo on 2007-07-27
Would it be correct to guess you are using aussie repos? (as it says en_AU at the end of the ones that fail so that's how I spotted it in case u r wondering)

FYI there are issues with the Oz repos - see here [http://ubuntuforums.org/showthread.php?t=508981](http://ubuntuforums.org/showthread.php?t=508981)

---

### Post by synd7 on 2007-07-28
I'm on Gutsy, the oz repos are messed up so i'm using the main ones. The translation bit comes from the fact that i'm using an Australian english language setting. For the American English it would be en_US, and en_GB for English English (???). I'm just not sure why they're being skipped

Thiswas happened while using feisty, edgy and dapper, but for some reason it didn't annoy me not knowing why it was happening back then :)

---

### Post by synd7 on 2007-07-29
So is this an uncommon problem then? Can anyone even confirm whether this a problem that needs solving?

---

### Post by synd7 on 2007-08-01
bump :D

---

