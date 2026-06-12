---
title: "i cant install ANYTHING!"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Countra on 2007-12-11
Hi, i cant install any packages, updates, etc.
I get these weird errors such as this one when i wanted to update:
> W: Duplicate sources.list entry [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_feisty_main_binary-i386_Packages)

and oh yeah, today when i started the computer it said that it was forced to check some drive (i think it was /sda/sd1/ or something) anyways, so it gone to 100%..
Yeah, and i have Ubuntu(of course) the newest version avalaible..
[COLOR="Red"]Heeeelp!!![/COLOR] :confused: :(

---

### Post by meborc on 2007-12-11
the problem is in the /etc/apt/sources.list file... as you see from the error, there is a duplicate line somewhere... so try to remember, did you edit this file somehow... what did you add? ... just look for the line that is duplicated (in 2 different places) and put ## before it...

then ```
sudo apt-get update
sudo apt-get install ANYTHING
```
:)

oh, and the disk check is something ubuntu performs in every 30 mounts or so just to see if your harddisk is running fine

---

### Post by PmDematagoda on 2007-12-11
Post the result of:-
```

cat /etc/apt/sources.list
```

And the disk check is routine, it takes place after a certain amount of boots to ensure that your drives stay consistent and have no errors.

---

### Post by Countra on 2007-12-11
this is another error i got:
> E: tzdata: subprocess post-installation script returned error exit status 1

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007j-0ubuntu0.7.04_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007j-0ubuntu0.7.04_all.deb)
  


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/liblame0_3.97-0.0_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/liblame0_3.97-0.0_i386.deb)
  


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libmp4v2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libmp4v2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5_i386.deb)
  


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcre3_7.4-0ubuntu0.7.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcre3_7.4-0ubuntu0.7.04.1_i386.deb)
  


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcrecpp0_7.4-0ubuntu0.7.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcrecpp0_7.4-0ubuntu0.7.04.1_i386.deb)
  


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcore/libxvidcore4_1.1.2-0.1ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcore/libxvidcore4_1.1.2-0.1ubuntu2_i386.deb)
  


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer-skins/mplayer-skins_2-7_all.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer-skins/mplayer-skins_2-7_all.deb)
  


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.7.3-1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.7.3-1.1_i386.deb)
  


W: Failed to fetch [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.50~winehq0~ubuntu~7.04-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.50~winehq0~ubuntu~7.04-1_i386.deb)
  




---

### Post by viking777 on 2007-12-11
It really does sound like your sources.list file is screwed.

Very easy way to fix that, go here:

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Fill in appropriate details and get a new one - all automtically!!

---

