---
title: "Upgrade problems"
date: 2011-07-23
forum: Any Other OS
---

### Post by MossMethod on 2011-07-23
Yo! I got a problem you guys. I keep get this failed to fetch error and I can not figure out why? I am running Linux Mint 11, Gnome 3 (figured mint is somewhat based on Ubuntu so it would be okay to ask here).

>  sudo apt-get update
[sudo] password for user: 
Ign file: binary/ InRelease
Ign file: binary/ Release.gpg                                                  
Ign file: binary/ Release                                                      
Ign file: binary/ Translation-en_US                                            
Ign file: binary/ Translation-en                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy InRelease                                
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg                              
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release.gpg                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Ign [http://ftp.cc.uoc.gr](http://ftp.cc.uoc.gr) katya InRelease                                       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy InRelease                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free i386 Packages                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe TranslationIndex                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main i386 Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe i386 Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse i386 Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main TranslationIndex                      
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release                               
Hit [http://ftp.cc.uoc.gr](http://ftp.cc.uoc.gr) katya Release.gpg                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse TranslationIndex                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted TranslationIndex                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe TranslationIndex                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe i386 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse i386 Packages           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free i386 Packages                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main TranslationIndex              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse TranslationIndex        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted TranslationIndex        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe TranslationIndex          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main TranslationIndex                 
Hit [http://ftp.cc.uoc.gr](http://ftp.cc.uoc.gr) katya Release                                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free TranslationIndex                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free TranslationIndex              
Hit [http://ftp.cc.uoc.gr](http://ftp.cc.uoc.gr) katya/main i386 Packages                              
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe i386 Packages                   
  404  Not Found [IP: 91.189.88.30 80]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Hit [http://ftp.cc.uoc.gr](http://ftp.cc.uoc.gr) katya/upstream i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Hit [http://ftp.cc.uoc.gr](http://ftp.cc.uoc.gr) katya/import i386 Packages                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://ftp.cc.uoc.gr](http://ftp.cc.uoc.gr) katya/import TranslationIndex                         
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main i386 Packages                    
  404  Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Translation-en                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Translation-en          
Ign [http://ftp.cc.uoc.gr](http://ftp.cc.uoc.gr) katya/main TranslationIndex                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en_US         
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_US                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en            
Ign [http://ftp.cc.uoc.gr](http://ftp.cc.uoc.gr) katya/upstream TranslationIndex             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en_US                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en_US             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en                
Ign [http://ftp.cc.uoc.gr](http://ftp.cc.uoc.gr) katya/import Translation-en_US                        
Ign [http://ftp.cc.uoc.gr](http://ftp.cc.uoc.gr) katya/import Translation-en
Ign [http://ftp.cc.uoc.gr](http://ftp.cc.uoc.gr) katya/main Translation-en_US
Ign [http://ftp.cc.uoc.gr](http://ftp.cc.uoc.gr) katya/main Translation-en
Ign [http://ftp.cc.uoc.gr](http://ftp.cc.uoc.gr) katya/upstream Translation-en_US
Ign [http://ftp.cc.uoc.gr](http://ftp.cc.uoc.gr) katya/upstream Translation-en
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-i386/Packages](http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by dino99 on 2011-07-23
What a mess :( 
Never mix distro: seeing both edgy (by the way its outdated and repo removed) and natty. And what about those ftp & ppa urls ?

Be more serious, what do you expect ?

sudo gedit /etc/apt/sources.list

and cleanup the room.

---

### Post by Perfect Storm on 2011-07-23
Moved to Other OS/Distro Talk.

---

### Post by MossMethod on 2011-07-23
> **dino99 said:**
> What a mess :( 
Never mix distro: seeing both edgy (by the way its outdated and repo removed) and natty. And what about those ftp & ppa urls ?

Be more serious, what do you expect ?

sudo gedit /etc/apt/sources.list

and cleanup the room.

Ouch, haha yeah I read another thread and fixed it (as far as edgy and natty concerned) and came back and saw this so here's the update (lol, by the sound of it there still some stuff I could get rid of). I wanted Gnome 3 thats what one of the PPA's is for ( I ran the code to do it).  Ill show you my software  source see what u would cut, since i am a beginner.  (I sign on to Gnome 3 when logging in)

Anyways I was able to eliminate fail to fetch errors by changing from the main server and tweaking wine.


Main Software (Linux Mint Software)
Upstream packages (upstream)
imported packages (import)
back ported packages (backport)



Other Software
Ubuntu 11.04 Natty Narwhal
Recommended updates
important security updates
Canonical Partners
Independent
[http://packages.mediabuntu.org/natty](http://packages.mediabuntu.org/natty)
[http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) natty-getdeb (apps)
[http://packages.medibuntu.org/karmic](http://packages.medibuntu.org/karmic)
http:..packages.mediabuntu.org/karmic (source code)
PPA.launchpad.net/Gnome3-team/ubuntu natty (main)
PPA.launchpad.net/Gnome3-team/ubuntu natty (main Source code)
file:///usr/share/local-repository binary/

(now when i run the  same code in terminal I get this)
sudo apt-get update
Ign file: binary/ InRelease
Ign file: binary/ Release.gpg                                                  
Ign file: binary/ Release                                                      
Ign file: binary/ Translation-en_US                                            
Ign file: binary/ Translation-en                                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease                              
Ign [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya InRelease                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg                                
Hit [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya Release.gpg                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release.gpg                        
Hit [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya Release                             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic InRelease                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya/main i386 Packages                  
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya/upstream i386 Packages              
Hit [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya/import i386 Packages                
Hit [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya/backport i386 Packages              
Ign [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya/backport TranslationIndex           
Ign [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya/import TranslationIndex             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main i386 Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe i386 Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse i386 Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main TranslationIndex                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free i386 Packages                     
Ign [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya/main TranslationIndex               
Ign [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya/upstream TranslationIndex           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse TranslationIndex                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted TranslationIndex                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe TranslationIndex                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe i386 Packages             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse i386 Packages           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main TranslationIndex              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse TranslationIndex        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted TranslationIndex        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free i386 Packages                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe TranslationIndex          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free TranslationIndex                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free TranslationIndex              
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya/backport Translation-en_US          
Ign [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya/backport Translation-en             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Sources                          
Ign [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya/import Translation-en_US            
Ign [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya/import Translation-en               
Ign [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya/main Translation-en_US              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya/main Translation-en                 
Ign [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya/upstream Translation-en_US          
Ign [http://packages.linuxmint-fr.net](http://packages.linuxmint-fr.net) katya/upstream Translation-en             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Sources            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en_US                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free i386 Packages                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Translation-en                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Translation-en          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en_US         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free TranslationIndex                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free TranslationIndex             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en
Reading package lists... Done

As for the mixing and matching,  yeah i have been trying different stuff.

Hey thanks for replying :p

---

### Post by MossMethod on 2011-07-23
> **Artificial Intelligence said:**
> Moved to Other OS/Distro Talk.

:popcorn: dEUS EX RULES (At least the 1st  video game, if you were referring to that in your sig )

---

### Post by Perfect Storm on 2011-07-24
> **MossMethod said:**
> :popcorn: dEUS EX RULES (At least the 1st  video game, if you were referring to that in your sig )

[http://en.wikipedia.org/wiki/Deus_ex_machina](http://en.wikipedia.org/wiki/Deus_ex_machina)

---

