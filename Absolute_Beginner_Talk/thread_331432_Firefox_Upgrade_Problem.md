---
title: "Firefox Upgrade Problem"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by davesmith on 2007-01-04
hallo
 
I seem to be having  difficulty updating my system with the recent upgrade to Firefox, also the cursor has started jumping around everywhere and making it difficult to type.

This is what I get from the terminal

sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open lock file /var/lib/aptitude/lock - open (2 No such file or directory)
Reading package lists... Done    
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

can anyone help me with this, what is the problem with the lock file and why does my cursor keep jumping around unexpectedly?

---

### Post by davesmith on 2007-01-04
output of <sudo aptitude update> is:

<Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open lock file /var/lib/aptitude/lock - open (2 No such file or directory)
Reading package lists... Done    
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release.gpg [191B]                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Translation-en_US                
Get:4 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US       
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports Release.gpg [191B]            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/main Translation-en_US          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/restricted Translation-en_US    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/universe Translation-en_US      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US         
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release                                   
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release [50.9kB]                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US        
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                 
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                              
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release [50.9kB]                 
Get:11 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                      
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Sources                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/main Packages                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/restricted Packages             
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/universe Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/multiverse Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/main Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/restricted Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/universe Sources                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/multiverse Sources              
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages [39.1kB]          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages                  
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages [39.1kB]           
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                              
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages [3514B]      
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages [17.0kB]       
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages [3514B]     
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                    
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [17.0kB]      
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages [2223B]      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                          
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages [2223B]     
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources [8118B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources [925B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources [1476B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources [14B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [17.0kB]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources [1476B]
99% [25 Packages bzip2 0]                               
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages - open (2 No such file or directory)
99% [26 Sources bzip2 0] 
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_edgy-security_universe_source_Sources - open (2 No such file or directory)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Sources
Fetched 255kB in 4s (56.2kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems>

something is not right here!

---

### Post by taurus on 2007-01-04
Try to run that command again...

```
sudo aptitude update
```

---

### Post by davesmith on 2007-01-04
<sudo aptitude update>

sakara@sakara-laptop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open lock file /var/lib/aptitude/lock - open (2 No such file or directory)
Reading package lists... Done    
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release.gpg [191B]                      
Get:4 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US       
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports Release.gpg [191B]            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/main Translation-en_US          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/restricted Translation-en_US    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/universe Translation-en_US      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US         
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US        
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Packages                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                             
Get:9 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                       
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Sources                          
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/main Packages                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/restricted Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/main Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/restricted Sources   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/universe Sources     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/multiverse Sources   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                    
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Sources
Fetched 11B in 2s (5B/s) 
Reading package lists... Done

---

