---
title: "Upgrade from Edgy to Feisty"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by davesmith on 2007-05-31
Hallo

I have been trying to upgrade from 6.10 to 7.04 using Update Manager, unfortunately without success.

Apparently i have a problem with python and the upgrade aborted, but not before about 70% of my files had been updated from edgy to feisty

Also...Update Manager is now not working, so i tried to use the terminal..... now i have un-met dependencies, here is the terminal output

<sudo aptitude update>

The following packages have unmet dependencies:
  hplip: Depends: hplip-data (< 1.6.9.1) but 1.7.3-0ubuntu1 is installed.
         Depends: python (< 2.5) but 2.5.1-0ubuntu3 is installed.
  python-glade2: Depends: python-gtk2 (= 2.10.3-0ubuntu3) but 2.10.4-0ubuntu3 is installed.

so now i cant update anything!!

can anyone help me sort this mess out?

all i wanted to do was perform a routine upgrade....

Davesmith

---

### Post by Cypher on 2007-05-31
In the terminal can you type
```

sudo apt-get update -f

```
and see what happens?

---

### Post by davesmith on 2007-05-31
thanks

the output of <sudo apt-get update -f> is...

<Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                 
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_US             
Get:4 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports Release.gpg [191B]         
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/main Translation-en_US       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/restricted Translation-en_US 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/universe Translation-en_US   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/multiverse Translation-en_US 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US    
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports Release          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/main Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/restricted Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/multiverse Sources
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages>

then, i run <sudo aptitude upgrade> i get

<sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages have unmet dependencies:
  hplip: Depends: hplip-data (< 1.6.9.1) but 1.7.3-0ubuntu1 is installed.
         Depends: python (< 2.5) but 2.5.1-0ubuntu3 is installed.
  python-glade2: Depends: python-gtk2 (= 2.10.3-0ubuntu3) but 2.10.4-0ubuntu3 is installed.>

ok, so what&#347; broken?

---

### Post by davesmith on 2007-06-01
having now successfully upgraded to 7.04, i am still having problems with unmet dependencies

the output of <sudo apt-get upgrade> is

<The following packages have unmet dependencies:
  hplip: Depends: hplip-data (< 1.6.9.1) but 1.7.3-0ubuntu1 is installed
         Depends: python (< 2.5) but 2.5.1-0ubuntu3 is installed
  python-glade2: Depends: python-gtk2 (= 2.10.3-0ubuntu3) but 2.10.4-0ubuntu3 is installed
E: Unmet dependencies. Try using -f.>

can anyone help me resolve these un-met dependencies?

thanks in advance

---

### Post by davesmith on 2007-06-01
here is the output of

<cat /etc/apt/sources.list>

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
#AUTOMATIX REPOS END

---

