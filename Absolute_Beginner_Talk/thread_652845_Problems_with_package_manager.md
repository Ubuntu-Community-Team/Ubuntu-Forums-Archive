---
title: "Problems with package manager"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by MONODA on 2007-12-29
I currently have enable all repositories that come with ubuntu except the source code. I have also enable medibuntu. But whenever I relod my repositories and see the details, half of them fail but I dont get any error message. Is this supposed to happen? if not how can I fix it? Thanks in advance.

---

### Post by Seisen on 2007-12-29
Post exactly what it says here so we can get more of an idea of what is going on.

---

### Post by MONODA on 2007-12-29
This is what I get when I type sudo apt-get update in terminal:
> Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                              
Hit [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy Release.gpg                                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                
Get:4 [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy/main Translation-en_US              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                  
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Ign [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy/main Translation-en_US
Get:5 [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy/universe Translation-en_US
Ign [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy/universe Translation-en_US
Get:6 [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy/restricted Translation-en_US
Ign [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Get:7 [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy/multiverse Translation-en_US
Ign [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy/multiverse Translation-en_US                    
Hit [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy-updates Release.gpg                             
Get:8 [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy-updates/universe Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Ign [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy-updates/universe Translation-en_US              
Get:9 [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy-updates/main Translation-en_US                
Ign [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy-updates/main Translation-en_US                  
Get:10 [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy-updates/multiverse Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy-updates/multiverse Translation-en_US            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Get:11 [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy-updates/restricted Translation-en_US         
Ign [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy-updates/restricted Translation-en_US            
Get:12 [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy Release [65.9kB]                             
Get:13 [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy-updates Release [58.5kB]                     
Hit [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy/main Packages                                   
Hit [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy/universe Packages                               
Hit [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy/restricted Packages                             
Hit [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy/multiverse Packages                             
Hit [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy-updates/universe Packages                       
Hit [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy-updates/main Packages                           
Hit [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy-updates/multiverse Packages                     
Hit [ftp://ftp.tudelft.nl](ftp://ftp.tudelft.nl) gutsy-updates/restricted Packages                     
Fetched 124kB in 18s (6592B/s)                                                 
Reading package lists... Done

but when I relod in the software sources manager I see what is attached.

---

### Post by Seisen on 2007-12-29
If you are talking about the ignore messages I get those sometimes too, that is no bid deal. What attachment are you talking about?

---

### Post by MONODA on 2007-12-29
Oh sorry
[[IMG]http://img166.imageshack.us/img166/8377/screenshotlh2.th.png[/IMG]](http://img166.imageshack.us/my.php?image=screenshotlh2.png)

---

