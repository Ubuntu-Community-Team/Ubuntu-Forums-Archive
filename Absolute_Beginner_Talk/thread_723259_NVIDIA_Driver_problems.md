---
title: "NVIDIA Driver problems"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Smoogz on 2008-03-13
Im using Ubuntu 7.10
my computer specs are
Compaq Presario V6000
2 Ghz AMD Turion 64
NVIDIA Geforece 6150 Go

when i try to enable the restricted drivers in sytem/administration/restricted drivers manager  it says the software source package nvidia-glx-new is not enabled.
so i go to software sources and ive checked all the boxes universe, multiverse, restricted, main.

it starts downloading with the package information and it says it couldnt download all repositories and then has this:

[http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.bz2:](http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz:](http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz:) Error reading from server. Remote end closed connection
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz:) 416 Requested Range Not Satisfiable
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz:) Error reading from server. Remote end closed connection
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz:) 416 Requested Range Not Satisfiable
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz:) Error reading from server. Remote end closed connection
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz:) 416 Requested Range Not Satisfiable
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz:) Error reading from server. Remote end closed connection
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:) 416 Requested Range Not Satisfiable
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:) Error reading from server. Remote end closed connection
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz:) 416 Requested Range Not Satisfiable
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz:) Error reading from server. Remote end closed connection
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz:) 416 Requested Range Not Satisfiable
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz:) Error reading from server. Remote end closed connection
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz:) 416 Requested Range Not Satisfiable
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz:) Error reading from server. Remote end closed connection

it also gives me these errors:

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) gutsy Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release: The following signatures were invalid: NODATA 1 NODATA 2

what should i do?

thnx in advance!

---

### Post by glennric on 2008-03-13
Try to run
```
sudo apt-get update
```
from a terminal.  Then try what you were doing again.

---

### Post by Smoogz on 2008-03-13
i just tried the sudo apt-get and then reselected the package sources and tried to enable the driver through the restircted drivers manager and it still gave the same responses as earlier


i did get these errors in the terminal after useing the apt-get command

drew@drew-laptop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg                              
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg          
Get:3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US 
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Get:4 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
  
Get:6 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release [6998B]                       
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Get:7 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                      
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                        
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US   
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
  Error reading from server. Remote end closed connection
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US       
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
  416 Requested Range Not Satisfiable
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources            
99% [10 Sources bzip2 0] [Waiting for headers] [Waiting for headers]  369B/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
  Sub-process bzip2 returned an error code (2)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                  
99% [11 Sources bzip2 0] [Waiting for headers] [Connecting to security.ubuntu.cbzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
  Sub-process bzip2 returned an error code (2)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                 
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
  416 Requested Range Not Satisfiable
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
  Error reading from server. Remote end closed connection
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release [65.9kB]                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
  416 Requested Range Not Satisfiable
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
  Error reading from server. Remote end closed connection
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                         
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
  416 Requested Range Not Satisfiable
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
  Error reading from server. Remote end closed connection
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release [58.5kB]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                            
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                     
99% [16 Packages bzip2 0] [Connecting to archive.ubuntu.com (91.189.88.31)]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                    
  Sub-process bzip2 returned an error code (2)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                               
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources                      
99% [18 Sources bzip2 0] [Connecting to archive.ubuntu.com (91.189.88.31)]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources                    
  Sub-process bzip2 returned an error code (2)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources                   
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages [7837B]             
99% [19 Packages gzip 0] [Waiting for headers]                       8845B/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                        
  Sub-process gzip returned an error code (1)
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources [1965B]              
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages                
  416 Requested Range Not Satisfiable
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages                      
  Error reading from server. Remote end closed connection
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages                
  416 Requested Range Not Satisfiable
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages                  
  Error reading from server. Remote end closed connection
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources                 
  416 Requested Range Not Satisfiable
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources                       
  Error reading from server. Remote end closed connection
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources                 
  416 Requested Range Not Satisfiable
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources                   
  Error reading from server. Remote end closed connection
Fetched 341kB in 39s (8680B/s)                                                 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz)  Error reading from server. Remote end closed connection
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz)  416 Requested Range Not Satisfiable
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz)  Error reading from server. Remote end closed connection
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz)  416 Requested Range Not Satisfiable
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz)  416 Requested Range Not Satisfiable
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz)  Error reading from server. Remote end closed connection
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz)  416 Requested Range Not Satisfiable
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz)  Error reading from server. Remote end closed connection
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  416 Requested Range Not Satisfiable
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  Error reading from server. Remote end closed connection
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  416 Requested Range Not Satisfiable
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  Error reading from server. Remote end closed connection
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  416 Requested Range Not Satisfiable
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  Error reading from server. Remote end closed connection
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz)  416 Requested Range Not Satisfiable
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz)  Error reading from server. Remote end closed connection
Reading package lists... Done
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) gutsy Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release: The following signatures were invalid: NODATA 1 NODATA 2
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
drew@drew-laptop:~$

---

