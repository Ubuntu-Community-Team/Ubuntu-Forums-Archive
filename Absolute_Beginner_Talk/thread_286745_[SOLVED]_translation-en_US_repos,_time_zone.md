---
title: "[SOLVED] translation-en_US repos, time zone"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by forger on 2006-10-28
question number 1:
How can i disable these translation-en_US repositories? I think ign means ignore and frankly I don't know why or how they appeared after upgrading to edgy eft. they were Translation-en_AU, but I managed to change it from the choose language from the logon screen and added these in /etc/environment:
```

LANG="en_US.UTF-8"
LANGUAGE="en_US:en"
LC_ALL="en_US.UTF-8"

```

this is how my apt-get update looks right now:
```
Get:1 http://se.archive.ubuntu.com edgy Release.gpg [191B]                     
Ign http://se.archive.ubuntu.com edgy/main Translation-en_US                   
Get:2 http://archive.canonical.com dapper-commercial Release.gpg [191B]        
Ign http://archive.canonical.com dapper-commercial/main Translation-en_US      
Get:3 http://www.getautomatix.com edgy Release.gpg [189B]                      
Ign http://www.getautomatix.com edgy/main Translation-en_US                    
Get:4 http://archive.ubuntu.com edgy-backports Release.gpg [189B]              
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US            
Get:5 http://security.ubuntu.com edgy-security Release.gpg [189B]              
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Ign http://se.archive.ubuntu.com edgy/restricted Translation-en_US             
Ign http://se.archive.ubuntu.com edgy/universe Translation-en_US               
Ign http://se.archive.ubuntu.com edgy/multiverse Translation-en_US             
Get:6 http://se.archive.ubuntu.com edgy-updates Release.gpg [189B]             
Ign http://se.archive.ubuntu.com edgy-updates/main Translation-en_US           
Ign http://wine.lowvoice.nl dapper Release.gpg                                 
Ign http://wine.lowvoice.nl dapper/main Translation-en_US                      
Hit http://archive.canonical.com dapper-commercial Release                     
Hit http://www.getautomatix.com edgy Release                                   
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US      
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US        
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US      
Get:7 http://archive.ubuntu.com edgy-updates Release.gpg [189B]                
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US              
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US        
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Hit http://security.ubuntu.com edgy-security Release                           
Ign http://se.archive.ubuntu.com edgy-updates/restricted Translation-en_US     
Ign http://se.archive.ubuntu.com edgy-updates/universe Translation-en_US       
Ign http://se.archive.ubuntu.com edgy-updates/multiverse Translation-en_US     
Hit http://se.archive.ubuntu.com edgy Release                                  
Hit http://se.archive.ubuntu.com edgy-updates Release                          
Hit http://archive.canonical.com dapper-commercial/main Packages               
Hit http://wine.lowvoice.nl dapper Release                                     
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US          
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US        
Get:8 http://archive.ubuntu.com edgy-security Release.gpg [189B]               
Ign http://archive.ubuntu.com edgy-security/main Translation-en_US             
Hit http://www.getautomatix.com edgy/main Packages                             
Ign http://archive.ubuntu.com edgy-security/restricted Translation-en_US       
Ign http://archive.ubuntu.com edgy-security/universe Translation-en_US         
Hit http://security.ubuntu.com edgy-security/main Packages                     
Hit http://se.archive.ubuntu.com edgy/main Packages                            
Hit http://se.archive.ubuntu.com edgy/restricted Packages                      
Hit http://se.archive.ubuntu.com edgy/main Sources                             
Hit http://se.archive.ubuntu.com edgy/restricted Sources                       
Ign http://archive.ubuntu.com edgy-security/multiverse Translation-en_US       
Get:9 http://archive.ubuntu.com edgy Release.gpg [191B]                        
Ign http://archive.ubuntu.com edgy/main Translation-en_US                      
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US                
Ign http://wine.lowvoice.nl dapper/main Packages                               
Ign http://archive.ubuntu.com edgy/universe Translation-en_US                  
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US                
Hit http://archive.ubuntu.com edgy-backports Release                           
Hit http://archive.ubuntu.com edgy-updates Release                             
Hit http://security.ubuntu.com edgy-security/restricted Packages               
Hit http://security.ubuntu.com edgy-security/main Sources                      
Hit http://security.ubuntu.com edgy-security/restricted Sources                
Hit http://se.archive.ubuntu.com edgy/universe Packages                        
Hit http://se.archive.ubuntu.com edgy/multiverse Packages            
Hit http://se.archive.ubuntu.com edgy/universe Sources               
Hit http://se.archive.ubuntu.com edgy/multiverse Sources             
Hit http://se.archive.ubuntu.com edgy-updates/main Packages          
Hit http://se.archive.ubuntu.com edgy-updates/restricted Packages    
Hit http://se.archive.ubuntu.com edgy-updates/main Sources           
Hit http://se.archive.ubuntu.com edgy-updates/restricted Sources     
Hit http://archive.ubuntu.com edgy-security Release                  
Hit http://archive.ubuntu.com edgy Release                                     
Hit http://wine.lowvoice.nl dapper/main Packages                               
Hit http://se.archive.ubuntu.com edgy-updates/universe Packages                
Hit http://se.archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://se.archive.ubuntu.com edgy-updates/universe Sources
Hit http://se.archive.ubuntu.com edgy-updates/multiverse Sources
Hit http://archive.ubuntu.com edgy-backports/main Packages
Hit http://archive.ubuntu.com edgy-backports/restricted Packages
Hit http://archive.ubuntu.com edgy-backports/universe Packages
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://archive.ubuntu.com edgy-updates/main Packages
Hit http://archive.ubuntu.com edgy-updates/restricted Packages
Hit http://archive.ubuntu.com edgy-updates/universe Packages
Hit http://archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://archive.ubuntu.com edgy-security/main Packages
Hit http://archive.ubuntu.com edgy-security/restricted Packages
Hit http://archive.ubuntu.com edgy-security/universe Packages
Hit http://archive.ubuntu.com edgy-security/multiverse Packages
Hit http://archive.ubuntu.com edgy/main Packages
Hit http://archive.ubuntu.com edgy/restricted Packages
Hit http://archive.ubuntu.com edgy/universe Packages
Hit http://archive.ubuntu.com edgy/multiverse Packages

```

