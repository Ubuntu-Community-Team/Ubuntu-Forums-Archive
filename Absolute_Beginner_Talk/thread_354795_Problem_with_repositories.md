---
title: "Problem with repositories"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by manuva on 2007-02-06
[B]Please advise!

i've tried to install both Wine and Flash 9 using the methods outlined in the [URL="http://www.psychocats.net/ubuntu/flash"[/URL] guide but it aint working for me.

Here is the Terminal results of my efforts:[/B]

[SIZE="1"][SIZE="1"]ben@ben-desktop:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
ben@ben-desktop:~$ gksudo gedit /etc/apt/sources.list

(gksudo:13074): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:13075): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(gedit:13075): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
ben@ben-desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Get:1 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]           
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US         
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                       
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                 
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US         
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages  
Get:6 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg [191B]     
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release
Fetched 6B in 6s (1B/s)                                                         
Reading package lists... Done
ben@ben-desktop:~$ sudo aptitude update && sudo aptitude install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Get:1 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]           
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US         
Get:2 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg [191B]                   
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_US                 
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                       
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                        
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages           
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Fetched 6B in 3s (2B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for flashplugin-nonfree
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
[/SIZE][/SIZE]

---

### Post by taurus on 2007-02-06
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

Otherwise, use this guide.

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by manuva on 2007-02-06
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main 

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

