---
title: "[SOLVED] Problem installing Software:dpkg was interrupted"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Google Spider on 2008-03-16
Hi,

I am haveing problems installing software

```

abhishek@edubuntu:~$ sudo apt-get update
[sudo] password for abhishek:
Ign cdrom://[APTonCD for ubuntu gutsy - i386 (2008-01-09 12:13) CD1]  Release.gpg
Ign cdrom://[APTonCD for ubuntu gutsy - i386 (2008-01-09 12:13) CD1]  Translation-en_IN
Ign cdrom://Edubuntu 7.10 _Gutsy Gibbon_ - Release i386 Binary-1 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Edubuntu 7.10 _Gutsy Gibbon_ - Release i386 Binary-1 (20071016) gutsy/restricted Translation-en_IN
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_IN
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Ign cdrom://[APTonCD for ubuntu gutsy - i386 (2008-01-09 12:13) CD1]  Release  
Get:1 http://in.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://in.archive.ubuntu.com gutsy/main Translation-en_IN                  
Get:2 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_IN               
Ign http://in.archive.ubuntu.com gutsy/restricted Translation-en_IN            
Ign http://in.archive.ubuntu.com gutsy/universe Translation-en_IN              
Ign http://in.archive.ubuntu.com gutsy/multiverse Translation-en_IN            
Hit http://in.archive.ubuntu.com gutsy Release                                 
Get:3 http://archive.canonical.com gutsy Release [6998B]                       
Hit http://in.archive.ubuntu.com gutsy/main Packages                           
Hit http://in.archive.ubuntu.com gutsy/restricted Packages                     
Hit http://in.archive.ubuntu.com gutsy/universe Packages                       
Hit http://in.archive.ubuntu.com gutsy/multiverse Packages                     
Get:4 http://archive.canonical.com gutsy/partner Packages [3606B]              
Get:5 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_IN     
Ign http://security.ubuntu.com gutsy-security/main Translation-en_IN
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_IN     
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_IN       
Get:6 http://security.ubuntu.com gutsy-security Release [51.2kB]             
Get:7 http://security.ubuntu.com gutsy-security/restricted Packages [14B]      
Get:8 http://security.ubuntu.com gutsy-security/main Packages [75.9kB]         
Get:9 http://security.ubuntu.com gutsy-security/multiverse Packages [2903B]    
Get:10 http://security.ubuntu.com gutsy-security/universe Packages [50.5kB]    
Get:11 http://hendrik.kaju.pri.ee gutsy Release.gpg [189B]                     
Ign http://hendrik.kaju.pri.ee gutsy/screenlets Translation-en_IN              
Get:12 http://hendrik.kaju.pri.ee gutsy Release [6702B]                        
Fetched 199kB in 10s (19.2kB/s)                                                
Failed to fetch http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/Release  Unable to find expected entry  screenlets/binary-i386/Packages in Meta-index file (malformed Release file?)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
abhishek@edubuntu:~$ sudo apt-get install gtk-recordmydesktop
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
abhishek@edubuntu:~$ 

```

```

abhishek@edubuntu:~$ sudo dpkg --configure -a
[sudo] password for abhishek:
Setting up sensors-applet (1.7.12+dfsg-1ubuntu1) ...

```
**Nothing happens after this ^**



