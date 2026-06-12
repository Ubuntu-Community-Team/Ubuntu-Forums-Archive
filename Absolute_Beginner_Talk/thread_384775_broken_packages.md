---
title: "broken packages"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by girard on 2007-03-14
what are broken packages? why did they "break"?

the system says that i have one broken package and that i should use the 'broken' filter to locate it.

what is the broken filter and where is it?

how do you fix that? thanks.

---

### Post by pillu on 2007-03-14
can you open up the terminal and type
```
sudo apt-get update
```
and see if that helps

---

### Post by irwa82 on 2007-03-14
Hi,

If you want to fix broken packages using the command line you would use the following:

sudo apt-get -f update

the -f tells apt to try and fix the broken packages.

---

### Post by Toadmund on 2007-03-15
I had the exact same problem, and I believe I have fixed it:) 

In synaptic-->edit-->fix broken packages.

I'll see how it goes.

---

### Post by girard on 2007-03-15
> **irwa82 said:**
> Hi,

If you want to fix broken packages using the command line you would use the following:

sudo apt-get -f update

the -f tells apt to try and fix the broken packages.

tried it already, but the -f has to go after update :) 

actually, i found how to remove broken packages already... it's in the synaptic manager. it automatically notifies you when there are broken packages (i think). but saw it there nevertheless.

going back to sudo update, i get this message:

:~$ sudo apt-get update -f
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                      
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_PH                    
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_PH                      
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_PH                    
Get:3 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]          
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_PH        
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_PH                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_PH                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_PH                  
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_PH              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_PH        
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_PH        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_PH          
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_PH            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_PH      
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                             
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_PH        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_PH      
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_PH             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_PH       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_PH         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_PH       
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources                                
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_PH                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources                  
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
[B]Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources [55.3kB]
99% [7 Sources gzip 0] [Connecting to security.ubuntu.com (82.211.81.138)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources                     
  Sub-process gzip returned an error code (1)[/B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_PH            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_PH      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_PH      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                
Fetched 8B in 8s (1B/s)                                                        
Failed to fetch** [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz)  **Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


i don't really understand this... but does it mean that i cannot download some files from:
[http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz)

i need to but a book about all of this.

---

