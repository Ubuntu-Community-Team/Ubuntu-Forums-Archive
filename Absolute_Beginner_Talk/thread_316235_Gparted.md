---
title: "Gparted"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by say592 on 2006-12-10
I googled like there was no tomorrow, but I couldnt find a version that I would just install.... (also I may need intallation help)

---

### Post by aysiu on 2006-12-10
Just paste this command into the terminal: ```
sudo aptitude update && sudo aptitude install gparted gksu
``` Then it should be installed.

---

### Post by say592 on 2006-12-10
All at once? And will it just download it online? So i put that whole string in at once and its good? Ill try, but if thats not what ya meant let me know.....

---

### Post by say592 on 2006-12-10
This is what I got:

joshua@joshua-desktop:~$ sudo aptitude update && sudo aptitude install gparted gksu
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                       
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                     
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                    
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US             
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                              
Get:4 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US       
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US         
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release.gpg                                  
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Translation-en_US                       
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US        
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                              
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                             
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                    
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                        
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US                
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US        
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources              
Fetched 10B in 10s (1B/s)                                                       
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  libcairomm-1.0-1 libgtkmm-2.4-1c2a 
The following NEW packages will be installed:
  gparted libcairomm-1.0-1 libgtkmm-2.4-1c2a 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1466kB of archives. After unpacking 5808kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main libcairomm-1.0-1 1.2.0-0ubuntu1 [40.5kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main libgtkmm-2.4-1c2a 1:2.10.2-0ubuntu1 [1104kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main gparted 0.2.5-1.1ubuntu11 [322kB]  
Fetched 1466kB in 8s (178kB/s)                                                  
Selecting previously deselected package libcairomm-1.0-1.
(Reading database ... 106378 files and directories currently installed.)
Unpacking libcairomm-1.0-1 (from .../libcairomm-1.0-1_1.2.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgtkmm-2.4-1c2a.
Unpacking libgtkmm-2.4-1c2a (from .../libgtkmm-2.4-1c2a_1%3a2.10.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package gparted.
Unpacking gparted (from .../gparted_0.2.5-1.1ubuntu11_i386.deb) ...
Setting up libcairomm-1.0-1 (1.2.0-0ubuntu1) ...

Setting up libgtkmm-2.4-1c2a (2.10.2-0ubuntu1) ...

Setting up gparted (0.2.5-1.1ubuntu11) ...

joshua@joshua-desktop:~$

What now?

---

### Post by bodhi.zazen on 2006-12-10
You are good to go.

In a terminal type```
sudo gparted
``` or check your menu....

---

### Post by say592 on 2006-12-10
Well its not in menu, so how could I add it? But it did show up with that code!

---

### Post by aysiu on 2006-12-10
Well, first of all, if you want it to be in the menu, you should use the command ```
gksudo gparted
``` not ```
sudo gparted
``` Read more about that here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Sometimes you can get it to show up by just refreshing the menu ```
killall gnome-panel
``` Other times, you can create a menu entry by right-click the menu, selecting **Edit menus** and then creating a new item with the command and an appropriate icon. The command, again, is ```
gksudo gparted
```

---

### Post by ceejay on 2007-12-09
Hi

slightly different problem here. I've just done a clean install of Ubuntu 7.10 on a brand new machine (home made!!!). It has 3 SATA disks all of which are recognised as devices. But only one was formatted during the install process.

OK, so I'm told I need to use gparted to move on to my other discs.  I tried add/remove applications but the entry for gparted says "Gnome Partition Editor cannot be installed on your computer type (i386)".

I also tried the aptitude command line referenced earlier in the thread but this failed with "No candidate version found for gparted".

Any suggestions?

The system has Intel Core Duo CPU on an Intel motherboard.

TIA.
Ceejay

---

### Post by ceejay on 2007-12-09
Update: well, I went to use Synaptic Package manager instead, marked gparted to load - and it downloaded and worked fine.

Problem solved, though any explanation would be very welcome.

Ceejay

---

### Post by uidb4056 on 2007-12-09
Have you installed Ubuntu x64 or i386? if you installed x64 may be you don't have the proper software sources selected.

In any case the install CD/DVD you have used must have gparted on it, have you a Live CD/DVD install or Alternate CD/DVD install?

---

### Post by ceejay on 2007-12-09
> **uidb4056 said:**
> Have you installed Ubuntu x64 or i386? if you installed x64 may be you don't have the proper software sources selected.


I don't remember being asked!  Uname -a reports "Linux aristotle 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux" - does that mean I have installed the x64 version?

If I don't have the proper sources selected - how would I know, and how would I fix that?

> 
In any case the install CD/DVD you have used must have gparted on it, have you a Live CD/DVD install or Alternate CD/DVD install?

You'd think so. But it didn't include the installation of this package.

Anyway - I think this post crossed with my last - I have now downloaded something and its busy working on my disks as I write: but there is definitely something dodgy about this package, it has crashed several times already!

All help and guidance very much appreciated....

Ceejay

---

### Post by thelatinist on 2007-12-09
First of all, this thread is over a year old.  Next time please start a new thread.

Second: Gutsy should include Gparted under System > Administration > Partition Manager.  Did you try looking there first?

---

### Post by ceejay on 2007-12-09
> **thelatinist said:**
> First of all, this thread is over a year old.  Next time please start a new thread.

Second: Gutsy should include Gparted under System > Administration > Partition Manager.  Did you try looking there first?

Sorry about the old thread.

Yes, I did look there, it was missing.  Trying to install it using add/remove programs failed, as did aptitude from the command line.  

But it did install - and is now present in the menu - having installed from synaptic package manner.

So I have two questions left, as per my earlier posts:

1 - why did one method fail and another work?

2 - the software I've got is very flaky and keeps crashing, which makes me think that I've downloaded something that really isn't compatible with my system (which would be a very good reason for add/remove applications for refusing the download!)

Guidance welcome.

---

### Post by ntu on 2007-12-09
Gparted is certainly in my Feisty cd. I have used it (when I used the Feisty cd as a live cd) to change partition sizes in my Feisty installation.

Just to clarify: I do not install gparted from the live cd. I find it simpler to do it all from gparted in the live cd. This way I can do operations on the partition that Ubuntu is installed on which cannot be done if gparted is also installed in that partition.

---

### Post by bodhi.zazen on 2007-12-10
Just for clarification :

1. gparted IS on the LIVE (Desktop cd) but is NOT installed by default.

2. @ceejay : I don not know why you had problems installing gparted. After you  install software you may need to log out and back in to update your menu. If that fails then run "sudo update-menus".

3. +1 on managing partitions from a live CD (which is probably why gparted is not installed by default).

---

### Post by ronmarley1 on 2007-12-10
> **bodhi.zazen said:**
> 
3. +1 on managing partitions from a live CD (which is probably why gparted is not installed by default).

Just to throw in my $.02...
Another option is the gParted LiveCD.  You can download the iso here: [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
and create a bootable CD.  It boots a little faster than the Ubuntu Live CD, so if all you are looking to do is edit partitions, it's a good choice.  However, as bodhi.zazen wrote, the Ubuntu Live CD works also.

---

