---
title: "duplicate sources.list"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Sonic Reducer on 2008-02-14
every time i **sudo apt-get update** from the command line i get a small error in the last line, but it doesn't seem to have any ill effects. heres a copy/paste from the command line:

```
ryan@ryan-desktop:~$ sudo apt-get update
[sudo] password for ryan:
Ign http://apt.wicd.net gutsy Release.gpg
Ign http://apt.wicd.net gutsy/extras Translation-en_US                         
Hit http://apt.wicd.net gutsy Release                                          
Get:1 http://www.getautomatix.com gutsy Release.gpg [189B]                     
Ign http://www.getautomatix.com gutsy/main Translation-en_US                   
Hit http://apt.wicd.net gutsy/extras Packages                                  
Hit http://www.getautomatix.com gutsy Release                                  
Ign http://ppa.launchpad.net gutsy Release.gpg                                 
Ign http://ppa.launchpad.net gutsy/main Translation-en_US                      
Get:2 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:3 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Ign http://archive.ubuntu.com gutsy/main Translation-en_US                     
Get:4 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_US               
Get:5 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                  
Get:6 http://wine.budgetdedicated.com gutsy Release.gpg [191B]                 
Ign http://wine.budgetdedicated.com gutsy/main Translation-en_US               
Ign http://ppa.launchpad.net gutsy/universe Translation-en_US                  
Hit http://ppa.launchpad.net gutsy Release                                     
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US            
Get:7 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]               
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_US             
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Get:8 http://security.ubuntu.com gutsy-security Release [51.2kB]               
Hit http://archive.ubuntu.com gutsy Release                                    
Hit http://www.getautomatix.com gutsy/main Packages                            
Get:9 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]            
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US    
Hit http://archive.canonical.com gutsy Release                                 
Hit http://wine.budgetdedicated.com gutsy Release                              
Ign http://ppa.launchpad.net gutsy/main Packages                               
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US    
Get:10 http://us.archive.ubuntu.com gutsy-backports Release.gpg [191B]         
Ign http://us.archive.ubuntu.com gutsy-backports/main Translation-en_US        
Hit http://archive.ubuntu.com gutsy-updates Release                            
Ign http://us.archive.ubuntu.com gutsy-backports/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com gutsy-backports/universe Translation-en_US    
Hit http://archive.canonical.com gutsy/partner Packages                        
Ign http://wine.budgetdedicated.com gutsy/main Packages                        
Ign http://ppa.launchpad.net gutsy/universe Packages                           
Ign http://us.archive.ubuntu.com gutsy-backports/restricted Translation-en_US  
Hit http://us.archive.ubuntu.com gutsy Release                                 
Hit http://us.archive.ubuntu.com gutsy-updates Release                         
Hit http://archive.ubuntu.com gutsy/main Packages                              
Hit http://archive.ubuntu.com gutsy/restricted Sources                         
Hit http://archive.ubuntu.com gutsy/main Sources                               
Get:11 http://us.archive.ubuntu.com gutsy-backports Release [44.0kB]           
Hit http://archive.canonical.com gutsy/partner Sources                         
Hit http://wine.budgetdedicated.com gutsy/main Sources                         
Hit http://ppa.launchpad.net gutsy/main Packages                               
Hit http://archive.ubuntu.com gutsy-updates/main Packages                      
Hit http://archive.ubuntu.com gutsy-updates/main Sources                       
Hit http://wine.budgetdedicated.com gutsy/main Packages                        
Hit http://ppa.launchpad.net gutsy/universe Packages                           
Get:12 http://security.ubuntu.com gutsy-security/main Packages [70.0kB]        
Hit http://us.archive.ubuntu.com gutsy/main Packages  
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources     
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy/universe Sources 
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Get:13 http://us.archive.ubuntu.com gutsy-backports/main Packages [27.1kB]
Get:14 http://security.ubuntu.com gutsy-security/multiverse Packages [2903B]
Get:15 http://security.ubuntu.com gutsy-security/universe Packages [42.1kB]
Get:16 http://us.archive.ubuntu.com gutsy-backports/multiverse Packages [6660B]
Get:17 http://us.archive.ubuntu.com gutsy-backports/universe Packages [80.9kB]
Get:18 http://security.ubuntu.com gutsy-security/restricted Packages [14B]     
Get:19 http://security.ubuntu.com gutsy-security/main Sources [12.3kB]
Get:20 http://security.ubuntu.com gutsy-security/multiverse Sources [833B]     
Get:21 http://security.ubuntu.com gutsy-security/universe Sources [5912B]      
Get:22 http://security.ubuntu.com gutsy-security/restricted Sources [14B]      
Get:23 http://us.archive.ubuntu.com gutsy-backports/restricted Packages [14B]  
Get:24 http://us.archive.ubuntu.com gutsy-backports/main Sources [7608B]
Get:25 http://us.archive.ubuntu.com gutsy-backports/multiverse Sources [2264B]
Get:26 http://us.archive.ubuntu.com gutsy-backports/universe Sources [17.3kB]
Get:27 http://us.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Fetched 372kB in 2s (142kB/s)                  
Reading package lists... Done
W: Duplicate sources.list entry http://security.ubuntu.com gutsy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

what is causing this error?

---

### Post by spiderbatdad on 2008-02-14
take a look at your sources.list. It's located in the file system /etc/apt/sources.list
looks like this source: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_main_binary-i386_Packages)

appear twice. Probably added by automatix. I haven't heard good things about automatix. You can edit the sources.list with ```
gksu gedit /etc/apt/sources.list
``` and delete the double entry. Then save the file.

---

### Post by emarkd on 2008-02-14
This line:

```
http://security.ubuntu.com gutsy-security/main
```

apparently appears twice in your /etc/apt/sources.list file.  You can edit the file and remove one of them to make the message go away.

---

