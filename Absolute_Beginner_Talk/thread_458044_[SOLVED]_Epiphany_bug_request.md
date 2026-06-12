---
title: "[SOLVED] Epiphany bug request"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-05-29
Not sure what I need to do here!

I have a bug reported re epiphany not starting - and have been asked to do the following


Thanks for your bug report. Could you installed libgtk2.0-0-dbg epiphany-browser-dbgsym firefox-dbg ([https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)) and get a new backtrace?

I've been to the website and followed the instructions then tried to run 

```
libgtk2.0-0-dbg epiphany-browser-dbgsym firefox-dbg
``` it doesn't work I get

```
bash: libgtk2.0-0-dbg: command not found
```

I added repo to the sources.list and did wget as it shows in the web page

```
kevin@kevin-desktop:~$ sudo gedit /etc/apt/sources.list
Password:
kevin@kevin-desktop:~$ wget -q "http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x0DE7276D5E0577F2" -O- | sudo apt-key add -
OK
kevin@kevin-desktop:~$ sudo apt-get update
Get: 1 http://wine.budgetdedicated.com feisty Release.gpg [191B]
Ign http://wine.budgetdedicated.com feisty/main Translation-en_GB
Get: 2 http://archive.canonical.com feisty-commercial Release.gpg [191B]       
Ign http://archive.canonical.com feisty-commercial/main Translation-en_GB      
Hit http://wine.budgetdedicated.com feisty Release                             
Ign http://people.ubuntu.com feisty Release.gpg                                
Ign http://people.ubuntu.com feisty/main Translation-en_GB                     
Get: 3 http://gb.archive.ubuntu.com feisty Release.gpg [191B]                  
Get: 4 http://gb.archive.ubuntu.com feisty/main Translation-en_GB [4827B]      
Hit http://archive.canonical.com feisty-commercial Release                     
Get: 5 http://security.ubuntu.com feisty-security Release.gpg [191B]           
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_GB    
Ign http://people.ubuntu.com feisty/universe Translation-en_GB                 
Get: 6 http://archive.ubuntu.com feisty-updates Release.gpg [191B]             
Ign http://archive.ubuntu.com feisty-updates/restricted Translation-en_GB      
Ign http://people.ubuntu.com feisty Release                                    
Ign http://gb.archive.ubuntu.com feisty/restricted Translation-en_GB           
Hit http://archive.canonical.com feisty-commercial/main Packages               
Ign http://security.ubuntu.com feisty-security/main Translation-en_GB          
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_GB    
Ign http://security.ubuntu.com feisty-security/universe Translation-en_GB      
Ign http://wine.budgetdedicated.com feisty/main Packages                       
Ign http://archive.ubuntu.com feisty-updates/main Translation-en_GB            
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_GB      
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_GB        
Ign http://gb.archive.ubuntu.com feisty/universe Translation-en_GB             
Get: 7 http://gb.archive.ubuntu.com feisty/multiverse Translation-en_GB [1573B]
Ign http://people.ubuntu.com feisty/main Packages                              
Get: 8 http://gb.archive.ubuntu.com feisty-updates Release.gpg [191B]          
Ign http://gb.archive.ubuntu.com feisty-updates/main Translation-en_GB         
Ign http://gb.archive.ubuntu.com feisty-updates/restricted Translation-en_GB   
Hit http://security.ubuntu.com feisty-security Release                         
Get: 9 http://gb.archive.ubuntu.com feisty-security Release.gpg [191B]         
Ign http://gb.archive.ubuntu.com feisty-security/main Translation-en_GB        
Ign http://gb.archive.ubuntu.com feisty-security/restricted Translation-en_GB  
Ign http://gb.archive.ubuntu.com feisty-security/universe Translation-en_GB    
Get: 10 http://gb.archive.ubuntu.com feisty-backports Release.gpg [191B]       
Ign http://gb.archive.ubuntu.com feisty-backports/main Translation-en_GB       
Hit http://archive.ubuntu.com feisty-updates Release                           
Ign http://people.ubuntu.com feisty/universe Packages                          
Hit http://wine.budgetdedicated.com feisty/main Sources                        
Ign http://gb.archive.ubuntu.com feisty-backports/restricted Translation-en_GB 
Ign http://gb.archive.ubuntu.com feisty-backports/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty-backports/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com feisty Release                     
Get: 11 http://people.ubuntu.com feisty/main Packages [423kB]                  
Hit http://wine.budgetdedicated.com feisty/main Packages                       
Hit http://gb.archive.ubuntu.com feisty-updates Release                        
Hit http://gb.archive.ubuntu.com feisty-security Release                       
Hit http://gb.archive.ubuntu.com feisty-backports Release                      
Hit http://security.ubuntu.com feisty-security/restricted Packages             
Hit http://archive.ubuntu.com feisty-updates/restricted Packages               
Get: 12 http://archive.ubuntustudio.org feisty Release.gpg [189B]              
Ign http://archive.ubuntustudio.org feisty/main Translation-en_GB              
Hit http://security.ubuntu.com feisty-security/main Packages                   
Hit http://security.ubuntu.com feisty-security/multiverse Packages             
Hit http://security.ubuntu.com feisty-security/universe Packages               
Hit http://archive.ubuntu.com feisty-updates/main Packages                     
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages               
Hit http://archive.ubuntu.com feisty-updates/universe Packages                 
Hit http://gb.archive.ubuntu.com feisty/main Packages                          
Hit http://security.ubuntu.com feisty-security/restricted Sources              
Hit http://security.ubuntu.com feisty-security/main Sources                    
Hit http://security.ubuntu.com feisty-security/multiverse Sources              
Hit http://security.ubuntu.com feisty-security/universe Sources                
Hit http://gb.archive.ubuntu.com feisty/restricted Packages                    
Hit http://gb.archive.ubuntu.com feisty/restricted Sources                   
Hit http://gb.archive.ubuntu.com feisty/main Sources                         
Hit http://gb.archive.ubuntu.com feisty/multiverse Sources                   
Hit http://gb.archive.ubuntu.com feisty/universe Sources                     
Hit http://gb.archive.ubuntu.com feisty/universe Packages                    
Hit http://gb.archive.ubuntu.com feisty/multiverse Packages                  
Hit http://archive.ubuntustudio.org feisty Release                           
Hit http://gb.archive.ubuntu.com feisty-updates/main Packages                
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://gb.archive.ubuntu.com feisty-updates/main Sources
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Sources           
Hit http://gb.archive.ubuntu.com feisty-security/main Packages               
Hit http://gb.archive.ubuntu.com feisty-security/restricted Packages         
Hit http://gb.archive.ubuntu.com feisty-security/restricted Sources          
Hit http://gb.archive.ubuntu.com feisty-security/main Sources                 
Hit http://gb.archive.ubuntu.com feisty-security/universe Sources             
Hit http://gb.archive.ubuntu.com feisty-security/universe Packages            
Hit http://archive.ubuntustudio.org feisty/main Packages                      
Hit http://gb.archive.ubuntu.com feisty-backports/main Packages               
Hit http://gb.archive.ubuntu.com feisty-backports/restricted Packages
Hit http://gb.archive.ubuntu.com feisty-backports/universe Packages
Hit http://gb.archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://gb.archive.ubuntu.com feisty-backports/main Sources
Hit http://gb.archive.ubuntu.com feisty-backports/restricted Sources
Hit http://gb.archive.ubuntu.com feisty-backports/universe Sources
Hit http://gb.archive.ubuntu.com feisty-backports/multiverse Sources
Get: 13 http://people.ubuntu.com feisty/universe Packages [1129kB]
Fetched 1558kB in 7s (196kB/s)                                                 
Reading package lists... Done
kevin@kevin-desktop:~$ sudo apt-get install yelp-dbgsym
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  yelp-dbgsym
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 299kB of archives.
After unpacking 721kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  yelp-dbgsym
Install these packages without verification [y/N]? y
Get: 1 http://people.ubuntu.com feisty/main yelp-dbgsym 2.18.1-0ubuntu2 [299kB]
Fetched 299kB in 1s (211kB/s)       
Selecting previously deselected package yelp-dbgsym.
(Reading database ... 140048 files and directories currently installed.)
Unpacking yelp-dbgsym (from .../yelp-dbgsym_2.18.1-0ubuntu2_i386.ddeb) ...
Setting up yelp-dbgsym (2.18.1-0ubuntu2) ...
kevin@kevin-desktop:~$ libgtk2.0-0-dbg epiphany-browser-dbgsym firefox-dbg
bash: libgtk2.0-0-dbg: command not found
kevin@kevin-desktop:~$ 

```

installed libgtk2.0-0-dbg

but still no joy

---

### Post by lreyes6 on 2007-05-29
> **forestpixie said:**
> 
i'm assuming you want to install this packages.... 

```
libgtk2.0-0-dbg epiphany-browser-dbgsym firefox-dbg
``` it doesn't work I get




if you want to install them you have to do this

```
sudo aptitude install libgtk2.0-0-dbg epiphany-browser-dbgsym firefox-dbg
```

or you can try to search it from synaptics

hope this helps

---

### Post by forestpixie on 2007-05-29
Didn't realise the whole was an install request, doing it now then do I just run the whole 

ibgtk2.0-0-dbg epiphany-browser-dbgsym firefox-dbg

in terminal?

---

### Post by forestpixie on 2007-05-29
ok installed it, ran it

but
bash: ibgtk2.0-0-dbg: command not found

?

All means nothing to me!

---

### Post by forestpixie on 2007-05-29
S'ok - I got it now.

Thanks

---

