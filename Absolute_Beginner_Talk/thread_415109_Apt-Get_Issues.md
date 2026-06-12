---
title: "Apt-Get Issues"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by stescotty on 2007-04-20
Here it goes....be gentle...working on week 3 of running Ubuntu;

I have Edgy running for the last 3 weeks and things are great.  I see that that updates say that there is a Distro upgrade...Hooray.....Start the upgrade process and after a bit I get an error about "Failed to fetch [http://wine.budgetdedicated.com/apt/edgy/main/binary-i386/packages.gz](http://wine.budgetdedicated.com/apt/edgy/main/binary-i386/packages.gz) sub process gzip returned an error code (1)"


I go and remove the Respository from the sources.list and do an apt-get update and get the same error...

Is it trying to get the information from some place other that sources.list

I have rebooted and tried several things....even uninstalled Wine.

Am I missing anything?

Thanks

---

### Post by sad_iq on 2007-04-20
in a terminal type **sudo nano /etc/apt/sources.list** and put a # mark in front of that line...it should look like this after the edit: **#deb [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)..**.(whatever)

---

### Post by stescotty on 2007-04-20
I tried that but it's not there...like i said before...I removed that link from the repository but it's still using that website....is it someplace else?

Here is my Souces.list


deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
deb [http://flomertens.free.fr/ubuntu/](http://flomertens.free.fr/ubuntu/) edgy main main-all
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all
#AUTOMATIX REPOS END

It's even in the list.

Thansk

---

### Post by sad_iq on 2007-04-20
Ok...reading (verry little) the apt-get manpage...well...I'm clueless..however try **sudo apt-get clean** ("clean clears out the local repository of retrieved package files.") ! If it fails try aptitude (**sudo aptitude update**) as it handles dependencies better!!!

---

### Post by jfinkels on 2007-04-20
> **stescotty said:**
> I tried that but it's not there...like i said before...I removed that link from the repository but it's still using that website....is it someplace else?

Here is my Souces.list

[...]

If that is truly the contents of your "/etc/apt/sources.list" file (remember, capital and lowercase letters make a difference...) then I see no reason why aptitude should be looking in the wine repository...You had it in there before right? Why not try adding it back **in** to see what happens :)

---

### Post by Seisen on 2007-04-20
Remove the "ca" from all your repos and see if that helps.

---

### Post by stescotty on 2007-04-20
Ok....Put it back...still didn't work... did and apt-get update and got this......

stescotty@stescotty-laptop:~$ sudo apt-get update
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Translation-en_US                   
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Get:3 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]          
Ign [http://flomertens.free.fr](http://flomertens.free.fr) edgy Release.gpg                                 
Get:4 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg [191B]                  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Translation-en_US             
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]              
Get:6 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release.gpg [191B]                  
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy Release.gpg                         
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy Release.gpg                                  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/multiverse Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Translation-en_US               
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_US                
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Translation-en_US              
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Translation-en_US                       
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg                              
  Could not resolve 'us.archive.ubuntu.com'
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release.gpg [191B]             
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Translation-en_US           
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Translation-en_US                   
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                       
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Translation-en_US     
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Translation-en_US          
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US      
Ign [http://flomertens.free.fr](http://flomertens.free.fr) edgy/main Translation-en_US                      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Translation-en_US       
Get:8 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release [2961B]                     
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy Release                                      
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy Release                             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Packages                                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Packages                            
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Packages                       
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US               
  Could not resolve 'us.archive.ubuntu.com'
Ign [http://flomertens.free.fr](http://flomertens.free.fr) edgy/main-all Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US            
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources                          
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Packages                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Sources                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US      
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Packages                            
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Packages                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Sources                       
Get:9 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages [1261B]               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/multiverse Packages                      
99% [9 Packages gzip 0] [Waiting for headers] [Waiting for headers] [Connecting
gzip: stdin: not in gzip format
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                         
  Sub-process gzip returned an error code (1)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Packages                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Packages                    
Hit [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Packages                                
Hit [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Packages                       
Ign [http://flomertens.free.fr](http://flomertens.free.fr) edgy Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Packages              
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Sources               
Hit [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Packages                   
Hit [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Packages                            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/multiverse Packages              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Ign [http://flomertens.free.fr](http://flomertens.free.fr) edgy/main Packages                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US      
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                        
Ign [http://flomertens.free.fr](http://flomertens.free.fr) edgy/main-all Packages                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US        
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]              
Hit [http://flomertens.free.fr](http://flomertens.free.fr) edgy/main Packages                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US       
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                        
  Could not resolve 'us.archive.ubuntu.com'
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US         
Hit [http://flomertens.free.fr](http://flomertens.free.fr) edgy/main-all Packages                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                         
Get:13 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                     
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                    
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                             
Fetched 2973B in 10s (281B/s)                                                  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

Now I can't get 4 repositories......

What's up.....could it be the site.....but this doesn't make sense......if i remove the repositories from the sources.list I would assume it doesn't try to download it.  Why is it still trying to get a repository when the location doesn't exist. 

Getting a little fustrated.

---

### Post by antoniuk on 2007-04-20
On a nice side note, my source.list looked ugly and was causing my upgrade to fail for 7.04. This thread got me thinking... thanks, upgrading as I type

---

### Post by stescotty on 2007-04-20
Solved the issue....it seems that the software sources was the place the updates were getting their repositories from....not sources.list.  I removed the http;//wine.XXXXXXXXXX and now the upgrade will work.

I thought that Software sources got their list from sources.iist.....I was wrong.

Thanks for the input

---