I tried it again
```

abhishek@edubuntu:~$ sudo apt-get update
Ign cdrom://[APTonCD for ubuntu gutsy - i386 (2008-01-09 12:13) CD1]  Release.gpg
Ign cdrom://[APTonCD for ubuntu gutsy - i386 (2008-01-09 12:13) CD1]  Translation-en_IN
Ign cdrom://Edubuntu 7.10 _Gutsy Gibbon_ - Release i386 Binary-1 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Edubuntu 7.10 _Gutsy Gibbon_ - Release i386 Binary-1 (20071016) gutsy/restricted Translation-en_IN
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_IN
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Ign cdrom://[APTonCD for ubuntu gutsy - i386 (2008-01-09 12:13) CD1]  Release
Get:1 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_IN               
Hit http://archive.canonical.com gutsy Release                                 
Get:2 http://in.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://in.archive.ubuntu.com gutsy/main Translation-en_IN                  
Get:3 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_IN     
Hit http://archive.canonical.com gutsy/partner Packages                        
Ign http://in.archive.ubuntu.com gutsy/restricted Translation-en_IN            
Ign http://in.archive.ubuntu.com gutsy/universe Translation-en_IN              
Ign http://in.archive.ubuntu.com gutsy/multiverse Translation-en_IN          
Hit http://in.archive.ubuntu.com gutsy Release                               
Ign http://security.ubuntu.com gutsy-security/main Translation-en_IN           
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_IN   
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_IN     
Hit http://security.ubuntu.com gutsy-security Release                        
Hit http://in.archive.ubuntu.com gutsy/main Packages                           
Hit http://security.ubuntu.com gutsy-security/restricted Packages            
Hit http://in.archive.ubuntu.com gutsy/restricted Packages                   
Hit http://in.archive.ubuntu.com gutsy/universe Packages                     
Hit http://in.archive.ubuntu.com gutsy/multiverse Packages                   
Hit http://security.ubuntu.com gutsy-security/main Packages                  
Hit http://security.ubuntu.com gutsy-security/multiverse Packages            
Hit http://security.ubuntu.com gutsy-security/universe Packages
Get:4 http://hendrik.kaju.pri.ee gutsy Release.gpg [189B]
Ign http://hendrik.kaju.pri.ee gutsy/screenlets Translation-en_IN
Get:5 http://hendrik.kaju.pri.ee gutsy Release [6702B] 
Fetched 6894B in 6s (1015B/s)                                                  
Failed to fetch http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/Release  Unable to find expected entry  screenlets/binary-i386/Packages in Meta-index file (malformed Release file?)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
abhishek@edubuntu:~$ 

```

What should I do now ?

Thanks for your time and effort.:)

---

### Post by spiderbatdad on 2008-03-16
Looks like there is a problem with updating the screenlets package. You could go into synaptic package manager, locate the screenlets package, highlight it (by clicking it), then go to the package menu at the top of the screen, click and select "lock version." From synaptic you can also run the search for and fix broken packages utility, or close synaptic and run sudo dpkg --configure -a again from the terminal.

---

### Post by Google Spider on 2008-03-16
> **spiderbatdad said:**
> Looks like there is a problem with updating the screenlets package. You could go into synaptic package manager, locate the screenlets package, highlight it (by clicking it), then go to the package menu at the top of the screen, click and select "lock version." From synaptic you can also run the search for and fix broken packages utility, or close synaptic and run sudo dpkg --configure -a again from the terminal.

Thanks for the reply..

I am not able to access synaptic. When I click on system>Administration>Synaptic, it pops-up the same screen which is attached in post #1 and then closes.

---

