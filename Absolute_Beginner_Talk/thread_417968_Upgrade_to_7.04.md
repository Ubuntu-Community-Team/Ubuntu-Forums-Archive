---
title: "Upgrade to 7.04"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by RogerDavis on 2007-04-22
Upgrading from 6.10 -> 7.04

I keep getting the same error (failed to fetch XXX, Sub-process bzip2 returned an error code (2)), about a dozen files named, check network and try again, and again, and again... now about 50 times or so.

One time it got all but about 6 files, but the next time it didn't find those, and back to about a dozen missing!

I'm using the update manager, I'm not up to the "renaming" method, and besides I've seen dire warnings about don't do it.

?) Is there a way to download a file or CD and upgrade from that, instead of depending on real time downloading? I'd rather keep my current setup than fight my way back to what I have done now. The upgrade to 6.10 kept it ok...

?) I'm told in an answer to "Download the "Alternate" Cd", but that seems just for machines with very little memory. Or maybe just wait a few days or weeks until the server use drops, assuming that is the problem?

?) Like the title says, Absolute Beginner... so :
- How do I put it in Synaptic as a CD Repository? Do I have to burn a CD, or can I just use a hard disk file, or is that what this means to do with the CD image on the hard drive?
- How do I start the upgrade with the downloaded file?  With the Update Manager, or?
- Afterward, how do I remove it from the list?
Thanks!

---

### Post by user1397 on 2007-04-22
> **RogerDavis said:**
> Upgrading from 6.10 -> 7.04

I keep getting the same error (failed to fetch XXX, Sub-process bzip2 returned an error code (2)), about a dozen files named, check network and try again, and again, and again... now about 50 times or so.

One time it got all but about 6 files, but the next time it didn't find those, and back to about a dozen missing!

I'm using the update manager, I'm not up to the "renaming" method, and besides I've seen dire warnings about don't do it.

?) Is there a way to download a file or CD and upgrade from that, instead of depending on real time downloading? I'd rather keep my current setup than fight my way back to what I have done now. The upgrade to 6.10 kept it ok...

?) I'm told in an answer to "Download the "Alternate" Cd", but that seems just for machines with very little memory. Or maybe just wait a few days or weeks until the server use drops, assuming that is the problem?

?) Like the title says, Absolute Beginner... so :
- How do I put it in Synaptic as a CD Repository? Do I have to burn a CD, or can I just use a hard disk file, or is that what this means to do with the CD image on the hard drive?
- How do I start the upgrade with the downloaded file?  With the Update Manager, or?
- Afterward, how do I remove it from the list?
Thanks!Yes, you can upgrade using an alternate CD.

You have to download it, burn it to a cd (with any cd burning application you want; also, make sure you burn it as an image, not as a data cd)  then put it in the drive, and add it as a repository using synaptic (it might even automatically pop up)

then you have to disable all your repositories except the cd one, and try going to the update manager, and clicking distribution upgrade (or something along those lines)

---

### Post by RogerDavis on 2007-04-22
Would this bypass the problem error (failed to fetch XXX, Sub-process bzip2 returned an error code (2)), about a dozen files named?
Thanks!

---

### Post by user1397 on 2007-04-22
> **RogerDavis said:**
> Would this bypass the problem error (failed to fetch XXX, Sub-process bzip2 returned an error code (2)), about a dozen files named?
Thanks!most likely, yes

---

