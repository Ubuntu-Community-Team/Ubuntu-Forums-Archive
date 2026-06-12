---
title: "Synaptic package install"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by newbie59 on 2007-03-11
I've tried to use synaptic in the past and the programs I've installed seem to be on my system (cause I can uninstall them), they're just not in the applications drop down menu where I can see to use them. Can someone explain why this is.
Example: I just installed kmail and the openPGP addon for thunderbird. I can't find kmail in the apps dropdown but the PGP button is installed in thunderbird.
How would I find where kmail is and put in the Apps dropdown or my desktop so I can easily access it.
Please keep in mind I do have 12 years Windows experience and I am finding alot of these "issues" in Linux somewhat easy to understand on a basic level (the install process is very simple). But from there, I'm pure virgin newbie and don't yet understand.
Any help is greatly appreciated. Thanks.

---

### Post by STREETURCHINE on 2007-03-11
can you post the out put of 

   ```
cat /etc/apt/sources.list
```

---

### Post by newbie59 on 2007-03-11
I don't know where to put the code for output

---

### Post by SurR3AL on 2007-03-11
type that in the terminal and post the output here :)

---

### Post by tallman9 on 2007-03-11
it should appear in the system menu...but maybe it's just hidden.
right click on the menu and choose edit menu.

---

### Post by newbie59 on 2007-03-11
I did a cut and paste in the terminal and this is what I got:
gracyrus59@gracyrus59-desktop:~$ cat /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END
gracyrus59@gracyrus59-desktop:~$

---

### Post by STREETURCHINE on 2007-03-11
un hash your 

 # deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


take the # from the front of all of them then

     ```
sudo apt-get update 
``` 


then reinstall your packages

---

### Post by newbie59 on 2007-03-11
I see menu layout and menu's and tool bars but not sure what I should do

---

### Post by newbie59 on 2007-03-11
I used: sudo apt-get update
and this is what I got:
gracyrus59@gracyrus59-desktop:~$ sudo apt-get update
Password:
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                     
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages                              
Get:1 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]          
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US        
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US            
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US        
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US      
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US        
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US             
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US               
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US         
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US       
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                            
Get:9 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                      
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                    
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                            
Get:10 [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages [737B]                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                     
99% [Waiting for headers] [Connecting to wine.lowvoice.nl]bzip2: (stdin) is not a bzip2 file.
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages        
  Sub-process bzip2 returned an error code (2)
Get:11 [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages [737B]                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources                       
99% [11 Packages bzip2 0] [Waiting for headers] [Connecting to wine.lowvoice.nlbzip2: (stdin) is not a bzip2 file.
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                             
  Sub-process bzip2 returned an error code (2)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages    
Get:12 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release.gpg [191B]    
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Translation-en_US
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                 
Fetched 12B in 6s (2B/s)                                                       
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.bz2](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.bz2](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_edgy-commercial_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
gracyrus59@gracyrus59-desktop:~$ 

what do I do from here

---

### Post by STREETURCHINE on 2007-03-11
ok in terminal type this or copy and paste it

    ```
gksudo gedit /etc/apt/sources.list
```

and delete the #from in front of all the lines starting with deb.


then save and exit then update with the command in terminal

```
sudo apt-get update
```

---

### Post by newbie59 on 2007-03-11
I don't know what unhash means

---

### Post by STREETURCHINE on 2007-03-11
this is the hash    #    just remove it from the front of the lines that start with deb

---

### Post by newbie59 on 2007-03-11
gksudo gedit /etc/apt/sources.list

got me this: (gedit:9456): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by newbie59 on 2007-03-11
I'm sorry but I'm not seeing any numbers

---

### Post by STREETURCHINE on 2007-03-11
thats ok everyone gets that it nis a bug that hasnt been fixed

---

### Post by STREETURCHINE on 2007-03-11
> **newbie59 said:**
> I'm sorry but I'm not seeing any numbers

you shouldnot see numbers

---

### Post by newbie59 on 2007-03-11
Ya'know, I'm just gonna uninstall kmail and leave Synaptic alone until I get further along in the learning curve

---

### Post by STREETURCHINE on 2007-03-11
just post a copy of your source list

```
gksudo gedit /etc/apt/sources.list
```

i will edit it here for you and you can copy and past it to your source list

---

### Post by STREETURCHINE on 2007-03-11
just be patient and take things one step at a time,you will get a lot of usefull help here

---

### Post by newbie59 on 2007-03-11
gracyrus59@gracyrus59-desktop:~$ gksudo gedit /etc/apt/sources.list

(gedit:9920): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
gracyrus59@gracyrus59-desktop:~$ 


This is what I got

---

### Post by newbie59 on 2007-03-11
I understand I will and am getting help 
It is just very frustrating 
I'm out of my comfort zone with this

---

### Post by newbie59 on 2007-03-11
Thank everyone for your help

---

### Post by STREETURCHINE on 2007-03-11
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END

ok you can open your source list and make it look like this jusy go line by line or delete the source list and copy and paste this one in save and update


use to open 

```
gksudo gedit /etc/apt/sources.list
```

that will allow you to edit but dont forget to hit save before you close

---

### Post by tallman9 on 2007-03-11
I don't really understand why you think there is a problem in his sources.list
He told that he installed everything successfully from synaptic, but doesn't see the program in the menu.
try this:
sudo apt-get install menu
then open a terminal and type:
update-menus
this should help...you can also try my first recomendation:
right click on the ubuntu logo and choose something like "edit menu" or "menu editor"
then enable the hidden programs.

---

### Post by STREETURCHINE on 2007-03-11
i was just trying to rule out a dependancy problem,so that is why i asked to see the source.list some programs need stuff from differant repos and if they are not all enabled then you have trouble 

i was not saying there was a problem there it was just somewhere to start

the basis of all trouble shooting start with the easy stuff and work through it till you eventually find the solution

---

### Post by leogibson on 2007-03-12
im having this same problem especially with the following:

Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") edgy/main Packages
  Sub-process gzip returned an error code (1)

---