### Post by bumanie on 2008-03-16
Try this, it may help
Follow this guide [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
Also enable repositories via System--> Administration--> Software Sources Tick the first 4 boxes and check out the third party tab and tick anything that is in there.
Also type in terminal
> sudo apt-get install build-essential  
PS then do > sudo dpkg --configure -a 

---

### Post by Google Spider on 2008-03-16
> **bumanie said:**
> Try this, it may help
Follow this guide [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
Also enable repositories via System--> Administration--> Software Sources Tick the first 4 boxes and check out the third party tab and tick anything that is in there.
Also type in terminal

um, I've been doing C programming so I already have build-essential..

And all the repositories you mentioned are already enabled.

---

### Post by Google Spider on 2008-03-16
> **bumanie said:**
> 
PS then do
```
sudo dpkg --configure -a 
```


I already did that. The output is in post #1

---

### Post by lswest on 2008-03-16
open your sources, and in there try unchecking the screenlets repo, then try running ```
sudo apt-get update
``` if that works, then it means the repo is either down, outdated, or has been moved.

---

### Post by Google Spider on 2008-03-16
> open your sources
..And that means ? :confused:

---

### Post by lswest on 2008-03-16
sorry, you did it before, so i assumed you knew what i meant.  go to system-->administration-->software sources

---

### Post by Google Spider on 2008-03-16
Ok, I unchecked screenlet repo and did sudo apt-get update.

here's the output
```

abhishek@edubuntu:~$ sudo apt-get update
[sudo] password for abhishek:
Ign cdrom://[APTonCD for ubuntu gutsy - i386 (2008-01-09 12:13) CD1]  Release.gpg
Ign cdrom://[APTonCD for ubuntu gutsy - i386 (2008-01-09 12:13) CD1]  Translation-en_IN
Ign cdrom://Edubuntu 7.10 _Gutsy Gibbon_ - Release i386 Binary-1 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Edubuntu 7.10 _Gutsy Gibbon_ - Release i386 Binary-1 (20071016) gutsy/restricted Translation-en_IN
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_IN
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Ign cdrom://[APTonCD for ubuntu gutsy - i386 (2008-01-09 12:13) CD1]  Release  
Get:1 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_IN               
Get:2 http://in.archive.ubuntu.com gutsy Release.gpg [191B]          
Ign http://in.archive.ubuntu.com gutsy/main Translation-en_IN                
Get:3 http://security.ubuntu.com gutsy-security Release.gpg [191B]   
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_IN   
Hit http://archive.canonical.com gutsy Release                       
Hit http://archive.canonical.com gutsy/partner Packages            
Ign http://in.archive.ubuntu.com gutsy/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com gutsy/universe Translation-en_IN
Ign http://in.archive.ubuntu.com gutsy/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com gutsy Release 
Ign http://security.ubuntu.com gutsy-security/main Translation-en_IN
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_IN
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_IN
Hit http://security.ubuntu.com gutsy-security Release               
Hit http://archive.canonical.com gutsy/partner Sources              
Hit http://in.archive.ubuntu.com gutsy/main Packages
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://in.archive.ubuntu.com gutsy/restricted Packages
Hit http://in.archive.ubuntu.com gutsy/universe Packages
Hit http://in.archive.ubuntu.com gutsy/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/main Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/universe Packages
Fetched 3B in 1s (2B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
abhishek@edubuntu:~$ 

```

---

### Post by Google Spider on 2008-03-16
Also did this again:
```

abhishek@edubuntu:~$ sudo dpkg --configure -a
Setting up sensors-applet (1.7.12+dfsg-1ubuntu1) ...

```

---

### Post by lswest on 2008-03-16
well that got rid of one error, what happens if you run ```
sudo apt-get install --reinstall sensors-applet
```  if that doesn't work, try ```
sudo dpkg --configure -a
```

---

### Post by Google Spider on 2008-03-16
Thanks for your time.

Here's the output
```

abhishek@edubuntu:~$ sudo apt-get install --reinstall sensors-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdevhelp-1-0 libgbf-1-1 anjuta-common devhelp-common libgbf-1-common
  binfmt-support
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 59 not upgraded.
Need to get 0B/98.1kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 101284 files and directories currently installed.)
Preparing to replace sensors-applet 1.7.12+dfsg-1ubuntu1 (using .../sensors-applet_1.7.12+dfsg-1ubuntu1_i386.deb) ...
Unpacking replacement sensors-applet ...
Setting up sensors-applet (1.7.12+dfsg-1ubuntu1) ...
***********************************************************************
The applet's configuration format changed for this release.
If you have the applet already in your panels, for the change to take
effect remove the applet from your panels and add a new instance of it.
***********************************************************************

abhishek@edubuntu:~$ 

```

---

### Post by lswest on 2008-03-16
according to that ```
sudo apt-get update
``` should work now, and if there is a problem with the applet, just remove it from the panel, and add it again.

and no problem, always happy to help ^^

---

### Post by Google Spider on 2008-03-16
I also tried sudo dpkg --configure -a
```

abhishek@edubuntu:~$ sudo dpkg --configure -a
abhishek@edubuntu:~$ 

```

---

### Post by lswest on 2008-03-16
yeah, the problem should be fixed now ^^

---

### Post by Google Spider on 2008-03-16
OK, The problem is solved. Thanks!

---

### Post by lswest on 2008-03-16
no problem, glad we got it solved.  Just don't forget to mark the thread as solved using the thread tools menu at the top of the forums, so that others know there's a solution here ;) thanks ^^

---

