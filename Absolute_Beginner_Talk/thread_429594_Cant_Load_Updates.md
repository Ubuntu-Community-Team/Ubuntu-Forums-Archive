---
title: "Cant Load Updates"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by KSZH2K on 2007-05-01
i'm really new to linux/ubuntu 7.04

I loaded feisty without any difficulties and even loaded updates at first but now i get this error each time i try to load updates


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report

I am also confused about the difference between terminal and console? Is there a difference?

I would really appreciate any help I can get.Please remember I am a newbie to linux.

Thanks

---

### Post by taurus on 2007-05-01
Open a terminal and run these commands.

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```
If there is an error message, post the complete error message here.

---

### Post by KSZH2K on 2007-05-01
I did exactly what you asked,heres what happened:



kevin@kevin-desktop:~$ sudo dpkg --configure -a
kevin@kevin-desktop:~$ sudo aptitude update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US
Get:2 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US       
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US           
Get:4 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty Release.gpg [191B]                         
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty/main Translation-en_US                       
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                  
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                  
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                          
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US    
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty Release                                      
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US     
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                 
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                    
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty/main Packages                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources               
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty/main Packages                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Fetched 9B in 1s (8B/s)  
Reading package lists... Done
kevin@kevin-desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  apport apport-gtk libpq5 python-apport python-problem-report rdesktop 
  vmware-player 
7 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
**[COLOR="Red"]Need to get 0B/12.4MB of archives.[/COLOR]** After unpacking 32.1MB will be used.
Do you want to continue? [Y/n/?] 

I then entered y and hit enter: the terminal then had this entered into it:


&#9508;                                                **[COLOR="Red"]Configuring vmware-player [/COLOR]**


 
  DISTRIBUTING VMWARE PLAYER

 If you are interested in distributing VMware   &#9618;  
 &#9474; Player electronically or via internal Web site, CD or other media, or     &#9618;  
 &#9474; are interested in placing an "Includes VMware Player" logo on your        &#9618;  
 &#9474; printed material, please send a request to                                &#9618;  
 &#9474; [email]player_distribution@vmware.com[/email] and we will provide you with a copy of     &#9646;  
 &#9474; our Distribution Agreement for your signature.  The Distribution          &#9618;  
 &#9474; Agreement must be signed by yourself and VMware prior to distributing     &#9618;  
 &#9474; VMware Player or using the "Includes VMware Player" logo.                 &#9618;  
  
 &#9474; LICENSES REQUIRED FOR THIRD-PARTY SOFTWARE The Software allows multiple   &#9618;  
 &#9474; operating systems and applications to run on a single personal computer.  &#9618;  
 &#9474; You are responsible for obtaining any licenses necessary to operate any   &#9618;  
 &#9474; such third-party software.                                                &#8595;  
 &#9474;                                                                              
 &#9474;            
                      <Ok> 

Two things came to mind because the same exact error was again repeated. 

I put the two things I did not understand in bold red. I also left the cofiguring box running because there was nothing else I could do but close it,in which case the errors are not changed.

Thanks in advance for your assistance!




 &#9474;

---

### Post by taurus on 2007-05-01
Are you trying to install vmware-player?

---

### Post by KSZH2K on 2007-05-01
That is one of the updates.

---