### Post by Countra on 2007-12-11
apt-get update gave me:
> Hit [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty/amsn Sources                              
Hit [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty/thunderbird Sources                       
Err [http://www.in.fh-merseburg.de](http://www.in.fh-merseburg.de) feisty/main Sources                          
  404 Not Found
Get:31 [http://apt.sourceguru.net](http://apt.sourceguru.net) feisty Release.gpg [189B]                     
Ign [http://apt.sourceguru.net](http://apt.sourceguru.net) feisty/all Translation-en_US                     
Hit [http://apt.sourceguru.net](http://apt.sourceguru.net) feisty Release                                   
Err [http://apt.sourceguru.net](http://apt.sourceguru.net) feisty Release                                   
  
Get:32 [http://apt.sourceguru.net](http://apt.sourceguru.net) feisty Release [4771B]                        
Ign [http://apt.sourceguru.net](http://apt.sourceguru.net) feisty Release                                   
Hit [http://apt.sourceguru.net](http://apt.sourceguru.net) feisty/all Packages                              
Hit [http://apt.sourceguru.net](http://apt.sourceguru.net) feisty/all Sources                               
Get:33 [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-feisty Release.gpg [191B]                
Ign [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-feisty/all Translation-en_US                
Get:34 [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports Release.gpg [189B]              
Hit [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-feisty Release                              
Err [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-feisty Release                              
  
Get:35 [http://mi.mirror.garr.it](http://mi.mirror.garr.it) feisty-backports Release.gpg [191B]            
Ign [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports/main Translation-en_US             
Ign [http://mi.mirror.garr.it](http://mi.mirror.garr.it) feisty-backports/main Translation-en_US           
Get:36 [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-feisty Release [4141B]                   
Get:37 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                          
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                     
Ign [http://mi.mirror.garr.it](http://mi.mirror.garr.it) feisty-backports/restricted Translation-en_US     
Ign [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-feisty Release                              
Ign [http://mi.mirror.garr.it](http://mi.mirror.garr.it) feisty-backports/universe Translation-en_US       
Hit [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-feisty/all Packages                         
Ign [http://mi.mirror.garr.it](http://mi.mirror.garr.it) feisty-backports/multiverse Translation-en_US     
Hit [http://mi.mirror.garr.it](http://mi.mirror.garr.it) feisty-backports Release                          
Hit [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-feisty/all Sources                          
Hit [http://mi.mirror.garr.it](http://mi.mirror.garr.it) feisty-backports/main Packages                    
Hit [http://mi.mirror.garr.it](http://mi.mirror.garr.it) feisty-backports/restricted Packages              
Hit [http://mi.mirror.garr.it](http://mi.mirror.garr.it) feisty-backports/universe Packages                
Hit [http://mi.mirror.garr.it](http://mi.mirror.garr.it) feisty-backports/multiverse Packages              
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Err [http://dl.google.com](http://dl.google.com) stable Release                                        
  
Hit [http://mi.mirror.garr.it](http://mi.mirror.garr.it) feisty-backports/main Sources                     
Hit [http://mi.mirror.garr.it](http://mi.mirror.garr.it) feisty-backports/restricted Sources               
Get:38 [http://dl.google.com](http://dl.google.com) stable Release [748B]                              
Ign [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://mi.mirror.garr.it](http://mi.mirror.garr.it) feisty-backports/universe Sources                 
Hit [http://mi.mirror.garr.it](http://mi.mirror.garr.it) feisty-backports/multiverse Sources               
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages                              
Hit [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports Release                            
Err [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports Release                            
  
Get:39 [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports Release [665B]                  
Ign [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports Release                            
Ign [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports/main Packages                      
Hit [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports/main Sources                       
Hit [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports/main Packages                      
Get:40 [http://dl.ivtvdriver.org](http://dl.ivtvdriver.org) feisty Release.gpg [189B]                      
Ign [http://dl.ivtvdriver.org](http://dl.ivtvdriver.org) feisty/all Translation-en_US                      
Hit [http://dl.ivtvdriver.org](http://dl.ivtvdriver.org) feisty Release                                    
Err [http://dl.ivtvdriver.org](http://dl.ivtvdriver.org) feisty Release                                    
  
Get:41 [http://dl.ivtvdriver.org](http://dl.ivtvdriver.org) feisty Release [10.3kB]                        
Get:42 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]               
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_US              
Ign [http://dl.ivtvdriver.org](http://dl.ivtvdriver.org) feisty Release                                    
Get:43 [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) feisty Release.gpg [189B]                   
Ign [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) feisty/uniklu Translation-en_US                
Ign [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) feisty/uniklu-intern Translation-en_US         
Hit [http://dl.ivtvdriver.org](http://dl.ivtvdriver.org) feisty/all Packages                               
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release                             
Ign [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) feisty/uniklu-testing Translation-en_US        
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) feisty Release                                 
Err [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) feisty Release                                 
  
Hit [http://dl.ivtvdriver.org](http://dl.ivtvdriver.org) feisty/all Sources                                
Get:44 [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) feisty Release [11.0kB]                     
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                       
Ign [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) feisty Release                                 
Get:45 [http://edevelop.org](http://edevelop.org) feisty Release.gpg [189B]                           
Ign [http://edevelop.org](http://edevelop.org) feisty/e17 Translation-en_US                           
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources                        
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) feisty/uniklu Packages                         
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) feisty/uniklu-intern Packages                  
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) feisty/uniklu-testing Packages                 
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) feisty/uniklu Sources                          
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) feisty/uniklu-intern Sources                   
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) feisty/uniklu-testing Sources                  
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                       
Hit [http://edevelop.org](http://edevelop.org) feisty Release                                         
Err [http://edevelop.org](http://edevelop.org) feisty Release                                         
  
Get:46 [http://edevelop.org](http://edevelop.org) feisty Release [997B]                               
Ign [http://edevelop.org](http://edevelop.org) feisty Release                                         
Ign [http://edevelop.org](http://edevelop.org) feisty/e17 Packages                                    
Ign [http://edevelop.org](http://edevelop.org) feisty/e17 Sources                                     
Hit [http://edevelop.org](http://edevelop.org) feisty/e17 Packages                                    
Ign [http://www.mpe.mpg.de](http://www.mpe.mpg.de) ./ Release.gpg                                       
Ign [http://www.mpe.mpg.de](http://www.mpe.mpg.de) ./ Translation-en_US                                 
Hit [http://www.mpe.mpg.de](http://www.mpe.mpg.de) ./ Release                                           
Hit [http://www.mpe.mpg.de](http://www.mpe.mpg.de) ./ Packages                                          
Hit [http://edevelop.org](http://edevelop.org) feisty/e17 Sources                                     
Hit [http://www.mpe.mpg.de](http://www.mpe.mpg.de) ./ Sources                                           
Ign [http://debian.o-hand.com](http://debian.o-hand.com) feisty/ Release.gpg                               
Ign [http://debian.o-hand.com](http://debian.o-hand.com) feisty/ Translation-en_US                         
Hit [http://debian.o-hand.com](http://debian.o-hand.com) feisty/ Release                                   
Ign [http://debian.o-hand.com](http://debian.o-hand.com) feisty/ Packages                                  
Ign [http://debian.o-hand.com](http://debian.o-hand.com) feisty/ Sources                                   
Hit [http://debian.o-hand.com](http://debian.o-hand.com) feisty/ Packages                                  
Get:47 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas Release.gpg [307B]           
Hit [http://debian.o-hand.com](http://debian.o-hand.com) feisty/ Sources                                   
Ign [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas/all Translation-en_US           
Get:48 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas Release [20.3kB]             
Get:49 [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty Release.gpg [189B]                      
Ign [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas Release                         
Get:50 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas/all Packages [13.4kB]        
Ign [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty/main Translation-en_US                     
Hit [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty Release                                    
Err [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty Release                                    
  
Get:51 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas/all Sources [2986B]          
Get:52 [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty Release [1363B]                         
Ign [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty Release                                    
Get:53 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]       
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg                            
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US                 
Get:54 [http://pkg-voip.buildserver.net](http://pkg-voip.buildserver.net) feisty Release.gpg [189B]               
Ign [http://pkg-voip.buildserver.net](http://pkg-voip.buildserver.net) feisty/main Translation-en_US              
Get:55 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release [5999B]          
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US             
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
Hit [http://pkg-voip.buildserver.net](http://pkg-voip.buildserver.net) feisty Release                             
Err [http://pkg-voip.buildserver.net](http://pkg-voip.buildserver.net) feisty Release                             
  
Ign [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty/main Packages                              
Ign [http://home.eng.iastate.edu](http://home.eng.iastate.edu) feisty Release.gpg                             
Get:56 [http://pkg-voip.buildserver.net](http://pkg-voip.buildserver.net) feisty Release [10.4kB]                 
Hit [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty/main Packages                              
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release.gpg                         
  Could not resolve 'archive.ubuntustudio.org'
Ign [http://home.eng.iastate.edu](http://home.eng.iastate.edu) feisty/all Translation-en_US                   
Ign [http://home.eng.iastate.edu](http://home.eng.iastate.edu) feisty Release                                 
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US              
  Could not resolve 'archive.ubuntustudio.org'
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                          
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                      
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                           
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                       
Ign [http://home.eng.iastate.edu](http://home.eng.iastate.edu) feisty/all Packages                            
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                          
  404 Not Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                      
  404 Not Found
Ign [http://pkg-voip.buildserver.net](http://pkg-voip.buildserver.net) feisty Release                             
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                           
  404 Not Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                       
  404 Not Found
Hit [http://pkg-voip.buildserver.net](http://pkg-voip.buildserver.net) feisty/main Packages                       
Ign [http://home.eng.iastate.edu](http://home.eng.iastate.edu) feisty/all Sources                             
Get:57 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release.gpg [189B]                    
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets Translation-en_US             
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release                             
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release                                  
Err [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release                                  
  
Get:58 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release [3687B]                       
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release                                  
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets Packages                      
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets Sources                       
Err [http://home.eng.iastate.edu](http://home.eng.iastate.edu) feisty/all Packages                            
  404 Not Found
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
Err [http://home.eng.iastate.edu](http://home.eng.iastate.edu) feisty/all Sources                             
  404 Not Found
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Sources                        
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
  Could not resolve 'archive.ubuntustudio.org'
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Sources                        
  Could not resolve 'archive.ubuntustudio.org'
Get:59 [http://archive.czessi.net](http://archive.czessi.net) feisty Release.gpg [481B]                     
Ign [http://archive.czessi.net](http://archive.czessi.net) feisty/main Translation-en_US                    
Ign [http://archive.czessi.net](http://archive.czessi.net) feisty/restricted Translation-en_US              
Ign [http://archive.czessi.net](http://archive.czessi.net) feisty/universe Translation-en_US                
Ign [http://archive.czessi.net](http://archive.czessi.net) feisty/multiverse Translation-en_US              
Ign [http://archive.czessi.net](http://archive.czessi.net) feisty/preview Translation-en_US                 
Hit [http://archive.czessi.net](http://archive.czessi.net) feisty Release                                   
Err [http://archive.czessi.net](http://archive.czessi.net) feisty Release                                   
  
Get:60 [http://archive.czessi.net](http://archive.czessi.net) feisty Release [27.9kB]                       
Ign [http://archive.czessi.net](http://archive.czessi.net) feisty Release                                   
Hit [http://archive.czessi.net](http://archive.czessi.net) feisty/main Packages                             
Hit [http://archive.czessi.net](http://archive.czessi.net) feisty/restricted Packages                       
Hit [http://archive.czessi.net](http://archive.czessi.net) feisty/universe Packages                         
Hit [http://archive.czessi.net](http://archive.czessi.net) feisty/multiverse Packages                       
Hit [http://archive.czessi.net](http://archive.czessi.net) feisty/preview Packages                          
Hit [http://archive.czessi.net](http://archive.czessi.net) feisty/main Sources                              
Hit [http://archive.czessi.net](http://archive.czessi.net) feisty/restricted Sources                        
Hit [http://archive.czessi.net](http://archive.czessi.net) feisty/universe Sources                          
Hit [http://archive.czessi.net](http://archive.czessi.net) feisty/multiverse Sources                        
Hit [http://archive.czessi.net](http://archive.czessi.net) feisty/preview Sources                           
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) edgy Release.gpg                  
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) edgy/main Translation-en_US       
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) edgy/dupdate Translation-en_US    
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) edgy/french Translation-en_US     
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu Release.gpg                
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/main Translation-en_US     
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/dupdate Translation-en_US  
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/french Translation-en_US   
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) edgy Release                      
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu Release                    
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) edgy/main Packages                
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) edgy/dupdate Packages             
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) edgy/french Packages              
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/main Packages              
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/dupdate Packages           
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/french Packages            
Hit [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) edgy/main Packages                
Hit [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) edgy/dupdate Packages             
Hit [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) edgy/french Packages              
Hit [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/main Packages              
Hit [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/dupdate Packages           
Hit [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/french Packages            
Get:61 [http://deb.opera.com](http://deb.opera.com) etch Release.gpg [189B]                            
Get:62 [http://repository.debuntu.org](http://repository.debuntu.org) feisty Release.gpg [189B]                 
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Translation-en_US                       
Hit [http://deb.opera.com](http://deb.opera.com) etch Release                                          
Err [http://deb.opera.com](http://deb.opera.com) etch Release                                          
  
Get:63 [http://deb.opera.com](http://deb.opera.com) etch Release [866B]                                
Ign [http://deb.opera.com](http://deb.opera.com) etch Release                                          
Ign [http://repository.debuntu.org](http://repository.debuntu.org) feisty/multiverse Translation-en_US          
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages                                
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages                                
Hit [http://repository.debuntu.org](http://repository.debuntu.org) feisty Release                               
Err [http://repository.debuntu.org](http://repository.debuntu.org) feisty Release                               
  
Get:64 [http://repository.debuntu.org](http://repository.debuntu.org) feisty Release [3079B]                    
Ign [http://repository.debuntu.org](http://repository.debuntu.org) feisty Release                               
Get:65 [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego Release.gpg [189B]          
Ign [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego/all Translation-en_US          
Hit [http://repository.debuntu.org](http://repository.debuntu.org) feisty/multiverse Packages                   
Get:66 [http://mirror.randumb.org](http://mirror.randumb.org) feisty-darkmagez Release.gpg [189B]           
Ign [http://mirror.randumb.org](http://mirror.randumb.org) feisty-darkmagez/multimedia-experimental Translation-en_US
Hit [http://repository.debuntu.org](http://repository.debuntu.org) feisty/multiverse Sources                    
Hit [http://mirror.randumb.org](http://mirror.randumb.org) feisty-darkmagez Release                         
Err [http://mirror.randumb.org](http://mirror.randumb.org) feisty-darkmagez Release                         
  
Hit [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego Release                        
Err [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego Release                        
  
Get:67 [http://mirror.randumb.org](http://mirror.randumb.org) feisty-darkmagez Release [7638B]              
Ign [http://mirror.randumb.org](http://mirror.randumb.org) feisty-darkmagez Release                         
Get:68 [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego Release [40.8kB]            
Hit [http://mirror.randumb.org](http://mirror.randumb.org) feisty-darkmagez/multimedia-experimental Packages
Hit [http://mirror.randumb.org](http://mirror.randumb.org) feisty-darkmagez/multimedia-experimental Sources 
Ign [http://www.tvfreeplayer.com](http://www.tvfreeplayer.com) feisty Release.gpg                             
Ign [http://www.tvfreeplayer.com](http://www.tvfreeplayer.com) feisty/all Translation-en_US                   
Hit [http://www.tvfreeplayer.com](http://www.tvfreeplayer.com) feisty Release                                 
Hit [http://www.tvfreeplayer.com](http://www.tvfreeplayer.com) feisty/all Packages                            
Hit [http://www.tvfreeplayer.com](http://www.tvfreeplayer.com) feisty/all Sources                             
Ign [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego Release                        
Hit [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego/all Packages                   
Get:69 [http://debs.peadrop.com](http://debs.peadrop.com) feisty Release.gpg [189B]                       
Ign [http://debs.peadrop.com](http://debs.peadrop.com) feisty/all Translation-en_US                       
Hit [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego/all Sources                    
Get:70 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US                    
Hit [http://debs.peadrop.com](http://debs.peadrop.com) feisty Release                                     
Err [http://debs.peadrop.com](http://debs.peadrop.com) feisty Release                                     
  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US              
Get:71 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Get:72 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US     
Get:73 [http://debs.peadrop.com](http://debs.peadrop.com) feisty Release [6970B]                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US     
Get:74 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_US     
Ign [http://debs.peadrop.com](http://debs.peadrop.com) feisty Release                                     
Get:75 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages                       
Hit [http://debs.peadrop.com](http://debs.peadrop.com) feisty/all Packages                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages              
Hit [http://debs.peadrop.com](http://debs.peadrop.com) feisty/all Sources                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Ign [http://www.kiberpipa.org](http://www.kiberpipa.org) ./ Release.gpg                                    
Ign [http://www.kiberpipa.org](http://www.kiberpipa.org) ./ Translation-en_US                              
Ign [http://www.kiberpipa.org](http://www.kiberpipa.org) ./ Release                                        
Ign [http://www.kiberpipa.org](http://www.kiberpipa.org) ./ Packages                                       
Hit [http://www.kiberpipa.org](http://www.kiberpipa.org) ./ Packages                                       
Get:76 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg [191B]               
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-en_US
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release
Err [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release
  
Get:77 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release [2965B]
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Sources
Fetched 320kB in 2m31s (2113B/s)
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg)  Could not resolve 'archive.ubuntustudio.org'
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntustudio.org'
Failed to fetch [http://ubuntu.geole.info/dists/feisty/universe/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/feisty/multiverse/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/feisty/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/feisty/universe/source/Sources.gz](http://ubuntu.geole.info/dists/feisty/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/feisty/multiverse/source/Sources.gz](http://ubuntu.geole.info/dists/feisty/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/feisty-backports/main/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/feisty-backports/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/feisty-backports/universe/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/feisty-backports/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/feisty-backports/multiverse/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/feisty-backports/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/feisty-backports/restricted/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/feisty-backports/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/feisty-backports/main/source/Sources.gz](http://ubuntu.geole.info/dists/feisty-backports/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/feisty-backports/universe/source/Sources.gz](http://ubuntu.geole.info/dists/feisty-backports/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/feisty-backports/multiverse/source/Sources.gz](http://ubuntu.geole.info/dists/feisty-backports/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/feisty-backports/restricted/source/Sources.gz](http://ubuntu.geole.info/dists/feisty-backports/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://www.in.fh-merseburg.de/~jahn/opensync-0.21/dists/feisty/main/binary-i386/Packages.gz](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://www.in.fh-merseburg.de/~jahn/opensync-0.21/dists/feisty/main/source/Sources.gz](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/dists/feisty/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz)  404 Not Found
Failed to fetch [http://home.eng.iastate.edu/~superm1/dists/feisty/all/binary-i386/Packages.gz](http://home.eng.iastate.edu/~superm1/dists/feisty/all/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://home.eng.iastate.edu/~superm1/dists/feisty/all/source/Sources.gz](http://home.eng.iastate.edu/~superm1/dists/feisty/all/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz)  Could not resolve 'archive.ubuntustudio.org'
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/source/Sources.gz](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/source/Sources.gz)  Could not resolve 'archive.ubuntustudio.org'
Reading package lists... Done
W: GPG error: [http://www.telemail.fi](http://www.telemail.fi) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFFF5E937215FF
W: GPG error: [http://ftp.musicbrainz.org](http://ftp.musicbrainz.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3A39A02A92132F7B
W: GPG error: [http://cl.naist.jp](http://cl.naist.jp) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B8F0E6C98ABD1965
W: GPG error: [http://www.linux2go.dk](http://www.linux2go.dk) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A278DF5EE8BDA4E3
W: GPG error: [http://kubuntu.org](http://kubuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://kubuntu.org](http://kubuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3
W: GPG error: [http://snapshots.ekiga.net](http://snapshots.ekiga.net) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A5E3A5A52ABFCB1
W: GPG error: [http://ubuntu.davromaniak.eu](http://ubuntu.davromaniak.eu) feisty-depomaniak Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8BB73F9E1D59E694
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: GPG error: [http://deb.svx.pl](http://deb.svx.pl) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C12ADDB16FB65A0F
W: GPG error: [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC0A1CC62F306651
W: GPG error: [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 371A69E3AE3BE9AA
W: GPG error: [http://apt.sourceguru.net](http://apt.sourceguru.net) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2404ED3A6AAAA569
W: GPG error: [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 80E5E56B02544D0E
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8CC68B397E2E4741
W: GPG error: [http://dl.ivtvdriver.org](http://dl.ivtvdriver.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4C8BC4C880DF6D58
W: GPG error: [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 84F27CD6A2BF7BCB
W: GPG error: [http://edevelop.org](http://edevelop.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 223020C2A7C6F0DF
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: GPG error: [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7096EDEA5B4E69BB
W: GPG error: [http://pkg-voip.buildserver.net](http://pkg-voip.buildserver.net) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A5E3A5A52ABFCB1
W: GPG error: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: GPG error: [http://archive.czessi.net](http://archive.czessi.net) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A714EB87D1B1F415
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [http://repository.debuntu.org](http://repository.debuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E466170BCF1FC29
W: GPG error: [http://mirror.randumb.org](http://mirror.randumb.org) feisty-darkmagez Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB5D6B0AA3012FB3
W: GPG error: [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 81600957AF425CB5
W: GPG error: [http://debs.peadrop.com](http://debs.peadrop.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 02D40794DD385D79
W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: Duplicate sources.list entry [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_feisty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
arsham@arsham-desktop:~$ [



And this is what i got from "source-o-matic":
> # Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) feisty main restricted 
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) feisty universe multiverse 
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

so i did what i said and i got this:
root@arsham-desktop:/home/arsham# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
gpg: directory `/root/.gnupg' created
gpg: new configuration file `/root/.gnupg/gpg.conf' created
gpg: WARNING: options in `/root/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/root/.gnupg/secring.gpg' created
gpg: keyring `/root/.gnupg/pubring.gpg' created
gpg: "KEY" not a key ID: skipping
root@arsham-desktop:/home/arsham# 
root@arsham-desktop:/home/arsham# gpg --export --armor KEY | sudo apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found

i still have problems :(

---

### Post by Countra on 2007-12-11
And this is what i got from cat /etc/apt/sources.list
> arsham@arsham-desktop:~$ cat /etc/apt/sources.list
# Trevi&#65533;o's Ubuntu Feisty Fawn Sources list
# [http://3v1n0.tuxfamily.org/blog/?page_id=13](http://3v1n0.tuxfamily.org/blog/?page_id=13)
#
# Repository List based on standard feisty with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
#  gpg --keyserver subkeys.pgp.net --recv KEY
#  gpg --export --armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
#  wget URL --quiet -O - | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
#  sudo apt-key add FILE
#
# In the repository list page there's also a script that can do this
# work automatically, this is suggested only if you know what you're doing

# Ubuntu supported packages (GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-proposed main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-proposed main restricted

# Ubuntu community supported packages (GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-proposed universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-proposed universe multiverse

# Ubuntu backports project (GPG key: 437D05B5)
deb [http://mi.mirror.garr.it/ubuntu](http://mi.mirror.garr.it/ubuntu) feisty-backports main restricted universe multiverse
deb-src [http://mi.mirror.garr.it/ubuntu](http://mi.mirror.garr.it/ubuntu) feisty-backports main restricted universe multiverse

# CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu servers.
# RealPlayer10, Opera, VmWare Server and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

# UbuntuStudio Repository (GPG key: B6A4EB33)
# GPG key-file: [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg)
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb-src [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

## kubuntu.org packages for the latest KDE version (GPG key: DD4D5088)
deb [http://kubuntu.org/packages/kde-357](http://kubuntu.org/packages/kde-357) feisty main
deb-src [http://kubuntu.org/packages/kde-357](http://kubuntu.org/packages/kde-357) feisty main
# deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) feisty main
# deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) feisty main

## kubuntu.org packages for the latest Koffice version (GPG key: DD4D5088)
# deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) feisty main
# deb-src [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) feisty main

## kubuntu.org packages for the latest amaroK version (GPG key: DD4D5088)
# deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) feisty main
# deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) feisty main

# kubuntu.org packages for KDE4 alpha-1 (GPG key: DD4D5088)
deb [http://kubuntu.org/packages/kde4-3.90.1](http://kubuntu.org/packages/kde4-3.90.1) feisty main
deb-src [http://kubuntu.org/packages/kde4-3.90.1](http://kubuntu.org/packages/kde4-3.90.1) feisty main

# Bleeding edge wine packages (GPG key: 387EE263)
# GPG key-file: [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg)
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

# Seveas' packages (GPG key: 1135D466)
# GPG key-file: [http://mirror.ubuntulinux.nl/1135D466.gpg](http://mirror.ubuntulinux.nl/1135D466.gpg)
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas all
deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas all

# The Opera browser (packages) (GPG key: 6A423791)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

# Google picasa packages (GPG key: 7FAC5991)
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

# Medibuntu (Multimedia, Entertainment & Distraction In Ubuntu - ex Penguin Liberation Front)
# GPG key-file: [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

# The repository from Kubuntu Germany
# GPG key-file: [http://archive.czessi.net/ubuntu/kczessi.gpg](http://archive.czessi.net/ubuntu/kczessi.gpg)
deb [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) feisty main restricted universe multiverse preview
deb-src [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) feisty main restricted universe multiverse preview

# Achim's Unofficial 'feisty' Kubuntu packages
# GPG key-file: [http://www.mpe.mpg.de/~ach/ach-gpg.asc](http://www.mpe.mpg.de/~ach/ach-gpg.asc)
deb [http://www.mpe.mpg.de/~ach/kubuntu/feisty](http://www.mpe.mpg.de/~ach/kubuntu/feisty) ./
deb-src [http://www.mpe.mpg.de/~ach/kubuntu/feisty](http://www.mpe.mpg.de/~ach/kubuntu/feisty) ./

# Ubuntu feisty University Klagenfurt packages
# GPG key-file: [http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub](http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub)
# $ sudo apt-key add uniklu-debuild.pub 
#   uniklu:         backports and new packages
#   uniklu-intern:  not freely redistributable (jvm), or modified packages
#   uniklu-testing: packages not ready for general use
deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu
deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu-intern
deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu-testing
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu-intern
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu-testing

# MEPIS improvements, overrides and updates (distro based on kubuntu)
# deb [http://apt.mepis.org/mepis32-6.5/](http://apt.mepis.org/mepis32-6.5/) mepis main
# deb [http://apt.mepis.org/simply32-6.0/](http://apt.mepis.org/simply32-6.0/) mepis main

# Ekiga and Debian pkg-voip
deb [http://pkg-voip.buildserver.net/ubuntu](http://pkg-voip.buildserver.net/ubuntu) feisty main

# MythTV Repository for Ubuntu Linux (GPG key: 80DF6D58)
deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) feisty all
deb-src [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) feisty all

# Official Beryl Ubuntu Packages (GPG key: 1609B551)
# GPG key-file: [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg)
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

# Ubuntu repository for Screenlets (GPG key: F854AFD7)
# GPG key-file: [http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg](http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg)
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets
deb-src [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets

# Subpixel Font rendering packages (GPG key: 937215FF)
# Improved fonts on LCDs - WARNING: May violate some patents
# GPG key-file: [http://www.telemail.fi/mlind/ubuntu/937215FF.gpg](http://www.telemail.fi/mlind/ubuntu/937215FF.gpg)
deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts main
deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts main

## Others mlind experimental misc Packages (GPG key: 937215FF)
## GPG key-file: [http://www.telemail.fi/mlind/ubuntu/937215FF.gpg](http://www.telemail.fi/mlind/ubuntu/937215FF.gpg)
# deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty experimental
# deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty experimental

# Skype packages
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

# Geole's Ubuntu Repository
# GPG key-file: [http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg](http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg)
deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) feisty universe multiverse
deb-src [http://ubuntu.geole.info/](http://ubuntu.geole.info/) feisty universe multiverse
deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) feisty-backports main universe multiverse restricted
deb-src [http://ubuntu.geole.info/](http://ubuntu.geole.info/) feisty-backports main universe multiverse restricted

# Linux2Go Ubuntu Packages (GPG key: E8BDA4E3)
deb [http://www.linux2go.dk/ubuntu](http://www.linux2go.dk/ubuntu) feisty main
deb-src [http://www.linux2go.dk/ubuntu](http://www.linux2go.dk/ubuntu) feisty main

# Asher256's Repository
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) edgy main dupdate french
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french

# Tvfreeplayer Packages (GPG key: )
# GPG key-file: [http://www.tvfreeplayer.com/linux/falcon/tvfreeplayer.gpg](http://www.tvfreeplayer.com/linux/falcon/tvfreeplayer.gpg)
deb [http://www.tvfreeplayer.com/linux/falcon](http://www.tvfreeplayer.com/linux/falcon) feisty all
deb-src [http://www.tvfreeplayer.com/linux/falcon](http://www.tvfreeplayer.com/linux/falcon) feisty all

# gnomemeeting - ekiga (GPG key: 52ABFCB1)
deb [http://snapshots.ekiga.net/ubuntu/](http://snapshots.ekiga.net/ubuntu/) feisty main
deb-src [http://snapshots.ekiga.net/ubuntu/](http://snapshots.ekiga.net/ubuntu/) feisty main

## lprod packages: many audio/video apps: avidemux, cinelerra...
# deb [http://lprod.org/deb/feisty/](http://lprod.org/deb/feisty/) ./
# deb-src [http://lprod.org/deb/feisty/](http://lprod.org/deb/feisty/) ./

# Cinelerra Feisty packages
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./

## Spring Packages (RTS game)
# deb [ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/](ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/) /
# deb-src [ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/](ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/) /

# Cafuego's feisty Stuff: Broadcom firmware, google-earth, secondlife (GPG key: 969F3F57)...
deb [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego all
deb-src [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego all

# Debuntu Ubuntu feisty packages
# GPG Key: [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt)
deb [http://repository.debuntu.org/](http://repository.debuntu.org/) feisty multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) feisty multiverse

## BMPx feisty Repository
## GPG key-file: [http://files.beep-media-player.org/packages/bmp-packages.pubkey](http://files.beep-media-player.org/packages/bmp-packages.pubkey)
# deb [http://files.beep-media-player.org/packages/ubuntu](http://files.beep-media-player.org/packages/ubuntu) feisty main testing
# deb-src [http://files.beep-media-player.org/packages/ubuntu](http://files.beep-media-player.org/packages/ubuntu) feisty main testing

# Morgoth Repository (GPG key: 7E2E4741)
# Provides Monkey's Audio, xmms pugins, vlc plugins, gqview, audacius, audacity...
# GPG key-file: [http://morgoth.free.fr/files/morgoth-signkey.gpg.asc](http://morgoth.free.fr/files/morgoth-signkey.gpg.asc)
deb [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) feisty-backports main
deb-src [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) feisty-backports main

## ATi & nVidia drivers Ubuntu packages
## GPG key: [http://albertomilone.com/drivers/tseliot.asc](http://albertomilone.com/drivers/tseliot.asc)
# deb [http://www.albertomilone.com/drivers/feisty/latest/32bit](http://www.albertomilone.com/drivers/feisty/latest/32bit) binary/

# Automatix repository (GPG key: E23C5FC3)
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

# edevelop - e17 (Enlightenment DR 17)
# GPG key: [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc)
deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17
deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17
# deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) feisty e17
# deb-src [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) feisty e17

# Musicbrainz Repository
# GPG key-file: [http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/public.key](http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/public.key)
deb [http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu](http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu) feisty musicbrainz
deb-src [http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu](http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu) feisty musicbrainz

## Imbrandons software repository (GPG key: 887D9FD2)
## GPG key-file: [http://www.imbrandon.com/packages/887D9FD2.gpg](http://www.imbrandon.com/packages/887D9FD2.gpg)
# deb [http://www.imbrandon.com/packages](http://www.imbrandon.com/packages) feisty all
# deb-src [http://www.imbrandon.com/packages](http://www.imbrandon.com/packages) feisty all

## Candyz's Ubuntu Packages
## GPG key-file: [http://cle.linux.org.tw/candyz/Ubuntu/candyz.key](http://cle.linux.org.tw/candyz/Ubuntu/candyz.key)
# deb [http://cle.linux.org.tw/candyz/Ubuntu/feisty](http://cle.linux.org.tw/candyz/Ubuntu/feisty) i386/

# The Ubuntu NLP Repository (GPG key: 8ABD1965)
# GPG key-file: [http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg](http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg)
deb [http://cl.naist.jp/~eric-n/ubuntu-nlp](http://cl.naist.jp/~eric-n/ubuntu-nlp) feisty all
deb-src [http://cl.naist.jp/~eric-n/ubuntu-nlp](http://cl.naist.jp/~eric-n/ubuntu-nlp) feisty all

# Ubuntu System Administrator packages (GPG key: 2F306651)
# GPG key-file: [http://ubuntu.moshen.de/2F306651.gpg](http://ubuntu.moshen.de/2F306651.gpg)
deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty multimedia misc
deb-src [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty multimedia misc

## Michael Biebl Tracker Repository (GPG key: BD058554)
## GPG Key-file: [http://www.teco.edu/~biebl/biebl.asc](http://www.teco.edu/~biebl/biebl.asc)
# deb [http://debs.michaelbiebl.de/](http://debs.michaelbiebl.de/) feisty main
# deb-src [http://debs.michaelbiebl.de/](http://debs.michaelbiebl.de/) feisty main

# The Consciousness Repository (GPG key: DD385D79)
# GPG key-file: [http://debs.peadrop.com/DD385D79.gpg](http://debs.peadrop.com/DD385D79.gpg)
deb [http://debs.peadrop.com](http://debs.peadrop.com) feisty all
deb-src [http://debs.peadrop.com](http://debs.peadrop.com) feisty all

## Tolero Ubuntu Repository
# deb [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) feisty main
# deb-src [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) feisty main

# IVTV Repository for Ubuntu Linux (GPG key: 80DF6D58)
# GPG key-file: [http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg](http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg)
deb [http://dl.ivtvdriver.org/ubuntu](http://dl.ivtvdriver.org/ubuntu) feisty all
deb-src [http://dl.ivtvdriver.org/ubuntu](http://dl.ivtvdriver.org/ubuntu) feisty all

# syzygy42 repository: avant-window-navigator, exaile, closure... (GPG key: 8434D43A)
# GPG key-file: [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg)
deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty all
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty all

## Firefox 3.0 alpha builds for feisty (unstable)
# deb [http://gnomefreak.youmortals.com/mozilla-testing](http://gnomefreak.youmortals.com/mozilla-testing) feisty main
# deb-src [http://gnomefreak.youmortals.com/mozilla-testing](http://gnomefreak.youmortals.com/mozilla-testing) feisty main

## Swiftfox (enhanced Firefox for linux) packages
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

# Sonnes repository (aMule AdunanZa, Audacious)
deb [http://adurepo.altervista.org/ubuntu](http://adurepo.altervista.org/ubuntu) feisty all
deb-src [http://adurepo.altervista.org/ubuntu](http://adurepo.altervista.org/ubuntu) feisty all

# darkmagez repository: rhythmbox and newer gtk (GPG key: A3012FB3)
# GPG key-file: [http://mirror.randumb.org/darkmagez/repo/A3012FB3.gpg](http://mirror.randumb.org/darkmagez/repo/A3012FB3.gpg)
deb [http://mirror.randumb.org/darkmagez/repo](http://mirror.randumb.org/darkmagez/repo) feisty-darkmagez multimedia-experimental #core-experimental
deb-src [http://mirror.randumb.org/darkmagez/repo](http://mirror.randumb.org/darkmagez/repo) feisty-darkmagez multimedia-experimental #core-experimental

## Raof Repository: newer versions of Compiz, beagle, mono, scribus... (GPG key: 2F306651)
## GPG key-file: [http://raof.dyndns.org/falcon/2F306651.gpg](http://raof.dyndns.org/falcon/2F306651.gpg)
##deb [http://raof.dyndns.org/falcon](http://raof.dyndns.org/falcon) feisty all
# deb-src [http://raof.dyndns.org/falcon](http://raof.dyndns.org/falcon) feisty all

# FoLKeN 'Repozytorium' (GPG key: 6FB65A0F)
deb [http://deb.svx.pl/](http://deb.svx.pl/) feisty main universe bleeding
deb-src [http://deb.svx.pl/](http://deb.svx.pl/) feisty main universe bleeding

# Le d&#65533;pomaniak repository (GPG key: 1D59E694)
# GPG key-file: [http://ubuntu.davromaniak.eu/1D59E694.gpg](http://ubuntu.davromaniak.eu/1D59E694.gpg)
deb [http://ubuntu.davromaniak.eu](http://ubuntu.davromaniak.eu) feisty-depomaniak all
deb-src [http://ubuntu.davromaniak.eu](http://ubuntu.davromaniak.eu) feisty-depomaniak all

# Mez's Repository (GPG key: 6AAAA569)
# GPG key-file: [http://apt.sourceguru.net/6AAAA569.gpg](http://apt.sourceguru.net/6AAAA569.gpg)
deb [http://apt.sourceguru.net](http://apt.sourceguru.net) feisty all
deb-src [http://apt.sourceguru.net](http://apt.sourceguru.net) feisty all

# Ryan Kavanagh's packages (GPG key: 02544D0E)
# GPG key-file: [http://packages.ryanak.ca/02544D0E.gpg](http://packages.ryanak.ca/02544D0E.gpg)
deb [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-feisty all
deb-src [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-feisty all

# OpenedHand Debian/Ubuntu Packages
deb [http://debian.o-hand.com](http://debian.o-hand.com) feisty/
deb-src [http://debian.o-hand.com](http://debian.o-hand.com) feisty/

# OpenSync svn ubuntu repository (GPG key: B029CB84)
deb [http://www.in.fh-merseburg.de/~jahn/opensync-0.21/](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/) feisty main
deb-src [http://www.in.fh-merseburg.de/~jahn/opensync-0.21/](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/) feisty main

# Iuculano's debian packages (GPG key: AE3BE9AA)
# GPG key-file: [http://ubuntu.iuculano.it/AE3BE9AA.gpg](http://ubuntu.iuculano.it/AE3BE9AA.gpg)
deb [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty amsn thunderbird #ck-kernel #all
deb-src [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty amsn thunderbird #ck-kernel #all

# Elisa Debian Packages
deb [http://elisa.fluendo.com/packages](http://elisa.fluendo.com/packages) feisty main

# PollyCooke, il repository :)
deb [http://download.tuxfamily.org/pollyrepo](http://download.tuxfamily.org/pollyrepo) feisty/

# Trevi&#65533;o's Ubuntu Feisty Fawn Repository (GPG key: 81836EBF - DD800CD9)
# Many "random" bleeding edge software: aMule, aMSN, Mercury, flash...
# Further informations and complete packages list: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org)
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0

# Trevi&#65533;o's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, compiz and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs...
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

## Trevi&#65533;o's Ubuntu Suspend2 patched kernels Repository (GPG key: 81836EBF - DD800CD9)
## Ubuntu kernels patched with Suspend2 plus other related tools [www.suspend2.net](www.suspend2.net)
## Warning: they will replace standard ubuntu kernel related packages
# deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty suspend2
# deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty suspend2
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
arsham@arsham-desktop:~$ 



---

### Post by PmDematagoda on 2007-12-11
Forgive me for saying this, but the size of your sources list is simply too big to find the problem easily, so if you do not mind could you please follow these steps:-

1)Backup the sources.list file. 

2)Make a new sources.list file using [Source-O-Matic]("http://www.ubuntu-nl.org/source-o-matic/") and replace the old sources.list file with the new sources.list file.

3) Then do:-
```
sudo apt-get update
```

That should tell us if the issue is with the sources.list file or something else.

Incidentally I do not see any duplicate of the Wine repositories but I do see some Edgy repos not associated with Wine(I did go through the sources.list file, if you were wondering).

---

### Post by Partyboi2 on 2007-12-11
> and oh yeah, today when i started the computer it said that it was forced to check some drive (i think it was /sda/sd1/ or something) anyways, so it gone to 100%..
Yeah, and i have Ubuntu(of course) the newest version avalaible..
After 23 times the drive is mounted , ubuntu does a check on the drive to make sure there are no errors. So this is normal.

---

### Post by philinux on 2007-12-11
> **Partyboi2 said:**
> After 23 times the drive is mounted , ubuntu does a check on the drive to make sure there are no errors. So this is normal.

It depends on the size of your drive, mine was set by the system to 36 , everybody's will be slightly different. i've set mine to 50.

---

### Post by jaybombalous on 2007-12-11
> **philinux said:**
> It depends on the size of your drive, mine was set by the system to 36 , everybody's will be slightly different. i've set mine to 50.


if u use ext3 then enable journaling and **turn off** the disk check. :) Yes, journaling is much faster(in some instances), do some research at IBM.com and u will soon learn how to setup a proper computer.

---

### Post by Countra on 2007-12-11
How do i change my source.list file? Yes i did go to [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) but i dont know how to change my source.list also, i did go to [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine) but i didnt get much help there considering one thing:
root@arsham-desktop:/home/arsham# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
bash: deb: command not found
root@arsham-desktop:/home/arsham# 
see, this happens when i try to execute the command DEB; command not found.
Really annoying.. lol 
So basically, we have established that my source.list is messed uu, but i just need to know how to change the source.list and whats up with the deb command, anyways? hmm thanks! :)

---

### Post by PmDematagoda on 2007-12-11
Just open Nautilus in Root mode using:-

```
gksudo nautilus
```

Then go to the /etc/apt folder and replace the old sources.list file after making a backup of it.

After that is done execute the code I gave before, that should solve your problem.

> we have established that my source.list is ****** up(can you say that here? lol)

No you cannot, this is not a forum where you can just mouth off what ever comes to your head, be formal, concise and clear and also be helpful towards others, do not insult them or make fun of them.

---

### Post by Perfect Storm on 2007-12-11
By editing the source list manually;

```
sudo nano /etc/apt/sources.list
```

[ctrl]+[o] = save
[ctrl]+[x] = exit

---

### Post by aysiu on 2007-12-11
> **Countra said:**
> How do i change my source.list file? Follow these step-by-step instructions:
[http://www.psychocats.net/ubuntu/sources#key](http://www.psychocats.net/ubuntu/sources#key)

---

### Post by Countra on 2007-12-12
i have changed the source.list now but i still got
> E: tzdata: subprocess post-installation script returned error exit status 1
now when i tried to add a program through the Add/Remove feature :(

---

### Post by Countra on 2007-12-12
and this is the new source.list update btw:
> root@arsham-desktop:/home/arsham# apt-get update
Get:1 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/main Translation-en_US                 
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Get:2 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/universe Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US       
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates Release              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Get:4 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]     
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/main Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/restricted Packages        
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/universe Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/main Packages        
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/restricted Packages  
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/universe Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/multiverse Packages  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Fetched 4B in 1s (2B/s)
Reading package lists... Done


---

### Post by meborc on 2007-12-12
after changing the sources.list you must also update
```
sudo apt-get update
```
EDIT: you beat me to it :) ... and still problems?

---

### Post by t0p on 2007-12-12
> **Countra said:**
> How do i change my source.list file? Yes i did go to [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) but i dont know how to change my source.list also, i did go to [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine) but i didnt get much help there considering one thing:
root@arsham-desktop:/home/arsham# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
bash: deb: command not found
root@arsham-desktop:/home/arsham# 
see, this happens when i try to execute the command DEB; command not found.
Really annoying.. lol 
So basically, we have established that my source.list is messed uu, but i just need to know how to change the source.list and whats up with the deb command, anyways? hmm thanks! :)

About what you said concerning the "deb" command: as far as I know, there *is* no "deb" command!  .deb is what Ubuntu/Debian packages are called.  Exactly what are you trying to do when you give this "deb" command?

---

### Post by jken146 on 2007-12-12
It looks like a line that should be in /etc/apt/sources.list rather than a command.

---

### Post by Countra on 2007-12-13
well now the sources.list is changed and it is working great but i still cant install any packages/prorgams..
this is another error i got:> E: tzdata: subprocess post-installation script returned error exit status 1


really weird.. :-k
EDIT: and yeah, i have done the apt-get update, look:
> arsham@arsham-desktop:~$ sudo apt-get update
[sudo] password for arsham:
Get:1 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/main Translation-en_US                 
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Get:2 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/universe Translation-en_US     
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Get:3 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty Release [57.2kB]                  
Get:4 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_US              
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release [50.9kB]
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release                             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                       
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources                        
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                       
Get:7 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates Release [50.9kB]             
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [103kB]         
Get:9 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/main Packages [1007kB]               
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages [6341B]  
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages [59.2kB]   
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages [6092B]  
Get:13 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/restricted Packages [7628B]         
Get:14 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/universe Packages [3754kB]          
Get:15 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/multiverse Packages [148kB]         
Get:16 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/main Packages [160kB]       
Get:17 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/restricted Packages [6341B] 
Get:18 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/universe Packages [70.9kB]  
Get:19 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/multiverse Packages [12.8kB]
Fetched 5501kB in 3m1s (30.3kB/s)                                              
Reading package lists... Done

see? Nothing weird there :smile:

---

### Post by g2g591 on 2007-12-13
" tzdata: subprocess post-installation script returned error exit status 1"
is a message saying that the package tzdata isn't installing correctly. Your sources are fine. try changing your timezone  (tzdate=timezone data, had this issue when I upgraded to Gutsy, speaking of witch, why havn't you upgraded, fiesty isnt LTS) to something else, then running a command to install someting, then changing it back. Whatever other things you install ARE installing just fine

---

### Post by Anicka on 2007-12-13
You could try:```
sudo dpkg --configure tzdata
```

---

### Post by Countra on 2007-12-13
> arsham@arsham-desktop:~$ sudo dpkg --configure tzdata
Setting up tzdata (2007j-0ubuntu0.7.04) ...
Running 'tzconfig' to set this system's timezone.
/var/lib/dpkg/info/tzdata.postinst: line 27: /usr/sbin/tzconfig: No such file or directory
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tzdata
 i get the same error

> speaking of witch, why havn't you upgraded, fiesty isnt LTS
how could i update when i cant install anything? Or i dont know, im kind of new to this..

---

### Post by Anicka on 2007-12-13
New suggestion:```
sudo dpkg-reconfigure tzdata
```Choose an arbitary timezone (f.x. Europe/London). Re-run and put in your own timezone. It seems to have helped some guys [https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/153013](https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/153013)

---

### Post by Countra on 2007-12-14
WOW i changed my time zone to london and it WORKED! *victory dance*
thank you everyone! now im one step closer to become the ultimate LINUX WIZARD! haha
:-D

---

### Post by mastergunner on 2007-12-20
.......

---

### Post by PmDematagoda on 2007-12-20
> **mastergunner said:**
> .......

What do you mean by that? Do you have a problem? If so, a few words might be a little clearer than just using "...";).

---

### Post by Countra on 2007-12-21
roflmao that "...." was short for "im here to troll some and get a few more BEANS!" :-D

---

### Post by Perfect Storm on 2007-12-21
Bean hunter taking care off, please continue the on topic.

Thanks


A.I. Dude
Ubuntu forum Staff

---

