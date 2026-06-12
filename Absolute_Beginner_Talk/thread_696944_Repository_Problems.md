---
title: "Repository Problems"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by mindalchemist on 2008-02-14
I for some reason keep having problems with my repository index.  I have changed servers and I still get this:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://www.gtlib.gatech.edu/pub/ubuntu/dists/gutsy/Release:](http://www.gtlib.gatech.edu/pub/ubuntu/dists/gutsy/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://www.gtlib.gatech.edu/pub/ubuntu/dists/gutsy-updates/Release:](http://www.gtlib.gatech.edu/pub/ubuntu/dists/gutsy-updates/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://www.gtlib.gatech.edu/pub/ubuntu/dists/gutsy-security/Release:](http://www.gtlib.gatech.edu/pub/ubuntu/dists/gutsy-security/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://www.gtlib.gatech.edu/pub/ubuntu/dists/gutsy-proposed/Release:](http://www.gtlib.gatech.edu/pub/ubuntu/dists/gutsy-proposed/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

What can I do?

---

### Post by jan quark on 2008-02-14
change to main server, if you haven't already

---

### Post by mindalchemist on 2008-02-14
I tried, same thing.  Went to the UK, went to another country, and then GA Tech.  Still nothing.  I checked and they all seem to be EN-US Translation files.

---

### Post by jan quark on 2008-02-14
i get an ignored
when doing sudo apt-get update

but you know what, I think it is not that crucial and important
isn't it?


```
 Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US
Get:2 http://de.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://de.archive.ubuntu.com gutsy/main Translation-en_US
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release
Ign http://de.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://de.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://de.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:3 http://de.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://de.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://de.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://de.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://de.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://de.archive.ubuntu.com gutsy Release
Get:4 http://de.archive.ubuntu.com gutsy-updates Release [58.5kB]   
Hit http://security.ubuntu.com gutsy-security/main Packages
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://de.archive.ubuntu.com gutsy/main Packages
Hit http://de.archive.ubuntu.com gutsy/restricted Packages
Hit http://de.archive.ubuntu.com gutsy/main Sources
Hit http://de.archive.ubuntu.com gutsy/restricted Sources
Hit http://de.archive.ubuntu.com gutsy/universe Packages
Hit http://de.archive.ubuntu.com gutsy/universe Sources
Hit http://de.archive.ubuntu.com gutsy/multiverse Packages
Hit http://de.archive.ubuntu.com gutsy/multiverse Sources
Get:5 http://de.archive.ubuntu.com gutsy-updates/main Packages [160kB]
Get:6 http://de.archive.ubuntu.com gutsy-updates/restricted Packages [4263B]
Get:7 http://de.archive.ubuntu.com gutsy-updates/main Sources [34.7kB]
Get:8 http://de.archive.ubuntu.com gutsy-updates/restricted Sources [937B]
Get:9 http://de.archive.ubuntu.com gutsy-updates/universe Packages [67.1kB]
Get:10 http://de.archive.ubuntu.com gutsy-updates/universe Sources [10.3kB]
Get:11 http://de.archive.ubuntu.com gutsy-updates/multiverse Packages [9942B]
Get:12 http://de.archive.ubuntu.com gutsy-updates/multiverse Sources [1883B]
Fetched 348kB in 2s (134kB/s)                           
Reading package lists... Done
```

---

### Post by Rocket2DMn on 2008-02-14
Can you please post your sources.list file?
```
cat /etc/apt/sources.list
```

---

### Post by mindalchemist on 2008-02-14
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) gutsy main restricted web
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) gutsy restricted main multiverse web universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) gutsy-updates restricted main multiverse universe web
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) gutsy-updates restricted main multiverse universe web #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) gutsy-security main restricted web
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) gutsy-security restricted main multiverse web universe #Added by software-properties
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) gutsy-security universe
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) gutsy-proposed restricted main multiverse universe web
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) gutsy-proposed restricted main multiverse universe web
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) gutsy-backports restricted main multiverse universe web
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) gutsy-backports restricted main multiverse universe web
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) gutsy-security multiverse

