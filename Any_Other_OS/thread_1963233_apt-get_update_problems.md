---
title: "apt-get update problems"
date: 2012-04-22
forum: Any Other OS
---

### Post by adquinn82 on 2012-04-22
I've recently started using linux mint 12 amd64 and now i get allot of errors when i update. I am also new to Linux so if this is a common and obvious fix i do apologize. Any advise is appreciated.
   
```
HP-Pavilion-dv7-Notebook-PC:~# apt-get update
Ign file: binary/ InRelease
Ign file: binary/ Release.gpg                                                  
Ign file: binary/ Release                                                      
Ign file: binary/ Translation-en_US                                            
Ign file: binary/ Translation-en                                               
Ign [http://quozl.netrek.org](http://quozl.netrek.org) ./ InRelease                                       
Ign [http://quozl.netrek.org](http://quozl.netrek.org) ./ Release.gpg                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security InRelease                         
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa InRelease                               
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid InRelease                               
Ign [http://quozl.netrek.org](http://quozl.netrek.org) ./ Release                                         
Get:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa Release.gpg [197 B]                   
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb InRelease                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa InRelease                                
Ign [http://archive.canonical.com](http://archive.canonical.com) lisa InRelease                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric InRelease                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                                
Get:2 [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa Release [17.7 kB]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates InRelease                        
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security Release.gpg                       
Get:3 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198 B]                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free amd64 Packages                  
Get:4 [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/main Sources [14.3 kB]                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa Release.gpg                              
Ign [http://archive.canonical.com](http://archive.canonical.com) lisa Release.gpg                              
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]          
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg [198 B]                    
Get:7 [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb Release.gpg [836 B]             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Get:8 [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/upstream Sources [10.3 kB]            
Get:9 [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/import Sources [1,190 B]              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free amd64 Packages              
Get:10 [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/backport Sources [20 B]              
Get:11 [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/main amd64 Packages [15.0 kB]        
Get:12 [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/upstream amd64 Packages [28.9 kB]    
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg [198 B]           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security Release                           
Get:14 [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/import amd64 Packages [22.1 kB]      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates Release.gpg                      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Get:15 [http://quozl.netrek.org](http://quozl.netrek.org) ./ Packages [2,201 B]                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free i386 Packages                   
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Get:16 [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/backport amd64 Packages [20 B]       
Get:17 [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/main i386 Packages [15.0 kB]         
Get:18 [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/upstream i386 Packages [28.4 kB]     
Ign [http://archive.canonical.com](http://archive.canonical.com) lisa Release                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release                                  
Get:19 [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/import i386 Packages [22.0 kB]       
Get:20 [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/backport i386 Packages [20 B]        
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/backport TranslationIndex               
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/import TranslationIndex                 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/main TranslationIndex                   
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/upstream TranslationIndex               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free TranslationIndex                
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources/DiffIndex               
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner amd64 Packages/DiffIndex        
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner i386 Packages/DiffIndex         
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner TranslationIndex                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                          
Ign [http://quozl.netrek.org](http://quozl.netrek.org) ./ Translation-en_US                               
Ign [http://archive.canonical.com](http://archive.canonical.com) lisa/partner TranslationIndex                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates Release                          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free TranslationIndex            
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb Release                           
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb Release                           
Ign [http://quozl.netrek.org](http://quozl.netrek.org) ./ Translation-en                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main amd64 Packages/DiffIndex            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted amd64 Packages/DiffIndex      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe amd64 Packages/DiffIndex        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse amd64 Packages/DiffIndex      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages/DiffIndex             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages/DiffIndex       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages/DiffIndex         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages/DiffIndex       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages/DiffIndex      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex              
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages/DiffIndex       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main amd64 Packages/DiffIndex    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages/DiffIndex     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages/DiffIndex 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/main TranslationIndex             
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/apps amd64 Packages/DiffIndex     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/multiverse TranslationIndex       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner amd64 Packages                  
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main amd64 Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/restricted TranslationIndex       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/universe TranslationIndex         
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/games amd64 Packages/DiffIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en                
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/apps i386 Packages/DiffIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main amd64 Packages/DiffIndex  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main amd64 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe amd64 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages         
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/games i386 Packages/DiffIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages         
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/apps TranslationIndex             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted amd64 Packages/DiffIndex
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/games TranslationIndex            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe amd64 Packages/DiffIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en          
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/backport Translation-en_US              
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/backport Translation-en                 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/import Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse amd64 Packages/DiffIndex
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/import Translation-en                   
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/main Translation-en_US                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages/DiffIndex   
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/main Translation-en                     
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/upstream Translation-en_US              
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) lisa/upstream Translation-en                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages/DiffIndex
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/apps amd64 Packages               
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/games amd64 Packages              
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/apps i386 Packages                
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/games i386 Packages               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/main TranslationIndex                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/multiverse TranslationIndex              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/restricted TranslationIndex              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/universe TranslationIndex                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en_US               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en_US                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en_US           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en_US             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/main TranslationIndex            
Err [http://archive.canonical.com](http://archive.canonical.com) lisa/partner amd64 Packages                   
  404  Not Found [IP: 91.189.92.191 80]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main amd64 Packages            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/multiverse TranslationIndex      
Err [http://archive.canonical.com](http://archive.canonical.com) lisa/partner i386 Packages          
  404  Not Found [IP: 91.189.92.191 80]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/restricted TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/universe TranslationIndex
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en_US     
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en        
Ign [http://archive.canonical.com](http://archive.canonical.com) lisa/partner Translation-en_US      
Ign [http://archive.canonical.com](http://archive.canonical.com) lisa/partner Translation-en         
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/apps Translation-en_US            
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en      
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/apps Translation-en               
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/games Translation-en_US           
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/games Translation-en    
Err [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/main Sources
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/restricted Sources
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/universe Sources
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/multiverse Sources
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/main amd64 Packages
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/universe amd64 Packages
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/main i386 Packages
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/restricted i386 Packages
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/universe i386 Packages
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.166 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lisa-security/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/main Sources
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/restricted Sources
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/universe Sources
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/multiverse Sources
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/main amd64 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/restricted amd64 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/universe amd64 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/multiverse amd64 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/main i386 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/restricted i386 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/universe i386 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/main Sources
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/restricted Sources
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/universe Sources
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/multiverse Sources
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/main amd64 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/universe amd64 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/multiverse amd64 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/main i386 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/universe i386 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.170 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lisa-updates/universe Translation-en
Fetched 179 kB in 1min 1s (2,924 B/s)
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb Release: The following signatures were invalid: BADSIG A8A515F046D7E7CF GetDeb Archive Automatic Signing Key <archive@getdeb.net>
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lisa-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/lisa-security/main/source/Sources)  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lisa-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/lisa-security/restricted/source/Sources)  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lisa-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/lisa-security/universe/source/Sources)  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lisa-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/lisa-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lisa-security/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/lisa-security/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lisa-security/restricted/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/lisa-security/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lisa-security/universe/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/lisa-security/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lisa-security/multiverse/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/lisa-security/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lisa-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/lisa-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lisa-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/lisa-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lisa-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/lisa-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lisa-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/lisa-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://archive.canonical.com/dists/lisa/partner/binary-amd64/Packages](http://archive.canonical.com/dists/lisa/partner/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.191 80]

W: Failed to fetch [http://archive.canonical.com/dists/lisa/partner/binary-i386/Packages](http://archive.canonical.com/dists/lisa/partner/binary-i386/Packages)  404  Not Found [IP: 91.189.92.191 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/lisa/main/source/Sources)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/lisa/restricted/source/Sources)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/lisa/universe/source/Sources)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/lisa/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/lisa/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/lisa/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/lisa/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/lisa/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/lisa/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/lisa/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/lisa/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/lisa/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/main/source/Sources)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/restricted/source/Sources)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/universe/source/Sources)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.170 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
HP-Pavilion-dv7-Notebook-PC:~#
```

