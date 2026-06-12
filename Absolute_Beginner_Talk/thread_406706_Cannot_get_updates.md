---
title: "Cannot get updates"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by handyguy33 on 2007-04-11
Hi. I'm having some trouble getting my update manager to work. I've been trying all morning to get my updates but the update manager fails to fetch anything. I tried to get some stuff on automatix and, again, no joy. I tried "sudo apt-get update" and this is what I got as a result:

Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US      
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
  Temporary failure resolving 'security.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release.gpg                              
  Temporary failure resolving 'ca.archive.ubuntu.com'
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                      
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                    
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                             
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Translation-en_US                   
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Translation-en_US             
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/multiverse Translation-en_US             
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg                       
  Temporary failure resolving 'archive.ubuntu.com'
Get:2 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]          
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US        
Get:3 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release [4874B]             
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Translation-en_US               
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release.gpg                           
  Temporary failure resolving 'ubuntu.beryl-project.org'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US            
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US      
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US        
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US      
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Translation-en_US                
  Temporary failure resolving 'ubuntu.beryl-project.org'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release.gpg                      
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Translation-en_US        
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Translation-en_US  
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US  
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Translation-en_US    
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg                      
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
  Temporary failure resolving 'archive.ubuntu.com'
Fetched 5066B in 1m2s (80B/s)         
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg)  Temporary failure resolving 'ca.archive.ubuntu.com'
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'ca.archive.ubuntu.com'
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving 'ca.archive.ubuntu.com'
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2)  Temporary failure resolving 'ca.archive.ubuntu.com'
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving 'ca.archive.ubuntu.com'
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg)  Temporary failure resolving 'ca.archive.ubuntu.com'
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'ca.archive.ubuntu.com'
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving 'ca.archive.ubuntu.com'
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2)  Temporary failure resolving 'ca.archive.ubuntu.com'
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving 'ca.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/Release.gpg](http://ubuntu.beryl-project.org/dists/edgy/Release.gpg)  Temporary failure resolving 'ubuntu.beryl-project.org'
Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/main/i18n/Translation-en_US.bz2](http://ubuntu.beryl-project.org/dists/edgy/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'ubuntu.beryl-project.org'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-en_US.bz2)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2)  Temporary failure resolving 'archive.ubuntu.com'
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas would be appreciated as I'm starting to get frustrated, here.
Thanks

---

### Post by Hendrixski on 2007-04-11
Yeah.... looks like your /etc/apt/sources.list file may be hozed... or your gpg keys.

Perhaps try replacing it with this one:    [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Installing_Additional_Software](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Installing_Additional_Software) 
and don't forget to get the gpg key with the wget thing.


Hope that helps

---

### Post by handyguy33 on 2007-04-12
That did the trick. Thanks a bunch.

---

