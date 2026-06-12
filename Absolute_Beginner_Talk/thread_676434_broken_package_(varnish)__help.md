---
title: "broken package (varnish)  help"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by nynoah on 2008-01-23
When I run update I get an error.  Can anyone tell me what I need to do to resolve this before it snowballs into a locked system on me.   The package name is Varnish.  I tried reloading it in synaptic, that did not work.  I tried to remove it, that did not work.

Here is a copy from my Terminal  

> noah@noah-desktop:~$ sudo aptitude remove kdelibs5 kde4base-data kde4libs-data
[sudo] password for noah:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following partially installed packages will be configured:
  varnish 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up varnish (1.0.3-2) ...
Starting HTTPd accelerator: /usr/bin/ld: crti.o: No such file: No such file or directory
collect2: ld returned 1 exit status
pclose=256
Internal error: GCC returned 0x0100
invoke-rc.d: initscript varnish, action "start" failed.
dpkg: error processing varnish (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 varnish
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
noah@noah-desktop:~$ 



---

### Post by nynoah on 2008-01-23
I just ran     sudo dpkg--configure -a  

and then this and I still get the error.............

> noah@noah-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/multiverse Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-en_US                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release                                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release                                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/multiverse Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/multiverse Sources                          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/multiverse Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/multiverse Sources                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Fetched 193B in 1s (159B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up varnish (1.0.3-2) ...
Starting HTTPd accelerator: /usr/bin/ld: crti.o: No such file: No such file or directory
collect2: ld returned 1 exit status
pclose=256
Internal error: GCC returned 0x0100
invoke-rc.d: initscript varnish, action "start" failed.
dpkg: error processing varnish (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 varnish
E: Sub-process /usr/bin/dpkg returned an error code (1)
noah@noah-desktop:~$ 


---

### Post by nynoah on 2008-01-23
does anyone have any sugestions?  HELP?

---

### Post by macogw on 2008-01-23
do either of these help?
sudo aptitude purge varnish
sudo apt-get install -f

---

### Post by nynoah on 2008-01-24
Thanks Macgow........I tried those commands and still got an error.  I will try them with my internet browser shut down and see what happens.  But here is the output from the Terminal.


> noah@noah-desktop:~$ sudo aptitude purge varnish
[sudo] password for noah:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages will be automatically REMOVED:
  varnish{p} 
The following packages will be REMOVED:
  varnish{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 750kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 174611 files and directories currently installed.)
Removing varnish ...
Stopping HTTPd accelerator: invoke-rc.d: initscript varnish, action "stop" failed.
dpkg: error processing varnish (--purge):
 subprocess pre-removal script returned error exit status 1
Starting HTTPd accelerator: /usr/bin/ld: crti.o: No such file: No such file or directory
collect2: ld returned 1 exit status
pclose=256
Internal error: GCC returned 0x0100
invoke-rc.d: initscript varnish, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 varnish
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
noah@noah-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up varnish (1.0.3-2) ...
Starting HTTPd accelerator: /usr/bin/ld: crti.o: No such file: No such file or directory
collect2: ld returned 1 exit status
pclose=256
Internal error: GCC returned 0x0100
invoke-rc.d: initscript varnish, action "start" failed.
dpkg: error processing varnish (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 varnish
E: Sub-process /usr/bin/dpkg returned an error code (1)
noah@noah-desktop:~$ 


---

### Post by nynoah on 2008-01-24
can someone please help me.  What could be causing this.  I can not download programs now because this Varnish error keeps on coming up all the time.

Noah

---

### Post by RomeReactor on 2008-01-24
Hi. Try:
```
sudo dpkg --remove --force-remove-reinstreq varnish
```

---

### Post by nynoah on 2008-01-24
I think that worked.....It did not give me an error code

---

### Post by Slipmyknot101 on 2008-02-13
For those who still have problems removing varnish after following what is available before this post, please try the following because it worked for me:

1. Open Synaptic Package Manager
2. Search for 'varnish' and locate it.
3. Right click on 'varnish' package.
4. Click 'properties' in the popup menu.
5. Click tab 'installed files' on the 'properties' popup menu.
6. Open command prompt.
7. Type 'sudo nautilus' (if you don't use nautilus, replace 'sudo *nautilus*' with 'sudo [whatever your file manager is]'.
8. When Nautilus (or your other file manager) opens, navigate to each listed instance of where the file is installed.
9. Make sure you remove all instances of the file but pay particular attention to making sure instances within etc/etc/init.d, and /etc are removed.
10. To check the system to see if there are any missed instances, use "whereis varnish" in the command prompt, but this step is not vital.
11. Close Synaptic Package Manager and reopen it once again.
12. Search for "varnish", and right click it again. 
13. Click "remove all" or "completely uninstall" or whatever suggests a complete and total annihilation of this package and click it.
14. Click 'apply' and it may very well work for you.

Thanks. Hope this helps!

---

