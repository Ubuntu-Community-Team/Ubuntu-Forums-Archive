---
title: "problem with apt-get update"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by tarunkool on 2007-10-27
hello everybody
i am new ubuntu 7.04 so please help me out
whenever i try to update, all the updates get failed.
neither i am able to install any new software through add/remove applications

as i am new to linux so plz be specific about everything.

---

### Post by taurus on 2007-10-27
Can you post the complete output of that command?

```
sudo apt-get update
```

---

### Post by Maestro23 on 2007-10-27
> **tarunkool said:**
> hello everybody
i am new ubuntu 7.04 so please help me out
whenever i try to update, all the updates get failed.
neither i am able to install any new software through add/remove applications

as i am new to linux so plz be specific about everything.

Need to see your **sources.list** file. Open a terminal and type the following command:

> cat /etc/apt/sources.list

Copy/paste the contents here.

*EDIT: Nevermind, taurus in on it. :smile:

---

### Post by tarunkool on 2007-10-27
here's the output

tarun@tarun-laptop:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_IN
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_IN
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release.gpg [191B]  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Translation-en_IN             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Translation-en_IN           
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Translation-en_IN         
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Translation-en_IN   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/universe Translation-en_IN     
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security Release.gpg [191B]          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Translation-en_IN        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/restricted Translation-en_IN  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/universe Translation-en_IN    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/multiverse Translation-en_IN  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release                                
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release [50.9kB]             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release                        
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security Release [50.9kB]            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security Release                       
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Packages [1007kB]               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Packages                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Packages                    
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Sources [293kB]                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Sources                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Sources                     
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Packages [3754kB]           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Sources                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Sources                     
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Packages [131kB]        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Packages                  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Packages            
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Sources [32.9kB]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Sources
Get:11 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/universe Packages [50.2kB]
1% [11 Packages bzip2 0] [Connecting to in.archive.ubuntu.com (91.189.88.31)]
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/universe Packages            
  Sub-process bzip2 returned an error code (2)
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Packages [86.4kB]   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Packages                                  
Get:13 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/restricted Packages [6360B]                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/restricted Packages                            
Get:14 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Sources [16.0kB]                       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Sources                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/restricted Sources                             
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/universe Packages [42.9kB]                  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/universe Packages                              
Get:16 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/universe Sources [6295B]                    
2% [16 Sources bzip2 0] [Connecting to in.archive.ubuntu.com (91.189.88.31)]                    
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/universe Sources           
  Sub-process bzip2 returned an error code (2)
Get:17 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/multiverse Packages [6101B]                 
2% [Working]                                                                     992B/s 1h31m57s
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/multiverse Packages                            
  Sub-process bzip2 returned an error code (2)
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/multiverse Sources                             
Get:18 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Packages [1307kB]                               
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Packages                                           
  Error reading from server. Remote end closed connection [IP: 91.189.88.31 80]
Get:19 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Sources [385kB]                                 
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Sources                                            
  Error reading from server. Remote end closed connection [IP: 91.189.88.31 80]
Get:20 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Packages [4912kB]                           
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Packages                                       
  Error reading from server. Remote end closed connection [IP: 91.189.88.31 80]
Get:21 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Packages [173kB]                        
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Packages                                   
  Error reading from server. Remote end closed connection [IP: 91.189.88.31 80]
Get:22 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Packages [6403B]                  
1% [Connecting to in.archive.ubuntu.com (91.189.88.31)]                         165B/s 20h40m12s
gzip: stdin: not in gzip format
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Packages                             
  Sub-process gzip returned an error code (1)
Get:23 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Sources [39.6kB]                        
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Sources                                    
  Error reading from server. Remote end closed connection [IP: 91.189.88.31 80]
Get:24 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Packages [111kB]                       
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Packages                                  
  Error reading from server. Remote end closed connection [IP: 91.189.88.31 80]
Get:25 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/restricted Packages [6403B]                 
1% [25 Packages gzip 0] [Waiting for headers]                                   165B/s 20h55m29s
gzip: stdin: not in gzip format
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/restricted Packages                            
  Sub-process gzip returned an error code (1)
Get:26 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Sources [17.9kB]                       
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Sources                                   
  Error reading from server. Remote end closed connection [IP: 91.189.88.31 80]
Get:27 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/universe Packages [50.2kB]                  
1% [Working]                                                                    2085B/s 1h39m15s
gzip: stdin: not in gzip format
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/universe Packages                              
  Sub-process gzip returned an error code (1)
Fetched 95.8kB in 1m57s (817B/s)                                                                
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.bz2](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.bz2](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.bz2](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  Error reading from server. Remote end closed connection [IP: 91.189.88.31 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  Error reading from server. Remote end closed connection [IP: 91.189.88.31 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Error reading from server. Remote end closed connection [IP: 91.189.88.31 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  Error reading from server. Remote end closed connection [IP: 91.189.88.31 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  Error reading from server. Remote end closed connection [IP: 91.189.88.31 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  Error reading from server. Remote end closed connection [IP: 91.189.88.31 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz)  Error reading from server. Remote end closed connection [IP: 91.189.88.31 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by tarunkool on 2007-10-27
here is sources.list

# See [ftp://help.ubuntu.com/community/UpgradeNotes](ftp://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [ftp://in.archive.ubuntu.com/ubuntu/](ftp://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [ftp://in.archive.ubuntu.com/ubuntu/](ftp://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-security multiverse

---

