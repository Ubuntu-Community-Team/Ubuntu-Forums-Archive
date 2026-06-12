---
title: "Updates, Add/Remove = Not Working!"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by brandknewme on 2007-02-21
Hello,
I am still in love with my Ubuntu. I can't get enough.

However, I am having some troubles, which will probably be easy for you guys to figure out. 

Okay, if I try to do any updates, add/remove or package manager,  it will do that black faded roll over thing asif it's going to do something, then just sits there doing nothing. At first I thought it was updating, but I left it for a full day and nothing. I can hit enter and get out of it. But, I cant update anything.

What can I do?

PLEASE Help, I don't want to go back to Windows!!!!!!

---

### Post by tonyr1988 on 2007-02-21
Open a Terminal (Applications -> Accessories -> Terminal) and type:

> sudo apt-get update

If it spits anything out, copy / paste that here.

---

### Post by brandknewme on 2007-02-21
This is what it says :
--------------------------------------------------------------------

Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) edgy/main Translation-en_US                   
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) edgy/restricted Translation-en_US             
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) edgy/universe Translation-en_US               
Get:2 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) edgy-updates Release.gpg [191B]             
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) edgy-updates/main Translation-en_US           
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) edgy-updates/restricted Translation-en_US     
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) edgy Release                                  
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) edgy-updates Release                          
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) edgy/main Packages                            
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) edgy/restricted Packages                      
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) edgy/main Sources                             
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) edgy/restricted Sources                       
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) edgy/universe Packages                        
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) edgy-updates/main Packages                    
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) edgy-updates/restricted Packages              
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) edgy-updates/main Sources                     
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) edgy-updates/restricted Sources               
Get:3 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release.gpg [191B]                  
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Translation-en_US                
Get:5 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release [2961B]                     
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Get:6 [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy Release.gpg [191B]             
Ign [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy/stable Translation-en_US         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Hit [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy Release                          
Hit [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy/stable Packages                  
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                        
Get:8 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release.gpg [189B]                    
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn Translation-en_US
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn Translation-en_US
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release 
Get:9 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn Packages [8953B]
99% [9 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn Packages           
  Sub-process bzip2 returned an error code (2)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                  
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn Sources                       
Get:10 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn Packages [8953B]           
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn Sources                       
99% [10 Packages bzip2 0] [Waiting for headers]                     25.2kB/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn Packages                      
  Sub-process bzip2 returned an error code (2)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                         
Fetched 2970B in 10s (291B/s)                                                  
Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/edgy/beryl-svn/binary-i386/Packages.bz2](http://download.tuxfamily.org/3v1deb/dists/edgy/beryl-svn/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/edgy/beryl-svn/binary-i386/Packages.bz2](http://download.tuxfamily.org/3v1deb/dists/edgy/beryl-svn/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by tubasoldier on 2007-02-21
Interesting, It may be that you need to update your sources list? 
but another thing that I would try if I were you would be 
```
sudo apt-get clean
```

---

