---
title: "New User want's to get rid of his problems"
date: 2011-04-04
forum: Any Other OS
---

### Post by Blanco Negro on 2011-04-04
Hello Everybody, 
Got my LOOONIXXX Mint 5 hours ago (first time Linux use), encountered some problems, (small), 
Anyway I got this Idea and wanted to realize it:
Register at ubuntuforums and create a tread in which I will post my problems and see if folks from this site can help, I assure you, i google my probs first and see if you had them here already.
Shall we start?
My GEar:

Compaq Presario cq40(-514TX)
2 Partitions:
Windows 7 32-Bit
Ubuntu 10.10 (linux mint 10)

First:
The walk-up-
- ... My experienced friend installed Lime 'inside' of my windows7, 
      no problems so far, but then suddenly Nvidia & wireless drivers don't func, download, reboot both orbs are green.
Proceed to download updates, out of inexperience decide to get 1's and 2's first and leave the 3's (talking about priority) get that one " firmware-b43-installer" didn't install proper, google it decide to go with TERMINAL, this is what comes out/happens next: 
___________________________________________________________
blanco@linuxmint ~ $ lspci -vvnn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
blanco@linuxmint ~ $ sudo apt-get update
[sudo] password for blanco: 
Ign file: binary/ Release.gpg
Ign file:/usr/share/local-repository/ binary/ Translation-en                                                                                        
Ign file:/usr/share/local-repository/ binary/ Translation-en_US                                                                                     
Ign file: binary/ Release                                                                                                                           
Ign file: binary/ Packages                                                                                                                          
Ign file: binary/ Packages                                                                                                                          
Get:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) julia Release.gpg [198B]                                                                                        
Ign [http://packages.linuxmint.com/](http://packages.linuxmint.com/) julia/import Translation-en                                                                                      
Ign [http://packages.linuxmint.com/](http://packages.linuxmint.com/) julia/import Translation-en_US                                                                                   
Ign [http://packages.linuxmint.com/](http://packages.linuxmint.com/) julia/main Translation-en                                                                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                                                                                               
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en                                                                            
Ign [http://packages.linuxmint.com/](http://packages.linuxmint.com/) julia/main Translation-en_US                                                                   
Ign [http://packages.linuxmint.com/](http://packages.linuxmint.com/) julia/upstream Translation-en                                            
Ign [http://packages.linuxmint.com/](http://packages.linuxmint.com/) julia/upstream Translation-en_US                                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                                                                                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en                                                                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                                                                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en                                                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US                                                   
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US                                                       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                                                                                 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en                                                          
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US                                 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en                                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US                                 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en                                      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg                                                  
Get:2 [http://packages.linuxmint.com](http://packages.linuxmint.com) julia Release [7,253B]                                                  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en                                                                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US                                                             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en                                                          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en                                                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US                                                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en                                                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US                                                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en                                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                                                                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                                                                           
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US                                 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en                                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US           
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en                                      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages                                                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages                                   
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) julia/main i386 Packages                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages                             
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) julia/upstream i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages               
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) julia/import i386 Packages                    
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) julia/main i386 Packages                      
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) julia/upstream i386 Packages
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) julia/import i386 Packages
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) julia/main i386 Packages
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) julia/upstream i386 Packages                                                                                      
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) julia/import i386 Packages                                                                                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg                                                                                              
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_US
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages
Fetched 7,451B in 24s (304B/s)
Reading package lists... Done
blanco@linuxmint ~ $ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 266 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
blanco@linuxmint ~ $ ^C
blanco@linuxmint ~ $ sudo dpkg --configure -a
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
blanco@linuxmint ~ $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 266 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
________________________________________________________

Apparently its some wireless driver defunct, 
I'm using dsl, got no problems with internet
But i still want to fix it, out of interest and for experience
Later got told to download the rest of the updates, when clicking the shield this came out:
________________________________________________________
Failed to fetch [http://packages.linuxmint.com/dists/julia/main/binary-i386/Packages.gz](http://packages.linuxmint.com/dists/julia/main/binary-i386/Packages.gz)  Unable to connect to packages.linuxmint.com:http:
Failed to fetch [http://packages.linuxmint.com/dists/julia/upstream/binary-i386/Packages.gz](http://packages.linuxmint.com/dists/julia/upstream/binary-i386/Packages.gz)  Unable to connect to packages.linuxmint.com:http:
Failed to fetch [http://packages.linuxmint.com/dists/julia/import/binary-i386/Packages.gz](http://packages.linuxmint.com/dists/julia/import/binary-i386/Packages.gz)  Unable to connect to packages.linuxmint.com:http:
Some index files failed to download, they have been ignored, or old ones used instead.
________________________________________________________

downloading the rest now.
Ladies & Gentleman, please explain to me the nature of this two errors
Thank you very much.....in advance.....implying i yearn for answers......implying ya'll must ANSWER :cool:

looonix4evAR:guitar:

---

