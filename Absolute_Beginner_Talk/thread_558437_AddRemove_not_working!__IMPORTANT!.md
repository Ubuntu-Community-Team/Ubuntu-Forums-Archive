---
title: "Add/Remove not working!  IMPORTANT!"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by helixed on 2007-09-23
Hey everybody,

When I try to add any application in the add/remove bar, the updator retrieves 73 our of 74 packages, and then displays the following error:

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

It seems automatix2 is also not working, and I'm not sure whether this error is related or not.  I found this situation to be odd considering my internet it working perfectly.

I was wondering if this error could be related to the fact that I am currently on the Iowa State University network.

 I apologize if this issue has already been taken care of, but I really need to use my computer as soon as possible and I do not have time to dig for an answer.

Thank you,

Helixed

---

### Post by overdrank on 2007-09-23
> **helixed said:**
> Hey everybody,

When I try to add any application in the add/remove bar, the updator retrieves 73 our of 74 packages, and then displays the following error:

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

It seems automatix2 is also not working, and I'm not sure whether this error is related or not.  I found this situation to be odd considering my internet it working perfectly.

I was wondering if this error could be related to the fact that I am currently on the Iowa State University network.

 I apologize if this issue has already been taken care of, but I really need to use my computer as soon as possible and I do not have time to dig for an answer.

Thank you,

Helixed

Hi can you post the output of these commands  in the terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by stmiller on 2007-09-24
> **helixed said:**
> 
It seems automatix2 is also not working, and I'm not sure whether this error is related or not.  I found this 


[Don't use automatix]("http://mjg59.livejournal.com/77440.html"). Ubuntu strongly advises you do not use it, as it breaks your system in many areas. Remove all automatix lines from your /apt/etc/sources.list file and then run
```

sudo apt-get update
sudo apt-get autoremove
sudo apt-get autoclean

```

---

### Post by helixed on 2007-09-24
Okay,

After reading that article, I'm not convinced I shouldn't use automatix.  I went to remove all of the references from that file.  I typed in:

sudo gedit /apt/etc/sources.list

When the file opened, it was completely blank.  Did I type in a bad command?  Overdrank, when I ran sudo apt-get update, I received the following:

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                 
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]                    
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                  
Get:3 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US             
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                           
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US    
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                      
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages [4912kB]
99% [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages [4912kB]
99% [10 Packages gzip 0]             
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 10B in 1s (8B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

And when I ran sudo apt-get upgrade, I got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Thanks for the help,

Helixed

---

### Post by alienexplorers on 2007-09-24
Use :
> cat /etc/apt/sources.lst
to list the sources.lst file.

Is your add/remove program working.

---

### Post by helixed on 2007-09-24
I ran gksu gedit /etc/apt/sources.list instead of sudo (I have no idea what the difference is) and it opened the sources file.  I deleted all of the automatix mentions, bit I still got the same thing when I ran sudo apt-get update.

Thanks,

Helixed

---

### Post by alienexplorers on 2007-09-24
Try:
> sudo aptitude update
sudo aptitude upgrade

---

### Post by helixed on 2007-09-24
This produced:

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages [4912kB]
99% [4 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages [4912kB]
99% [5 Packages gzip 0]            
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 5B in 1s (4B/s)
Reading package lists... Done

and:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Thanks,

Helixed

---

### Post by asmoore82 on 2007-09-24
> **helixed said:**
> Okay,

After reading that article, I'm not convinced I shouldn't use automatix.

[SIZE="3"]1. read the article again.
2. If not_convinced(); goto #1;[/SIZE]

your system has a problem and we are telling you that Automatix is the cause!
Automatix is so poorly designed/implemented, there's really no way of
knowing the full extent of damage it could have caused.

> ```
killall -9 dpkg
```

**May well leave the system in an inconsistent and unbootable state**, and
is carried out without warning. **This is entirely unacceptable** and will
leave a stale lockfile in any case.

that is so dead serious that there's no other way to say it: ***entirely unacceptable***.

---

### Post by dptxp on 2007-09-24
Open Add/Remove

Click on Preferences at bottom left of Add/Remove screen when Add/Remove opens.

Choose custom server and let Ubuntu find the best for you.

I think that you are connected to wrong server.

---

### Post by helixed on 2007-09-24
Hey everybody, thanks for the help,

I decided to do a quick reformat just to resolve the issue as soon as possible.  Everything seems to be working fine.

dptxp:  I mistyped earlier.  I meant to say I'm convinced I shouldn't use automatix.  I guess that's what happens when you type this late at night.

Anyway, thanks again.

Helixed

---

### Post by alienexplorers on 2007-09-24
Try this command:
> ls /var/lib/apt/lists/partial/
Delete any files you see there and run
> sudo apt-get update again.

---

### Post by FuturePilot on 2007-09-24
Never mind.... I stand corrected.

---

