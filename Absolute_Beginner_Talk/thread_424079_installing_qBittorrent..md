---
title: "installing qBittorrent."
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by stokes0224 on 2007-04-26
can someone simplify this for me please?

[http://qbittorrent.sourceforge.net/download.php]("http://qbittorrent.sourceforge.net/download.php")

many thanks stokes.

---

### Post by kakalaky on 2007-04-26
```
sudo gedit /etc/apt/sources.lst
```

insert the proper lines for your distro into the file.  For example, if you are using feisty it would be:

```
deb http://hydr0g3n.free.fr/qbittorrent/feisty/ ./
deb-src http://hydr0g3n.free.fr/qbittorrent/feisty/ ./
```

then

```
sudo apt-get update && sudo apt-get install qbittorrent
```

---

### Post by stokes0224 on 2007-04-26
i did all that and this is what came out;


Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 0s (5B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package qbittorrent

---

### Post by kakalaky on 2007-04-26
can you post your sources.lst?

---

### Post by stokes0224 on 2007-04-26
[IMG]http://i62.photobucket.com/albums/h84/stokes0224/Screenshot-sources.png[/IMG]

---

### Post by Nythain on 2007-04-26
wrong file... /etc/apt/sources.list not sources.lst...

---

### Post by taurus on 2007-04-26
```
cat /etc/apt/sources.list
```

---

### Post by kakalaky on 2007-04-26
Oops, one of those days.  Add it to sources.list not sources.lst.  Sorry.

---

### Post by stokes0224 on 2007-04-26
thanks for your help its all sorted now!!!

---

### Post by Freelance Physicist on 2007-06-22
I'm having the same problem installing qBittorrent.

```
$ cat /etc/apt/sources.list | grep qbittorrent

deb http://hydr0g3n.free.fr/qbittorrent/feisty/ ./
deb-src http://hydr0g3n.free.fr/qbittorrent/feisty/ ./
```

and yet ...

```
$ sudo apt-get update && sudo apt-get install qbittorrent

Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Get:2 http://wine.budgetdedicated.com feisty Release.gpg [191B]                
Ign http://wine.budgetdedicated.com feisty/main Translation-en_US              
Get:3 http://us.archive.ubuntu.com feisty Release.gpg [191B]         
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                 
Ign http://hydr0g3n.free.fr ./ Release.gpg                           
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US      
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com feisty-security Release                         
Hit http://wine.budgetdedicated.com feisty Release                             
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US           
Get:4 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]           
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US   
Hit http://us.archive.ubuntu.com feisty Release                                
Hit http://us.archive.ubuntu.com feisty-updates Release                        
Hit http://security.ubuntu.com feisty-security/main Packages                   
Ign http://wine.budgetdedicated.com feisty/main Packages                       
Ign http://hydr0g3n.free.fr ./ Translation-en_US                               
Hit http://us.archive.ubuntu.com feisty/main Packages                
Hit http://us.archive.ubuntu.com feisty/restricted Packages          
Hit http://us.archive.ubuntu.com feisty/main Sources                 
Hit http://security.ubuntu.com feisty-security/restricted Packages             
Hit http://security.ubuntu.com feisty-security/main Sources                    
Hit http://security.ubuntu.com feisty-security/restricted Sources              
Hit http://wine.budgetdedicated.com feisty/main Sources                        
Hit http://us.archive.ubuntu.com feisty/restricted Sources                     
Hit http://us.archive.ubuntu.com feisty/universe Packages                      
Hit http://us.archive.ubuntu.com feisty/universe Sources                       
Hit http://us.archive.ubuntu.com feisty/multiverse Packages                    
Hit http://us.archive.ubuntu.com feisty/multiverse Sources                     
Hit http://us.archive.ubuntu.com feisty-updates/main Packages                  
Hit http://security.ubuntu.com feisty-security/universe Packages               
Hit http://security.ubuntu.com feisty-security/universe Sources                
Hit http://security.ubuntu.com feisty-security/multiverse Packages             
Hit http://security.ubuntu.com feisty-security/multiverse Sources              
Hit http://wine.budgetdedicated.com feisty/main Packages                       
Ign http://hydr0g3n.free.fr ./ Release                               
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Ign http://hydr0g3n.free.fr ./ Packages             
Ign http://hydr0g3n.free.fr ./ Sources              
Hit http://hydr0g3n.free.fr ./ Packages
Hit http://hydr0g3n.free.fr ./ Sources
Fetched 4B in 2s (2B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package qbittorrent**

```

Any ideas?

---

### Post by Sushubh on 2007-06-22
is this application better than ktorrent?

---

### Post by andre_dc on 2007-10-17
Hi ,

Since a recent update my qbittorrent does no longer work , I tried re-installing but without success. ( I tried synaptic first but without success ) , accrding to the output bellow there is a library issue ? 
Also this might not be the right place to post my error , but where should I post it ?

Tx , 
andre :(

$ cat /etc/apt/sources.list | grep qbittorrent
# [http://qbittorrent.sourceforge.net/download.php](http://qbittorrent.sourceforge.net/download.php)
deb [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./
deb-src [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./


$ sudo apt-get update && sudo apt-get install qbittorrent
Get:1 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main Translation-en_US                                         
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/restricted Translation-en_US      
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/universe Translation-en_US        
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/multiverse Translation-en_US      
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/universe Translation-en_US        
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Get:3 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty-updates Release.gpg [191B]      
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty-updates/main Translation-en_US      
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty-updates Release             
Ign [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Release.gpg                          
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/restricted Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/restricted Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/universe Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/universe Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/universe Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty-updates/restricted Sources
Ign [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Translation-en_US
Ign [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Release
Ign [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Packages
Ign [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Sources
Hit [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Packages
Hit [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Sources
Fetched 3B in 2s (1B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  qbittorrent: Depends: libqt4-core (>= 4.3.0) but 4.2.3-0ubuntu3 is to be installed
               Depends: libqt4-gui (>= 4.3.0) but 4.2.3-0ubuntu3 is to be installed
E: Broken packages

---

### Post by homerj742 on 2007-10-24
I've had failure after the Gusty update as well, somebody please help..

---

