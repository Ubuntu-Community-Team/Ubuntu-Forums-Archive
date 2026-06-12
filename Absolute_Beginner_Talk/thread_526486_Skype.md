---
title: "Skype"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Evelyn on 2007-08-15
I went to Skype.com and tried to download it. I was installing the package and this message came up:

Could not install all dependencies
Usually this is related to an error of the software distributor.
See the terminal window for more details.
Details:  installArchives() failed

Please help.

---

### Post by por100pre1 on 2007-08-15
Check for Skype in [Medibuntu]("http://www.medibuntu.org/packages.php") and read how to [add the repos]("http://www.medibuntu.org/repository.php"). Then you can install it by copy/paste and ENTER this in a terminal:

```
sudo apt-get install skype
```

---

### Post by Evelyn on 2007-08-15
This what I did (see below).  Did I do it correctly?  Is there anything else I should do?

rie-rie@dell:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package skype
rie-rie@dell:~$ echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" | sudo tee -a /etc/apt/sources.list
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
rie-rie@dell:~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

OK
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US                
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Get:3 [http://ftp.debian.org](http://ftp.debian.org) sarge Release.gpg [378B]                           
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge/main Translation-en_US                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release [2195B]           
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US       
Hit [http://ftp.debian.org](http://ftp.debian.org) sarge Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Err [http://ftp.debian.org](http://ftp.debian.org) sarge Release                             
  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US 
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B] 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Get:7 [http://ftp.debian.org](http://ftp.debian.org) sarge Release [34.6kB]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
Get:8 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages [5483B]               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources              
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge Release                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources           
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge/main Packages                        
Get:9 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages [2849B] 
Get:10 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages [5483B]              
Hit [http://ftp.debian.org](http://ftp.debian.org) sarge/main Packages                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Get:11 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages [2849B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 54.6kB in 1s (38.0kB/s)
Reading package lists... Done
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_feisty_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_feisty_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
rie-rie@dell:~$ 
rie-rie@dell:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  librte1
The following NEW packages will be installed:
  librte1 skype
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
2 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
rie-rie@dell:~$

---

### Post by Evelyn on 2007-08-15
I still don't have Skype.  Please help!

---

### Post by Steveway on 2007-08-15
You need to close Synaptic, Add/Remove or the Update-Manager if any of those is running.

---

### Post by Amazona aestiva on 2007-08-15
I can install it... perhaps download error:confused:
Try again:
[http://www.skype.com/go/getskype-linux-ubuntu]("http://www.skype.com/go/getskype-linux-ubuntu")

---

### Post by Evelyn on 2007-08-15
I've tried all of that and it still won't work.  It seems to come down to for skype to install I need zope2.7 and inorder to get that I need python2.3 but installing that would remove several 9if not all) the programs on my computer and some that (I believe) are critical to running ubuntu.  Help!

---

### Post by mali2297 on 2007-08-15
If you search for skype in synaptic, do yo find a version 1.3.0.53-1medibuntu?

I could install that version without the dependencies that are causing you problems.

---

### Post by Jussi01 on 2007-09-03
Did you ever get this sorted?

---

### Post by L Campbell on 2007-09-03
> **Evelyn said:**
> I went to Skype.com and tried to download it. I was installing the package and this message came up:

Could not install all dependencies
Usually this is related to an error of the software distributor.
See the terminal window for more details.
Details:  installArchives() failed

Please help.

If you go here:-  [http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

and under "Choose distribution", click on Feisty, you should be on your way.

This is what worked for me.

---