question number 2:
My time zone is Europe/Belgrade, and every time I change it, it goes back to Europe/Sarajevo. Why? I have periodic ntp set to yu.europe.pool.ntp.org

---

### Post by joensson on 2006-11-01
Try 
```
sudo dpkg-reconfigure locales
```

I also did an ```
unset LANG LANGUAGE
``` before running the above reconfigure, but I'm not sure it is necessary.

/J

---

### Post by forger on 2006-11-01
> **joensson said:**
> Try 
```
sudo dpkg-reconfigure locales
```

I also did an ```
unset LANG LANGUAGE
``` before running the above reconfigure, but I'm not sure it is necessary.

/J

this worked:
```
unset LANG LANGUAGE
```
thanks a lot :)

---

### Post by forger on 2006-11-03
> **forger said:**
> this worked:
```
unset LANG LANGUAGE
```
thanks a lot :)

er.. actually it does work for one session, when i close terminal it keeps resetting it :\
and the reconfiguration didn't actually do anything

---

### Post by purana on 2006-11-29
I just did a fresh install of xubuntu 6.10 and have come across the same problem. I added a new sources.list and everytime I apt-get update it errors with a few lines appended like so;

```

root@barney:~# apt-get update
Get:1 http://ftp.iinet.net.au edgy Release.gpg [191B]
Ign http://ftp.iinet.net.au edgy/main Translation-en_AU
Ign http://ftp.iinet.net.au edgy/restricted Translation-en_AU
Ign http://ftp.iinet.net.au edgy/universe Translation-en_AU
Ign http://ftp.iinet.net.au edgy/multiverse Translation-en_AU
Get:2 http://ftp.iinet.net.au edgy-updates Release.gpg [189B]
Ign http://ftp.iinet.net.au edgy-updates/main Translation-en_AU
Ign http://ftp.iinet.net.au edgy-updates/restricted Translation-en_AU
Ign http://ftp.iinet.net.au edgy-updates/universe Translation-en_AU
Ign http://ftp.iinet.net.au edgy-updates/multiverse Translation-en_AU
Get:3 http://ftp.iinet.net.au edgy-security Release.gpg [191B]
Ign http://ftp.iinet.net.au edgy-security/main Translation-en_AU
Ign http://ftp.iinet.net.au edgy-security/restricted Translation-en_AU
Ign http://ftp.iinet.net.au edgy-security/universe Translation-en_AU
Ign http://ftp.iinet.net.au edgy-security/multiverse Translation-en_AU

```

If I unset the environment variables as per other poster it fixes it. But why do I need to undo that when other friends who have installed the same way have no such problem and leave those variables intact.

Anyone got ideas?

---

### Post by yanychar on 2008-05-16
> **purana said:**
> Anyone got ideas?

this line in /etc/apt/apt.conf helps in Debian unstable
```

APT::Acquire::Translation "none";

```

---

### Post by jniebles on 2008-05-17
> **yanychar said:**
> this line in /etc/apt/apt.conf helps in Debian unstable
```

APT::Acquire::Translation "none";

```

this also disables the Translation-en_US in hardy.

thanks.

---

