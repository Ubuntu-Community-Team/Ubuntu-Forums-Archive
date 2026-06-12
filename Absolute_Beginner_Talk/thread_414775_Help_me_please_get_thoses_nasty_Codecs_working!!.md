---
title: "Help me please get thoses nasty Codecs working!!"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by zazen666 on 2007-04-20
Just fresh installed with Xubuntu .

following this guide:


[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)


But not seeming to work:


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
-- INSERT --                                                  1,1           Top



And second step



marshal@marshal-laptop:~$ wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
Password:
OK
marshal@marshal-laptop:~$ sudo apt-get update
Get:1 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/main Translation-en_US                 
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:2 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Get:3 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty Release [57.2kB]
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates Release                       
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/main Packages                          
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/main Sources                           
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/restricted Sources                     
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/universe Sources                       
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/multiverse Sources                     
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/restricted Sources             
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Fetched 57.5kB in 2s (27.1kB/s)
Reading package lists... Done
marshal@marshal-laptop:~$ sudo apt-get install libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
marshal@marshal-laptop:~$ wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
Password:
gpg: Invalid option "-wget"
gpg: no valid OpenPGP data found.
marshal@marshal-laptop:~$ wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
OK
marshal@marshal-laptop:~$ sudo apt-get update
Get:1 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/main Translation-en_US                 
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:2 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty Release        
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates Release                        
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/main Packages                          
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/main Sources                           
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/restricted Sources                     
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/universe Sources                       
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/multiverse Sources                     
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/restricted Sources             
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Fetched 3B in 2s (1B/s)
Reading package lists... Done
marshal@marshal-laptop:~$ sudo apt-get install libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
marshal@marshal-laptop:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
marshal@marshal-laptop:~$

---

### Post by Lieter on 2007-04-20
Use automatics:
[www.getautomatix.com](www.getautomatix.com)

it has a codecs menu :)

---

### Post by xyz on 2007-04-20
This here,too:
[Enabling Multimedia in Feisty (HOW-TO)]("http://ubuntuforums.org/showthread.php?t=413624")

---

### Post by Obor on 2007-04-20
Following this guide will work [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

You are missing the medibuntu repo in your source list, thats why the libdvdcss2 and w32codecs packages are not available

---

