---
title: "Update Manager"
date: 2012-01-16
forum: Any Other OS
---

### Post by UltimateCat on 2012-01-16
At the moment my Update Manager is holding a very long list of security updates.

A window opened and gave me a Warning  some of the packages are "not authenticate" so.... I am.....:confused:

How come there are so many ( 823.8 MB)  updates? 

How do I know which security update to allow Update Manager to install?

Any advise is appreciated because I don't understand.

Thanks in advance

---

### Post by oldos2er on 2012-01-17
Can you run ```
sudo apt-get update
``` in a terminal, and post the output here?

---

### Post by UltimateCat on 2012-01-18
Oldos2er:
Here's the output from the command you asked me for.
Sure is long-


```
cat@ztcat:~$ sudo apt-get update
[sudo] password for cat: 
Get:1 http://downloadue.info lucid Release.gpg
Ign http://downloadue.info/repo/ lucid/all Translation-en_US                   
Hit http://packages.medibuntu.org karmic Release.gpg                           
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Hit http://packages.enlightenment.org karmic Release.gpg                       
Ign http://downloadue.info lucid Release                                       
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/akirad/akirad/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Get:2 http://deb.playonlinux.com lucid Release.gpg [197B]                      
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Ign http://downloadue.info lucid/all Packages                                  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-backports Release.gpg                   
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://ppa.launchpad.net/akirad/ppa/ubuntu/ lucid/main Translation-en_US   
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/compiz/ubuntu/ lucid/main Translation-en_US       
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/falk-t-j/games/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net/bogdanb/ppa/ubuntu/ karmic/main Translation-en_US 
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://packages.medibuntu.org/ karmic/free Translation-en_US               
Ign http://downloadue.info lucid/all Packages                                  
Hit http://archive.canonical.com lucid Release                                 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-proposed Release.gpg                    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US 
Ign http://packages.enlightenment.org/ubuntu/ karmic/main Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
Ign http://deb.playonlinux.com/ lucid/main Translation-en_US                   
Hit http://downloadue.info lucid/all Packages                                  
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net/team-xbmc/karmic-ppa/ubuntu/ karmic/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://us.archive.ubuntu.com lucid Release                                 
Hit http://us.archive.ubuntu.com lucid-updates Release                         
Hit http://us.archive.ubuntu.com lucid-backports Release                       
Hit http://us.archive.ubuntu.com lucid-proposed Release                        
Get:3 http://deb.playonlinux.com lucid Release [1,722B]                        
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net karmic Release                                    
Ign http://packages.medibuntu.org/ karmic/non-free Translation-en_US           
Err http://deb.playonlinux.com lucid Release                                   
  
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/main Sources                     
Hit http://security.ubuntu.com lucid-security/restricted Sources               
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://security.ubuntu.com lucid-security/universe Sources                 
Hit http://security.ubuntu.com lucid-security/multiverse Packages              
Ign http://packages.enlightenment.org/ubuntu/ karmic/extras Translation-en_US  
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Hit http://ppa.launchpad.net lucid Release                                     
Ign http://ppa.launchpad.net karmic Release                                    
Hit http://security.ubuntu.com lucid-security/multiverse Sources               
Hit http://us.archive.ubuntu.com lucid/restricted Packages                     
Hit http://us.archive.ubuntu.com lucid/main Sources                            
Hit http://us.archive.ubuntu.com lucid/restricted Sources                      
Hit http://us.archive.ubuntu.com lucid/universe Packages                       
Hit http://us.archive.ubuntu.com lucid/universe Sources                        
Hit http://us.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://us.archive.ubuntu.com lucid/multiverse Sources                      
Hit http://us.archive.ubuntu.com lucid-updates/main Packages                   
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages             
Hit http://us.archive.ubuntu.com lucid-updates/main Sources                    
Hit http://packages.medibuntu.org karmic Release                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://packages.enlightenment.org karmic Release                           
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources              
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages               
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources                
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages             
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources              
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://us.archive.ubuntu.com lucid-backports/main Packages                 
Hit http://us.archive.ubuntu.com lucid-backports/restricted Packages           
Hit http://us.archive.ubuntu.com lucid-backports/universe Packages             
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Packages           
Hit http://us.archive.ubuntu.com lucid-backports/main Sources                  
Hit http://packages.medibuntu.org karmic/free Packages                         
Ign http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net lucid/main Packages                               
Ign http://packages.enlightenment.org karmic/main Packages                     
Hit http://us.archive.ubuntu.com lucid-backports/restricted Sources            
Hit http://us.archive.ubuntu.com lucid-backports/universe Sources              
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com lucid-proposed/restricted Packages            
Hit http://us.archive.ubuntu.com lucid-proposed/main Packages                  
Ign http://ppa.launchpad.net karmic/main Packages                              
Hit http://us.archive.ubuntu.com lucid-proposed/multiverse Packages            
Hit http://us.archive.ubuntu.com lucid-proposed/universe Packages              
Hit http://packages.medibuntu.org karmic/non-free Packages                     
Err http://ppa.launchpad.net karmic/main Packages                              
  404  Not Found
Ign http://packages.enlightenment.org karmic/extras Packages         
Ign http://packages.enlightenment.org karmic/main Packages
Ign http://packages.enlightenment.org karmic/extras Packages
Hit http://packages.enlightenment.org karmic/main Packages
Hit http://packages.enlightenment.org karmic/extras Packages
Ign http://www.openprinting.

```

Hope this doesn't mean something could be wrong-

---

### Post by bluexrider on 2012-01-18
Why would you still have Karmic sources listed

---

### Post by raja.genupula on 2012-01-18
open your update manager settings and then at other software TAB uncheck those error canonical PPA's and update again.

---

### Post by KRISHNASHK on 2012-01-18
check out the third party applications ,try to unselect them , the rest of the update will probably be the important fixes.

---

### Post by Frogs Hair on 2012-01-18
The Enlightenment and other 9.10 packages / sources  may be the problem . If want to run E. remove Karmic packages find a PPA or packages that are 10.04 compatible . As stated if you remove the 9.10 sources the update may succeed .

---

### Post by UltimateCat on 2012-01-18
I have Ultimate Edition, sorry, I forgot to say-

I am not sure why I have Karmic sources listed.

I will try like you said Raja.genupula:

and open the update Mgr setting and TAB those error canonical PPA's
(Still learning about Update MGR this is my first time using it
I have only been online for about 2 weeks.

---

### Post by UltimateCat on 2012-01-18
> **KRISHNASHK said:**
> check out the third party applications ,try to unselect them , the rest of the update will probably be the important fixes.

I will try to unselect them and see what happens. 
Thank You

---

### Post by UltimateCat on 2012-01-19
> **bluexrider said:**
> Why would you still have Karmic sources listed
I think I still have the Karmic sources because I have Ultimate Edition 2.7.
I ( think) because 10.04 came from 9.10 sources that's why. Truthfully I am :confused:

A friend of mine made a pearl script that detects and fixes any launchpad PPA's link in 
/etc/apt/sources.list

And backs up the orginal :
/etc/apt/sources.list as..../etc/apt/apt/sources.list.backup
Also imports GPG key for the links detected.

It is suppose to solve gpg key errors ( which *I had one)* in Ultimate Edition.


I'm wondering what you think as you have more experience with Ubuntu than I do.

---

### Post by oldos2er on 2012-01-19
Moved to Other OS/Distro Talk.

Ubuntu Ultimate forums are here: [http://forumubuntusoftware.info/](http://forumubuntusoftware.info/)
I think you should seek an answer there as to whether your sources.list is problematic or not.

---