---

### Post by MG&amp;TL on 2012-04-22
Can you post the output of:

```
cat /etc/apt/sources.list
```I think something's gone a bit wrong if you're trying to fetch "lisa" updates from an ubuntu server...

---

### Post by binson on 2012-04-22
same problem with me dude  :(

---

### Post by adquinn82 on 2012-04-22
```
# deb cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lisa main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lisa main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lisa-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lisa-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lisa universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lisa universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lisa-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lisa-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lisa multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lisa multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lisa-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lisa-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lisa-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lisa-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lisa-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lisa-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lisa-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lisa partner
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lisa-security multiverse
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) lisa main upstream import backport
deb-src [http://packages.linuxmint.com/](http://packages.linuxmint.com/) lisa main upstream import backport #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric partner
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric free non-free

deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb games
deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./
```

---

### Post by JC Cheloven on 2012-04-22
First off, please when posting such large listings use the "code" or "quote" tags (the small icons above the editing area when you edit your post which are a '#' symbol or a text balloon symbol, respectively). Doing so, your listing will appear at a small scrollable area, much more readable.

As for your problem, did it happen for long? It could the servers being down temporarily or so. Anyway you can try
```
sudo dpkg-reconfigure -a
```
(Will take a while)

---

### Post by adquinn82 on 2012-04-22
no change at all:confused:

---

### Post by sanderj on 2012-04-22
[http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/](http://us.archive.ubuntu.com/ubuntu/dists/lisa-updates/) does not exist (anymore?).

Could this have to do with Ubuntu (archives / websites) not supporting Mint stuff anymore? I believe I read something about that.

---

### Post by Perfect Storm on 2012-04-22
Moved to Other OS/Distro Talk.

---

### Post by ronnieredd on 2012-04-26
vers. 10.04
```
W: GPG error: http://archive.canonical.com lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```
The web site is there. The key is not valid.:oops:

---

### Post by eyelessfade on 2012-04-26
> **ronnieredd said:**
> vers. 10.04
```
W: GPG error: http://archive.canonical.com lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```
The web site is there. The key is not valid.:oops:

Same on 12.04. Think the server is having some problems due to the release of precise&#8230; Should be better tomorrow I hope

---

### Post by Shiba on 2012-04-26
I'm having the same problem on Precise and Lucid. Can someone confirm this is Precise related?

EDIT: Ok, I can confirm that this is gone on my installations without me doing anything.

---

### Post by mikolec on 2012-11-15
> **JC Cheloven said:**
> 
```
sudo dpkg-reconfigure -a
```(Will take a while)

it worked for me with simmilar issue... :) thanks!

---

