---
title: "Updating Problem"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by toasty_ghosty on 2007-07-01
I'm trying to update my 3D drivers but when I run sudo apt-get update I get this:

theking@OptimusPrimeTheSecond:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B] 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Get:2 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release.gpg [191B]        
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release              
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release                               
Err [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release                               
  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources           
Get:5 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release [2961B]           
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3155B in 2s (1276B/s)
Reading package lists... Done
W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: You may want to run apt-get update to correct these problems
theking@OptimusPrimeTheSecond:~$ 

What signatures is it talking about?

---

### Post by nanotube on 2007-07-01
we are talking about the digital gpg sigtature for the beryl-project repository, which lets you verify the integrity of the repository/packages.

here's the instruction to get the gpg key for the beryl repository;
[http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/)

---

### Post by toasty_ghosty on 2007-07-01
Thank You. I'm trying to update my ATI drivers and I am having issues. But that should help.

---

### Post by nanotube on 2007-07-01
> **toasty_ghosty said:**
> Thank You. I'm trying to update my ATI drivers and I am having issues. But that should help.

oh, well, also note that that gpg error is just a warning - you can still proceed to install stuff out of other repositories without any problems...

good luck :)

---

### Post by davidjmayo on 2007-07-01
Are you using Feisty Fawn (7.04) or Edgy (6.10) 

Nanotube--is the problem with the repos. Look again it's looking at both feisty and edgy repos. The error is with edgy and beryl

---

### Post by nanotube on 2007-07-01
> **davidjmayo said:**
> Are you using Feisty Fawn (7.04) or Edgy (6.10) 

Nanotube--is the problem with the repos. Look again it's looking at both feisty and edgy repos. The error is with edgy and beryl

hey yes, you are right - that's a separate problem, but a problem nevertheless. all other repos point to feisty, but the beryl one seems to point to edgy. the OP would want to edit sources.list and change that. :) 

good catch, davidjmayo! ;)

---

