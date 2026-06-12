---
title: "Synaptic Package Manager Won't Load!"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by bamf on 2006-09-18
Hello,

Whenever I try to open Synatpic, it asks me for my password then thinks and then just doesn't load up. I don't know what I did to make this happen. I can however go into to terminal and run apt-get update and upgrade and it works just fine with 0 errors. Just for some reason I can't load it in the GUI! Any help would be awesome this has been bugging me.

Thanks,
Kiley

---

### Post by aktiwers on 2006-09-18
That is normal. Just type in the password you use when you logon to ubuntu.

If I missunderstood you, take a look at my old thread from when my Synaptic was broken. There is a lot of useful commands, suggested by other members, that might fix your problem.

Edit:
Heh, forgot to post the link ](*,)
[http://www.ubuntuforums.org/showthread.php?t=252762](http://www.ubuntuforums.org/showthread.php?t=252762)

---

### Post by bamf on 2006-09-19
Thanks for posting that link.

Here's what was happening... I would try to open synaptic I would then put in  my password then it would think... then just act like nothing ever happened and not open up synaptic...

I downloaded that deborphan program just cause it looked cool and deleted some repositories, all of which were some stupid gstreamer thing and then tried to open up Synaptic again, this time it didnt even prompt me for my password! Help?? I don't want to reinstall! I got my tablet and everything working perfectly.

Heres what happenes when I sudo apt-get update and sudo apt-get upgrade in terminal...

> kiley@lilbamf:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:1 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]                       
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages                              
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release                                    
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]                    
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release                                 
Get:3 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]        
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg                                    
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]                      
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [189B]             
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                     
Get:6 [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg [189B]                         
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]              
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages                           
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages                              
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages               
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release                                      
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release                 
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources                        
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release                                        
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 8B in 2s (3B/s)  
Reading package lists... Done



> Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


It doesn't seem like to much is wrong to me? Why won't synaptic open?

Thanks!
Kiley

---

### Post by Obor on 2006-09-19
What happens when you run 
```
gksudo synaptic
```
in the terminal? Maybe it will throw out some errors.

---

### Post by goatflyer on 2006-09-19
Sorry to barge in, but what is the last line output of
```

sudo dpkg --list synaptic

```

My working synaptic shows this:
```

ii  synaptic       0.57.8ubuntu11 Graphical package manager

```

The "ii " (ii and a space) means no errors with your synaptic.

I won't pretend to be an expert but I suppose if anything is wrong with your synaptic you could try:
```

sudo aptitude reinstall synaptic

```

Note that is aptitude, not apt-get

Good luck.

---

### Post by bamf on 2006-09-19
Hey, thanks for the responses...

When I type gksudo in terminal it does the same thing... it opens up the password box then just never loads.

When I type sudo dpkg --list synaptic I get this...

> kiley@lilbamf:~$ sudo dpkg --list synaptic
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  synaptic       0.57.8ubuntu11 Graphical package manager


So I tried the sudo aptitude reinstall synaptic

> kiley@lilbamf:~$ sudo aptitude reinstall synaptic
Reading package lists... Done
Building dependency tree... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be REINSTALLED:
  synaptic 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 1035kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main synaptic 0.57.8ubuntu11 [1035kB]
Fetched 1035kB in 5s (180kB/s)                       
(Reading database ... 90881 files and directories currently installed.)
Preparing to replace synaptic 0.57.8ubuntu11 (using .../synaptic_0.57.8ubuntu11_i386.deb) ...
Unpacking replacement synaptic ...
Setting up synaptic (0.57.8ubuntu11) ...


I tried to run Synaptic after this and it was still stuck in the same place, so I ran sudo dpkg --list synaptic again and got the exact same message....

> kiley@lilbamf:~$ sudo dpkg --list synaptic
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  synaptic       0.57.8ubuntu11 Graphical package manager


Any ideas? I've been searching the forums left and right for answers!

Thanks,
Kiley

---