---

### Post by Rocket2DMn on 2008-02-14
I don't think you are supposed to have "web" anywhere in the sources.list file.  Try removing them and running update.
```
sudo cp /etc/apt/sources.list etc/apt/sources.list.backup
gksudo gedit etc/apt/sources.list
```
Remove the "web" portions (not the whole line, just that phrase), then update:
```
sudo apt-get update
```

---

### Post by mindalchemist on 2008-02-14
This is what I got:

Get:1 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy Release.gpg [191B]
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy/main Translation-en_US      
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy/restricted Translation-en_US
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy/web Translation-en_US
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy/universe Translation-en_US
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy/multiverse Translation-en_US
Get:2 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-updates Release.gpg [191B]
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-updates/restricted Translation-en_US
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-updates/main Translation-en_US
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-updates/multiverse Translation-en_US
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-updates/universe Translation-en_US
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-updates/web Translation-en_US
Get:3 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-security Release.gpg [191B]
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-security/main Translation-en_US
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-security/restricted Translation-en_US
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-security/universe Translation-en_US
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-security/multiverse Translation-en_US
Get:4 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-proposed Release.gpg [191B]
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-proposed/restricted Translation-en_US
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-proposed/main Translation-en_US
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-proposed/multiverse Translation-en_US
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-proposed/universe Translation-en_US
Get:5 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-backports Release.gpg [191B]
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-backports/restricted Translation-en_US
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-backports/main Translation-en_US
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-backports/multiverse Translation-en_US
Ign [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-backports/universe Translation-en_US
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy Release                  
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-updates Release                          
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-security Release                         
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-proposed Release                         
Get:6 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-backports Release [44.0kB]             
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy/main Packages                            
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy/restricted Packages      
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-updates/restricted Packages              
Get:7 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-updates/main Packages [160kB]          
Get:8 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-updates/multiverse Packages [9942B]
Get:9 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-updates/universe Packages [67.1kB]     
Get:10 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-security/main Packages [70.0kB]       
Get:11 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-security/restricted Packages [14B]    
Get:12 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-security/restricted Sources [14B]
Get:13 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-security/main Sources [12.3kB]
Get:14 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-security/multiverse Sources [833B]    
Get:15 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-security/universe Sources [5912B]     
Get:16 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-security/universe Packages [42.1kB]   
Get:17 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-security/multiverse Packages [2903B]  
Get:18 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-proposed/restricted Packages [14B]    
Get:19 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-proposed/main Packages [104kB]        
Get:20 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-proposed/multiverse Packages [14B]    
Get:21 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-proposed/universe Packages [4992B]
Get:22 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-proposed/restricted Sources [14B]
Get:23 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-proposed/main Sources [45.4kB]        
Get:24 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-proposed/multiverse Sources [14B]     
Get:25 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-proposed/universe Sources [1464B]     
Get:26 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-backports/restricted Packages [14B]   
Get:27 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-backports/main Packages [27.1kB]      
Get:28 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-backports/multiverse Packages [6660B] 
Get:29 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-backports/universe Packages [80.9kB]  
Get:30 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-backports/restricted Sources [14B]    
Get:31 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-backports/main Sources [7608B]        
Get:32 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-backports/multiverse Sources [2264B]  
Get:33 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) gutsy-backports/universe Sources [17.3kB]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release.gpg [191B]    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Sources           
Fetched 715kB in 6s (107kB/s)                                                  
Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/Release](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/Release](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Rocket2DMn on 2008-02-14
Ah, you also need to comment out the Feisty repositories since you're running Gutsy, that can create problems.  
Is ubuntu.media.mit.edu a 3rd party repo or is that just a mirror for updates?  You can try the main mirror.  It's possible their sync is completely up to date, or some of their server is not available.  Comment out the Feisty stuff with # at the beginning of the line (or replace "feisty" with "gutsy" if the respective mirror supports it) and run update.  If you still get errors, you may just need to wait awhile for the mirror to fix itself.

---

