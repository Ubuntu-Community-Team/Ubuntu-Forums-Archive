---
title: "Updating Ubuntu - Error"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by davidpring2005 on 2007-03-23
I'm trying to update Ubuntu but i'm getting this error. Same happens when i try to install through Add/Remove.


```
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

---

### Post by taurus on 2007-03-23
Shutdown the Add/Remove window.  Then, open a terminal, Applications -> Accessories -> Terminal, and run these two commands.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by xopher on 2007-03-23
The error you are getting is caused by you having more than one instance of apt running, eg. Synaptic and Add/Remove, or Add/Remove and apt-get.

So just close all instances of possible updating-programs and re-run it.

But as taurus said, for simple updating I also just issue: ```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by davidpring2005 on 2007-03-23
The first command returned:

```
david@David-Laptop:~$ sudo aptitude update
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 http://ca.archive.ubuntu.com edgy Release.gpg [191B]                  
Ign http://ca.archive.ubuntu.com edgy/main Translation-en_CA                
Ign http://ca.archive.ubuntu.com edgy/restricted Translation-en_CA          
Ign http://ca.archive.ubuntu.com edgy/universe Translation-en_CA            
Ign http://ca.archive.ubuntu.com edgy/multiverse Translation-en_CA          
Get:2 http://ca.archive.ubuntu.com edgy-updates Release.gpg [191B]          
Ign http://ca.archive.ubuntu.com edgy-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com edgy-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com edgy-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com edgy-updates/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com edgy Release                
Hit http://ca.archive.ubuntu.com edgy-updates Release
Hit http://ca.archive.ubuntu.com edgy/main Packages                             
Hit http://ca.archive.ubuntu.com edgy/restricted Packages    
Hit http://ca.archive.ubuntu.com edgy/universe Packages
Hit http://ca.archive.ubuntu.com edgy/main Sources
Hit http://ca.archive.ubuntu.com edgy/restricted Sources
Hit http://ca.archive.ubuntu.com edgy/universe Sources
Hit http://ca.archive.ubuntu.com edgy/multiverse Packages
Hit http://ca.archive.ubuntu.com edgy-updates/main Packages  
Hit http://ca.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://ca.archive.ubuntu.com edgy-updates/universe Packages
Hit http://ca.archive.ubuntu.com edgy-updates/main Sources   
Hit http://ca.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://ca.archive.ubuntu.com edgy-updates/universe Sources
Hit http://ca.archive.ubuntu.com edgy-updates/multiverse Packages
Get:3 http://security.ubuntu.com edgy-security Release.gpg [191B]               
Ign http://security.ubuntu.com edgy-security/main Translation-en_CA             
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_CA       
Ign http://security.ubuntu.com edgy-security/universe Translation-en_CA         
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_CA       
Hit http://security.ubuntu.com edgy-security Release                            
Hit http://security.ubuntu.com edgy-security/main Packages                      
Hit http://security.ubuntu.com edgy-security/restricted Packages                
Hit http://security.ubuntu.com edgy-security/universe Packages                  
Hit http://security.ubuntu.com edgy-security/main Sources                       
Hit http://security.ubuntu.com edgy-security/restricted Sources                 
Hit http://security.ubuntu.com edgy-security/universe Sources                   
Hit http://security.ubuntu.com edgy-security/multiverse Packages                
Fetched 3B in 7s (0B/s)                                                         
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache
david@David-Laptop:~$ 
```

The second returned 

```
david@David-Laptop:~$ sudo aptitude upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
david@David-Laptop:~$ 

```

---

### Post by davidpring2005 on 2007-03-23
Ooooppps   i didn't realize i had it open on the other desktop..   how embaresing...lol

---

### Post by PurplePenguin on 2007-03-23
Don't be embarrassed.  In fact, now you've got this thread here, it'll help everybody else that gets this problem after you.  

It's happened to all of us, believe me. 

It happens to me once a month or so (I work with four desktops and forget what I'm doing and where sometimes!). :D

---

