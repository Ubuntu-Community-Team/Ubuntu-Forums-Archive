---
title: "made a mistake with sudo password and now cannot work as an administrator"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by drshrikant on 2007-05-19
i am extremely happy with ubuntu but have landed up myself in a mess... tempted to try out the sudo apt -get via the terminal and when prompted for password i typed my user login password but since then cannot add or remove applicatns. very worried. evn no cd is playin jus showin error unable to load media.

---

### Post by aysiu on 2007-05-19
Try this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by drshrikant on 2007-05-19
this luks v complicated.. but helpful.. thanks a lot...

---

### Post by drshrikant on 2007-05-19
is there not a gui type solution to this... the loggin in as root n den editing files is v difficult.. could not do that properly.. might mess up sumthin else..

---

### Post by drshrikant on 2007-05-19
sumone plz help me with troubleshooting sudo the gui way.. or atleast with straight on instructions   
as to how to go about it.. please ... i am absolutely ignorant abt the cli

---

### Post by aysiu on 2007-05-19
Maybe we can make it a little simpler.

First, let's diagnose the problem.

Can you post (just copy and paste) the output of this terminal command? ```
sudo apt-get update
``` Exactly what errors do you get?

---

### Post by Happy_Man on 2007-05-19
sudo apt-get shouldn't mess up your sudoers file.... quite odd.

---

### Post by drshrikant on 2007-05-19
typin sudo apt-get update in terminal is askin me for a password

---

### Post by icechen1 on 2007-05-19
> **drshrikant said:**
> typin sudo apt-get update in terminal is askin me for a password

tape your password when it ask so
or you could try gksudo <command here> because is more user friendly

---

### Post by aysiu on 2007-05-19
Okay. Please don't summarize what happens. Just copy and paste *exactly* what appears. And include what happens after you try to enter your password.

---

### Post by drshrikant on 2007-05-19
this might irritate you.. sorry... but by my password do you mean the one that i type at start up?? cuz i know no other password

---

### Post by aysiu on 2007-05-19
> **drshrikant said:**
> this might irritate you.. sorry... but by my password do you mean the one that i type at start up?? cuz i know no other password
Yes.

---

### Post by drshrikant on 2007-05-19
shrikant@shrikant-desktop:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_IN          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_IN    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_IN     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_IN   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                        
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Translation-en_IN                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Translation-en_IN           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Translation-en_IN             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Translation-en_IN           
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Translation-en_IN         
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Translation-en_IN   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release                                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Packages                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Sources                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Sources                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Sources                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Sources                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Sources             
Fetched 3B in 8s (0B/s)                                                        
Reading package lists... Done
shrikant@shrikant-desktop:~$

---

### Post by aysiu on 2007-05-19
That looks good to me.

So what's this business about not being able to install new packages? What are you trying to install?

Can you post the output of ```
sudo apt-get install *packagename*
``` where *packagename* is the name of the software package you're trying to install?

---

### Post by drshrikant on 2007-05-19
if this means there is no problem then why can't i add or remove any application or access update manager?? and if there is a prob what do i do.. please help

---

### Post by Happy_Man on 2007-05-19
To start, do as aysiu says... try typing in 
```
sudo apt-get install *packagename*
```

---

### Post by drshrikant on 2007-05-19
shrikant@shrikant-desktop:~$ sudo apt-get install kleansweep
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Segmentation fault (core dumped)
shrikant@shrikant-desktop:~$

---

### Post by aysiu on 2007-05-19
Can you try this? ```
sudo apt-get clean
sudo apt-get update
sudo apt-get install kleansweep
``` and past back any errors you encounter.

---

### Post by drshrikant on 2007-05-19
shrikant@shrikant-desktop:~$ sudo apt-get clean
shrikant@shrikant-desktop:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_IN        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Translation-en_IN                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Translation-en_IN           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Translation-en_IN             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Translation-en_IN           
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Translation-en_IN         
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Translation-en_IN   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release                                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Packages                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Sources                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Sources                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Sources                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Sources                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Sources             
Fetched 3B in 8s (0B/s)                                                        
Reading package lists... Done
shrikant@shrikant-desktop:~$ sudo apt-get install kleansweep
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Segmentation fault (core dumped)
shrikant@shrikant-desktop:~$

---

### Post by aysiu on 2007-05-19
Hm. That stinks.

Two more things to try: ```
sudo apt-get -f install
``` *-f* will try to fix any broken packages.

You can also try installing a different package (something other than *kleansweep*) and see if you still geta  segmentation fault. If you do, then it's definitely something wrong with *apt-get* in general. If you don't, then there's something wrong with the *kleansweep* package.

---

### Post by drshrikant on 2007-05-19
shrikant@shrikant-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Segmentation fault (core dumped)
shrikant@shrikant-desktop:~$ sudo apt-get install KmPlot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package KmPlot
shrikant@shrikant-desktop:~$ sudo apt-get install kmplot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Segmentation fault (core dumped)
shrikant@shrikant-desktop:~$

---

### Post by aysiu on 2007-05-19
Okay. We're almost at a deadend. I've been Googling around trying to find someone with a similar problem, and I can't find anything.

Does *aptitude* exhibit the same behavior? In other words, do you still get a segmentation fault if you do this? ```
sudo aptitude update
sudo aptitude install kmplot
```

---

### Post by drshrikant on 2007-05-19
t (core dumped)
shrikant@shrikant-desktop:~$ sudo aptitude update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_IN         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_IN   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_IN     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_IN   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                        
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Translation-en_IN            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Translation-en_IN              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Translation-en_IN            
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release.gpg [191B]            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Translation-en_IN          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Translation-en_IN    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release                                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Packages                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Packages                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Sources                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Sources                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Packages                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Sources                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Packages                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Sources                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Packages                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Packages             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Sources                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Sources              
Fetched 3B in 8s (0B/s)                                                         
Reading package lists... Done
shrikant@shrikant-desktop:~$ sudo aptitude install kmplot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Uncaught exception: apt.cc:466: void surrounding_or_internal(const pkgCache::DepIterator&, pkgCache::DepIterator&, pkgCache::DepIterator&): Assertion "found" failed.
shrikant@shrikant-desktop:~$

---

### Post by drshrikant on 2007-05-19
also got this.. from launchpad where i had clicked on problem from my file menu..
ProblemType: Bug
Architecture: i386
Date: Sat May 19 19:59:36 2007
DistroRelease: Ubuntu 7.04
ExecutablePath: /usr/bin/nautilus
Package: nautilus 1:2.18.1-0ubuntu1
PackageArchitecture: i386
ProcCmdline: nautilus --no-default-window --sm-client-id default2
ProcCwd: /home/shrikant
ProcEnviron:
 PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
 LANG=en_IN
 SHELL=/bin/bash
SourcePackage: nautilus
Uname: Linux shrikant-desktop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

** Affects: Ubuntu
    Importance: Undecided
        Status: Unconfirmed

--
add or remove applications not working
[https://bugs.launchpad.net/bugs/115619](https://bugs.launchpad.net/bugs/115619)
You received this bug notification because you are a direct subscriber
of the bug.

---

### Post by drshrikant on 2007-05-19
any hope???

---

### Post by drshrikant on 2007-05-19
can i re install ubuntu from the cd...

---

### Post by drshrikant on 2007-05-19
is there no solution ???

---

