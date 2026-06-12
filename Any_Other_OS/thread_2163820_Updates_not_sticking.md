---
title: "Updates not sticking"
date: 2013-07-19
forum: Any Other OS
---

### Post by Buntu Bunny on 2013-07-19
About two months ago I installed Voyager 12.04 on my old Dell Inspiron 700m. I don't have WiFi at home, so it only goes online every couple of weeks when I can get to free WiFi to update it. There have been no problems in the past, but about 10 days ago I noticed that Update Manager informed me that my last update was 48 days prior. I knew it had only been a few weeks and Update Manager had trouble getting online. It finally seemed to and the updates were made. 

This afternoon I took this laptop to the library to update; this time Update Manager said it had been 57 days, which basically was about how long ago since I installed it. After it updated the cache, it told me to check my internet connection. Firefox was online, so I knew I had a connection. 

When I ran apt-get update I got this.

```
sudo apt-get update
Hit http://us.archive.ubuntu.com precise Release.gpg
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://packages.medibuntu.org precise Release.gpg                          
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise Release                               
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://us.archive.ubuntu.com precise-updates Release                       
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise-backports Release                     
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://packages.medibuntu.org precise Release                              
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://ppa.launchpad.net precise Release.gpg                               
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:3 http://security.ubuntu.com precise-security/main Sources [83.6 kB]       
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Get:4 http://security.ubuntu.com precise-security/restricted Sources [2,494 B] 
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://security.ubuntu.com precise-security/universe Sources               
Hit http://us.archive.ubuntu.com precise-updates/main Sources                  
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources            
Hit http://security.ubuntu.com precise-security/multiverse Sources             
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise-updates/universe Sources              
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources            
Hit http://security.ubuntu.com precise-security/main i386 Packages             
Ign http://ppa.launchpad.net precise Release.gpg                               
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Hit http://ppa.launchpad.net precise Release                                   
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Hit http://security.ubuntu.com precise-security/universe i386 Packages         
Hit http://ppa.launchpad.net precise Release                                   
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages            
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages      
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://ppa.launchpad.net precise Release                          
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Ign http://ppa.launchpad.net precise Release                          
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://us.archive.ubuntu.com precise/main Translation-en          
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en    
Hit http://ppa.launchpad.net precise/main i386 Packages               
Hit http://us.archive.ubuntu.com precise/restricted Translation-en    
Hit http://us.archive.ubuntu.com precise/universe Translation-en      
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en  
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://ppa.launchpad.net precise/main i386 Packages               
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Hit http://ppa.launchpad.net precise/main i386 Packages               
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Ign http://packages.medibuntu.org precise/free Translation-en_US
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://packages.medibuntu.org precise/free Translation-en
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://packages.medibuntu.org precise/non-free Translation-en_US
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://packages.medibuntu.org precise/non-free Translation-en
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex                    
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex              
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Err http://ppa.launchpad.net precise/main Sources
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Fetched 136 kB in 25s (5,274 B/s)
W: Failed to fetch http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

The other curious thing is that Firefox doesn't remember my bookmarks.

I did not do anything fancy when I installed it, just a clean basic install. I have not messed with any directories, nor installed anything other than what came on the Live CD. Yet, something appears to be broken. Does anyone have an idea what and how to fix it?

---

### Post by deadflowr on 2013-07-19
You need to disable or remove the yannubuntu PPAs.
I don't know how the software sources are set up in Voyager,
but if like Ubuntu, you just go to software sources and then other software tab.
Then uncheck the repo for the yannubuntu PPA(s).[password required]
Then run update again.

---

### Post by QIII on 2013-07-19
YannBuntu may not be maintaining that PPA for 12.04 or might have moved it.  yannubuntu is his/her account name on Launchpad.  You might check there... or catch him/her on the Forum.

---

### Post by Buntu Bunny on 2013-07-19
> **deadflowr said:**
> You need to disable or remove the yannubuntu PPAs.
I don't know how the software sources are set up in Voyager,
but if like Ubuntu, you just go to software sources and then other software tab.
Then uncheck the repo for the yannubuntu PPA(s).[password required]
Then run update again.

Deadflowr, thank you! Voyager is just a bells & whistles version of Xubuntu, so I found it easily and removed it. It will be a day or two before I can get to the library to run another update, but I'll report back on that. 

> **QIII said:**
> YannBuntu may not be maintaining that PPA for 12.04 or might have moved it.  yannubuntu is his/her account name on Launchpad.  You might check there... or catch him/her on the Forum.

QIII, I did check Launchpad and saw that the development PPA for OS-Uninstaller has no updates. Hopefully removing it will solve my problem.

Many thanks to you both.

---

### Post by Buntu Bunny on 2013-07-20
OK, success, I think. I got to the library and booted up. Update manager had no complaints about getting online and updated the cache easily. Then it told me the system was up to date and that there were no updates to install. I went to terminal to apt-get update and apt-get dist-upgrade and was informed that there were no updates. Interesting.

So, what I have learned is that if I have a similar problem again, to run apt-get update and check for 

```
W: Failed to fetch
``` 

In this case ppa.launchpad.net/yannubuntu/os-uninstaller. Then I need to remove or disable it and try again. Is that correct?

I had researched this prior to asking here at the Forums, and have to say that the answers others were getting  in other places were confusing. You guys solved my problem simply and with no confusion. Thank you again deadflowr and QIII.

Oh, and I almost forgot to mention, my Firefox links are back. :P

---

