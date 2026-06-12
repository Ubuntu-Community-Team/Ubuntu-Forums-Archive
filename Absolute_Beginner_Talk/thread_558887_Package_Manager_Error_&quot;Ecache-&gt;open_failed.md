---
title: "Package Manager Error &quot;E:cache-&gt;open failed&quot;"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by EricJosepi on 2007-09-24
Hi,

My package manager just gave me this error and now I can't use Synaptec.

> E: Dynamic MMap ran out of room
E: Error occurred while processing libmono-corlib1.0-cil (NewFileVer1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Does anyone know a solution?

---

### Post by EricJosepi on 2007-09-24
Bump

---

### Post by overdrank on 2007-09-24
> **EricJosepi said:**
> Hi,

My package manager just gave me this error and now I can't use Synaptec.



Does anyone know a solution?

Hi could you post the output of these command in th terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by hnprashanth on 2007-12-29
Hi,
I have same problem.
When I did as u given here in terminal.
I got following:

```
prashanth@prashanth-desktop:~$ sudo apt-get update
[sudo] password for prashanth:
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_IN
Get:2 http://in.archive.ubuntu.com gutsy Release.gpg [191B]          
Ign http://in.archive.ubuntu.com gutsy/main Translation-en_IN        
Get:3 http://download.tuxfamily.org gutsy Release.gpg [189B]         
Ign http://download.tuxfamily.org gutsy/avant-window-navigator Translation-en_IN
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_IN
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_IN
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_IN
Hit http://security.ubuntu.com gutsy-security Release                
Ign http://in.archive.ubuntu.com gutsy/restricted Translation-en_IN  
Ign http://in.archive.ubuntu.com gutsy/universe Translation-en_IN
Ign http://in.archive.ubuntu.com gutsy/multiverse Translation-en_IN
Get:4 http://in.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://in.archive.ubuntu.com gutsy-updates/main Translation-en_IN
Ign http://in.archive.ubuntu.com gutsy-updates/restricted Translation-en_IN
Hit http://download.tuxfamily.org gutsy Release                     
Hit http://in.archive.ubuntu.com gutsy Release                       
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Hit http://in.archive.ubuntu.com gutsy-updates Release               
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://security.ubuntu.com gutsy-security/universe Packages      
Hit http://security.ubuntu.com gutsy-security/multiverse Packages    
Hit http://in.archive.ubuntu.com gutsy/main Packages                 
Hit http://in.archive.ubuntu.com gutsy/restricted Packages
Hit http://in.archive.ubuntu.com gutsy/universe Packages
Hit http://download.tuxfamily.org gutsy/avant-window-navigator Packages
Hit http://in.archive.ubuntu.com gutsy/multiverse Packages
Hit http://in.archive.ubuntu.com gutsy-updates/main Packages
Hit http://in.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://download.tuxfamily.org gutsy/avant-window-navigator Sources
Fetched 4B in 4s (1B/s)  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

---

### Post by overdrank on 2007-12-29
HI and then you can run the command in the terminal
```
sudo dpkg --configure -a
```

---

### Post by hnprashanth on 2007-12-29
Thanks Overdrank,
The problem is resolved.
It occured due to closing of terminal when sun-java6-jre was getting installed.
:KS

---

### Post by davepimp00 on 2008-04-02
Thanks overdrank

---