### Post by zvacet on 2007-04-22
before you download alternate Cd (wich is good idea) try one more time with 
```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by RogerDavis on 2007-04-22
Didn't work:
=========================
roger@roger-desktop:~$ sudo aptitude update && sudo aptitude upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US        
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US              
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Fetched 8B in 5s (1B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
==========================================================
Ideas, comments, anyone?

---

### Post by PatM on 2007-04-22
I had the same problem.
Make sure you download and burn the **Alternat CD** and not the normal desktop cd.
I did this and it solved all the problems.
Just start Ubuntu and then insert the CD.
If you don't get the prompt to update type:

**Alt + F2**

Then:

**gksu "sh  /cdrom/cdromupgrade"**

---

### Post by Tundro Walker on 2007-04-22
You're gonna hate this, but...

**The short answer...**

Upgrading my Edgy to Feisty through Update Manager borked up my Ubuntu install.  I had to d/l the Feisty .iso, burn to CD and do a clean install.  After that, it's been working fine (for all of the 1 day that I've had it installed.)

**The long answer (or, "a Sunday with Ubuntu")...**

My Edgy install was tweaked a bit...

1) I used Automatix2 to add in Flash, mp3, Nvidia, etc support
2) I tweaked a few config files here and there
3) I uninstalled the "ubuntu-desktop" meta package so I could remove programs I didn't want to use

In trying the upgrade, I knew it would require me to have "ubuntu-desktop" meta package reinstalled, so I did that and reinstalled all of its associated packages which I previously bumped off.

The upgrade asked its questions, and d/l'ed the 1000+ files ok (over the course of 8 hrs...wow), and seemed to install ok.  It noticed a few config files were tweaked, and asked if I wanted to replace them with its defaults.  To be safe, I said "yes".

All said and done, I rebooted, and Ubuntu would hang during the boot-up splash screen, with the orange bar showing the intitial sliver of color, but not progressing at all.  Others were getting this error, and it seemed related to either X Server or Xorg or Nvidia.  

I attempted a tweak by putting the line "piix" in the file...

```
/etc/initramfs-tools/modules
```...because [this Launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864") said that might help.  Some others said they were having problems with TTY loading.  Mine seemed to be X server related, because when I looked at the Xorg log, it seemed to hang when trying to detect my Nvidia card.

Anyways, I got tired of trying to find some way to patch it manually, so gave up and d/l'ed the .iso, which I saved on the /tmp folder of my borked Feisty upgrade.  It took like 30 min to d/l on my Broadband connection (vs. the 8 hours for upgrading).  But, I was stuck with on boot-able OS on my comp.  So, I tried a few LiveCD's, but I only have 1 CDROM drive (which is also my burner), and none of the LiveCD's would let me eject and insert my blank CD to burn the ISO.  I extracted the ISO files to a USB flash stick, but my computer didn't want to boot from it.  

So, I basically booted LiveCD Edgy Eft, re-partitioned my drive to put a temp install of it on, then when I could boot into the temp install on my HDD, I was able to burn the ISO image from my borked Feisty, and finally reboot to it's LiveCD and install Feisty from it.  (Seriously...this whole operation took me all night waiting for the ugrade to happen, all morning trying to figure out if I could fix it manually, then the rest of Sunday d/l'ing and installing Feisty from LiveCD...after trying to figure out a better way than simply re-installing Edgy again in another partition....c'est la vie.)

**So, here's the suggestions...**

1) Back up all your necessary stuff to start (that's a no-brainer...I keep 1 folder with critical stuff, so I just dumped it to a USB flash stick before upgrading and I was set).

2) Even if you're gonna try an upgrade, d/l and burn the Feisty .iso FIRST...just in case the upgrade doesn't work and you need to do a clean install (which is always easier...heck, the dev's can't anticipate all the crap folks do to their installed software to facilitate 100% upgrade success, so cut them some slack)

3) Just to be safe, burn a copy of the latest Edgy .iso, too...because a few folks are having problems with a clean Feisty install, much less an upgrade.

4) Be nice to the dev's.  Feisty fixed some bugs, but they also added new features (Compiz and other things), and whenever you add new stuff to an upgrade, there's the potential to add new bugs.   They're trying to make Ubuntu look and function as nice as Vista (and then some!), and they don't have as many resources as Microsoft.  So, cut them some slack.  They listen to feedback, and are responsive.  Be thankful for the work they do, and show your appreciation in any comments of feedback you send them.

All in all, I'm really, really impressed with what they've done so far.  Sure, the upgrade was shakey (which could probably be attributed to me using Automatix2...which I was warned about and take full responsibility in using).  But, I have YET for a CLEAN INSTALL of the Ubuntu versions I've used (Dapper, Edgy, now Feisty) to blow up on me.  It's always been a quick 30 min installation from LiveCD, and maybe 10-15 mins of updates, depending on how old the .iso is.

Outstanding work, Everyone!

---

