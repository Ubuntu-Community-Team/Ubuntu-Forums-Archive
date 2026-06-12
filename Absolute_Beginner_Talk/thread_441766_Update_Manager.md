---
title: "Update Manager"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by David Ostrom on 2007-05-12
Hello,
I'm having a problem with Update Manager, I keep getting this error message and won't update.
Can someone please explain this?
Thanks,
David

[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

---

### Post by taurus on 2007-05-12
Try

```
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by jtraub on 2007-05-12
[http://ubuntuforums.org/archive/index.php/t-6198.html](http://ubuntuforums.org/archive/index.php/t-6198.html)

---

### Post by David Ostrom on 2007-05-13
This is what I get when I do clean, update, upgrade This is what I get.

root@davids-computer:/home/david# apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                                                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                                                                                       
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US                      
Get:3 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]                               
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                             
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                      
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_US                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release                                                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                                                           
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [10.9kB]                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages                                       
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US                                
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages  
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [10.9kB]
99% [8 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
  Sub-process bzip2 returned an error code (2)
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages [1307kB]    
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages [1307kB]                                                                                           
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                                                                                                   
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                                                                                                        
99% [9 Packages gzip 0] [Waiting for headers]                                                                                                     249kB/s 0s
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                                                                                                       
  Sub-process gzip returned an error code (1)
99% [10 Packages gzip 0] [Waiting for headers]                                                                                                    249kB/s 0s
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                                                                                                       
  Sub-process gzip returned an error code (1)
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                                                                                                    
Fetched 10.9kB in 6s (1715B/s)                                                                                                                              
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@davids-computer:/home/david#

---

### Post by David Ostrom on 2007-05-13
I don't understand!! I can't get update manager to update without this error. What does it mean and how can I go about fixing it? 
Thanks,
David:confused:

---

### Post by David Ostrom on 2007-05-13
BTW I did do sudo aptitude clean, update,
upgrade, and still get the same thing

---

### Post by taurus on 2007-05-13
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by bobplano on 2007-05-13
try posting your sources.list here. from one of the warnings it sounds like you have duplicate lines
EDIT: wow lookslike taurus beat me to it

---

### Post by David Ostrom on 2007-05-13
Did I do this right, is this it?


david@davids-computer:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed main multiverse universe restricted
david@davids-computer:~$

---

### Post by taurus on 2007-05-13
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from your repos.  Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by David Ostrom on 2007-05-13
It's working!! it's working!!\\:D/ I'm doing sudo aptitude update and it's downloading the Packages right now.
I'll let you now more after I do sudo aptitude upgrade.
Thank you,
David

---

### Post by David Ostrom on 2007-05-13
This is the cat /etc/apt/sources.list after doing sudo aptitude upgrade



david@davids-computer:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed main multiverse universe restricted
david@davids-computer:~$ 


I still get this error message from Update Manager

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-) i386/Packages.bz2: Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-) i386/Packages.bz2: Sub-process bzip2 returned an error code (2)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-) i386/Packages.gz: Sub-process gzip returned an error code (1)

---

### Post by David Ostrom on 2007-05-14
Update Manager is still not working. I'm now going back to my reading and study up to figure out what I just did.
Thanks for the replies.
David

---

### Post by n0dl on 2007-05-14
have you tried another mirror? Try switching to japan's or canada's server

---

### Post by David Ostrom on 2007-05-14
Could it have something to do with this? Is there someway to override? I've already done what was suggested but still get the error.


Failed to fetch [http://security.ubuntu.com/ubuntu/di...6/Packages.bz2](http://security.ubuntu.com/ubuntu/di...6/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...86/Packages.gz](http://us.archive.ubuntu.com/ubuntu/...86/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...86/Packages.gz](http://us.archive.ubuntu.com/ubuntu/...86/Packages.gz) Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by David Ostrom on 2007-05-14
have you tried another mirror? Try switching to japan's or canada's server

What is mirror address for Japan and Canada?

David

---

### Post by ronbrooks on 2007-05-15
I can't upgrade either and this is what I get

ronbrooks@prodigy:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                       
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                     
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US             
Get:3 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]           
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US         
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                    
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                    
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US       
Get:6 [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main Release.gpg [191B]                     
Ign [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main/easyubuntu Translation-en_US             
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                        
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                              
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US                
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US         
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US              
Hit [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                              
Hit [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main/easyubuntu Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages [103kB]
99% [10 Packages gzip 0] 
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
  Sub-process gzip returned an error code (1)
Fetched 10B in 4s (2B/s)
Reading package lists... Done

---

### Post by ronbrooks on 2007-05-15
This is the out put of my sources list

ronbrooks@prodigy:~$ cat /etc/apt/sources.list
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
#deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy free non-free
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntu
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by David Ostrom on 2007-05-15
I think the problem lies with the [COLOR="Red"]source.list[/COLOR]. Maybe some one could could come up with an updated version.

---

### Post by taurus on 2007-05-15
> **ronbrooks said:**
> This is the out put of my sources list

ronbrooks@prodigy:~$ cat /etc/apt/sources.list
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
#deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy free non-free
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntu
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

It is NOT a great idea to include 3rd party repos in your /etc/apt/sources.list (like Automatix) when you try to upgrade your machine from one release to the next.  And if you still decide to include them in there, then good luck because it will probably break your system.  ;)

Look at the link in my sig for more info about Automatix & EasyUbuntu.

---

