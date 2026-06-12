---
title: "Nerolinux install problems"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by BigRay5264 on 2007-02-16
I was trying to install Nerolinux and have run into a problem...> bigray5264@Dell-C840:~$ sudo dpkg -i nerolinux-2.1.0.4-x86.deb
(Reading database ... 128358 files and directories currently installed.)
Preparing to replace nerolinux 2.1.0.4-1 (using nerolinux-2.1.0.4-x86.deb) ...
/var/lib/dpkg/info/nerolinux.prerm: 31: Syntax error: "(" unexpected
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 31: Syntax error: "(" unexpected
dpkg: error processing nerolinux-2.1.0.4-x86.deb (--install):
 subprocess new pre-removal script returned error exit status 2
/var/lib/dpkg/info/nerolinux.postinst: 70: Syntax error: "(" unexpected
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 nerolinux-2.1.0.4-x86.deb
bigray5264@Dell-C840:~$ 

opening up Synaptic yields this> E: The package nerolinux needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Is there a command I can use to just remove it?

---

### Post by BigRay5264 on 2007-02-16
In addition I can't use Synaptic until this gets fixed


[IMG]http://www.imageigloo.com/images/1538Screenshot-crop.png[/IMG]

---

### Post by taurus on 2007-02-16
Post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo aptitude update
```

---

### Post by BigRay5264 on 2007-02-16
> **taurus said:**
> Post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo aptitude update
```

here you go

```
bigray5264@Dell-C840:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 http://www.getautomatix.com edgy Release.gpg [189B]
Ign http://www.getautomatix.com edgy/main Translation-en_US
Hit http://www.getautomatix.com edgy Release                                    
Get:2 http://archive.canonical.com edgy-commercial Release.gpg [191B]           
Ign http://archive.canonical.com edgy-commercial/main Translation-en_US         
Ign http://dl.google.com stable Release.gpg                                     
Get:3 http://security.ubuntu.com edgy-security Release.gpg [191B]               
Ign http://security.ubuntu.com edgy-security/main Translation-en_US             
Get:4 http://us.archive.ubuntu.com edgy Release.gpg [191B]                      
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US                    
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US              
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US                
Ign http://us.archive.ubuntu.com edgy/multiverse Translation-en_US              
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US       
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US         
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US       
Ign http://dl.google.com stable/non-free Translation-en_US                      
Hit http://archive.canonical.com edgy-commercial Release                        
Get:5 http://archive.ubuntu.com edgy-backports Release.gpg [191B]               
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US             
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US       
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US         
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US       
Get:6 http://archive.ubuntu.com edgy-security Release.gpg [191B]                
Ign http://archive.ubuntu.com edgy-security/main Translation-en_US              
Ign http://archive.ubuntu.com edgy-security/restricted Translation-en_US        
Ign http://archive.ubuntu.com edgy-security/universe Translation-en_US          
Ign http://archive.ubuntu.com edgy-security/multiverse Translation-en_US        
Hit http://security.ubuntu.com edgy-security Release                            
Get:7 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/multiverse Translation-en_US
Hit http://www.getautomatix.com edgy/main Packages                              
Hit http://dl.google.com stable Release                                         
Get:8 http://archive.ubuntu.com edgy-proposed Release.gpg [191B]                
Ign http://archive.ubuntu.com edgy-proposed/restricted Translation-en_US        
Ign http://archive.ubuntu.com edgy-proposed/main Translation-en_US              
Hit http://us.archive.ubuntu.com edgy Release                                   
Ign http://archive.ubuntu.com edgy-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com edgy-proposed/universe Translation-en_US
Hit http://archive.ubuntu.com edgy-backports Release               
Hit http://archive.ubuntu.com edgy-security Release                
Hit http://us.archive.ubuntu.com edgy-updates Release              
Get:9 http://archive.ubuntu.com edgy-proposed Release [38.4kB]                  
Hit http://dl.google.com stable/non-free Packages                               
Hit http://archive.canonical.com edgy-commercial/main Packages                  
Hit http://security.ubuntu.com edgy-security/main Packages                      
Hit http://security.ubuntu.com edgy-security/restricted Packages                
Hit http://us.archive.ubuntu.com edgy/main Packages                             
Hit http://security.ubuntu.com edgy-security/universe Packages                  
Hit http://us.archive.ubuntu.com edgy/restricted Packages                       
Hit http://us.archive.ubuntu.com edgy/universe Packages                         
Hit http://us.archive.ubuntu.com edgy/multiverse Packages                       
Hit http://security.ubuntu.com edgy-security/multiverse Packages                
Hit http://security.ubuntu.com edgy-security/main Sources            
Hit http://security.ubuntu.com edgy-security/restricted Sources      
Hit http://security.ubuntu.com edgy-security/universe Sources        
Hit http://security.ubuntu.com edgy-security/multiverse Sources      
Hit http://archive.ubuntu.com edgy-backports/main Packages           
Hit http://archive.ubuntu.com edgy-backports/restricted Packages
Hit http://archive.ubuntu.com edgy-backports/universe Packages
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://us.archive.ubuntu.com edgy/main Sources
Hit http://us.archive.ubuntu.com edgy/restricted Sources
Hit http://us.archive.ubuntu.com edgy/universe Sources
Hit http://us.archive.ubuntu.com edgy/multiverse Sources
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://archive.ubuntu.com edgy-security/main Packages
Hit http://archive.ubuntu.com edgy-security/restricted Packages
Hit http://archive.ubuntu.com edgy-security/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://archive.ubuntu.com edgy-security/multiverse Packages
Get:10 http://archive.ubuntu.com edgy-proposed/restricted Packages [14B]
Get:11 http://archive.ubuntu.com edgy-proposed/main Packages [77.0kB]
Hit http://us.archive.ubuntu.com edgy-updates/main Sources                    
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates/universe Sources
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Sources
Get:12 http://archive.ubuntu.com edgy-proposed/multiverse Packages [14B]
Get:13 http://archive.ubuntu.com edgy-proposed/universe Packages [23.4kB]
Get:14 http://archive.ubuntu.com edgy-proposed/restricted Sources [14B]
Get:15 http://archive.ubuntu.com edgy-proposed/main Sources [23.5kB]
Get:16 http://archive.ubuntu.com edgy-proposed/multiverse Sources [14B]
Get:17 http://archive.ubuntu.com edgy-proposed/universe Sources [5240B]
Fetched 168kB in 2s (57.4kB/s)                      
Reading package lists... Done
bigray5264@Dell-C840:~$ 
```

---

### Post by taurus on 2007-02-16
What about

```
sudo aptitude update
```

---

### Post by BigRay5264 on 2007-02-16
> **taurus said:**
> What about

```
sudo aptitude update
```

not sure if I'm giving you what you want? That's the same command as before,right?

```
bigray5264@Dell-C840:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 http://www.getautomatix.com edgy Release.gpg [189B]
Ign http://www.getautomatix.com edgy/main Translation-en_US
Hit http://www.getautomatix.com edgy Release                                    
Hit http://www.getautomatix.com edgy/main Packages                              
Get:2 http://security.ubuntu.com edgy-security Release.gpg [191B]               
Ign http://security.ubuntu.com edgy-security/main Translation-en_US             
Get:3 http://archive.ubuntu.com edgy-backports Release.gpg [191B]               
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US             
Get:4 http://us.archive.ubuntu.com edgy Release.gpg [191B]                      
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US                    
Get:5 http://archive.canonical.com edgy-commercial Release.gpg [191B]           
Ign http://archive.canonical.com edgy-commercial/main Translation-en_US         
Ign http://dl.google.com stable Release.gpg                                     
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US       
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US         
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US       
Hit http://security.ubuntu.com edgy-security Release                            
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US       
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US         
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US       
Get:6 http://archive.ubuntu.com edgy-security Release.gpg [191B]                
Ign http://archive.ubuntu.com edgy-security/main Translation-en_US              
Ign http://archive.ubuntu.com edgy-security/restricted Translation-en_US        
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US              
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US                
Ign http://us.archive.ubuntu.com edgy/multiverse Translation-en_US              
Get:7 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]              
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US            
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US      
Ign http://dl.google.com stable/non-free Translation-en_US                      
Hit http://archive.canonical.com edgy-commercial Release                        
Ign http://archive.ubuntu.com edgy-security/universe Translation-en_US          
Ign http://archive.ubuntu.com edgy-security/multiverse Translation-en_US        
Get:8 http://archive.ubuntu.com edgy-proposed Release.gpg [191B]                
Ign http://archive.ubuntu.com edgy-proposed/restricted Translation-en_US        
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US        
Ign http://us.archive.ubuntu.com edgy-updates/multiverse Translation-en_US      
Hit http://us.archive.ubuntu.com edgy Release                                   
Hit http://us.archive.ubuntu.com edgy-updates Release                           
Hit http://security.ubuntu.com edgy-security/main Packages                      
Ign http://archive.ubuntu.com edgy-proposed/main Translation-en_US              
Ign http://archive.ubuntu.com edgy-proposed/multiverse Translation-en_US        
Ign http://archive.ubuntu.com edgy-proposed/universe Translation-en_US          
Hit http://archive.ubuntu.com edgy-backports Release                            
Hit http://archive.ubuntu.com edgy-security Release                             
Hit http://dl.google.com stable Release                                         
Hit http://security.ubuntu.com edgy-security/restricted Packages                
Hit http://security.ubuntu.com edgy-security/universe Packages                  
Hit http://security.ubuntu.com edgy-security/multiverse Packages                
Hit http://archive.ubuntu.com edgy-proposed Release                             
Hit http://archive.canonical.com edgy-commercial/main Packages                  
Hit http://dl.google.com stable/non-free Packages                               
Hit http://us.archive.ubuntu.com edgy/main Packages                             
Hit http://security.ubuntu.com edgy-security/main Sources                       
Hit http://security.ubuntu.com edgy-security/restricted Sources     
Hit http://security.ubuntu.com edgy-security/universe Sources       
Hit http://security.ubuntu.com edgy-security/multiverse Sources     
Hit http://archive.ubuntu.com edgy-backports/main Packages          
Hit http://us.archive.ubuntu.com edgy/restricted Packages           
Hit http://us.archive.ubuntu.com edgy/universe Packages
Hit http://us.archive.ubuntu.com edgy/multiverse Packages
Hit http://archive.ubuntu.com edgy-backports/restricted Packages    
Hit http://archive.ubuntu.com edgy-backports/universe Packages      
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages    
Hit http://us.archive.ubuntu.com edgy/main Sources                  
Hit http://us.archive.ubuntu.com edgy/restricted Sources
Hit http://us.archive.ubuntu.com edgy/universe Sources
Hit http://us.archive.ubuntu.com edgy/multiverse Sources
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates/universe Sources
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Sources
Hit http://archive.ubuntu.com edgy-security/main Packages
Hit http://archive.ubuntu.com edgy-security/restricted Packages
Hit http://archive.ubuntu.com edgy-security/universe Packages
Hit http://archive.ubuntu.com edgy-security/multiverse Packages
Hit http://archive.ubuntu.com edgy-proposed/restricted Packages
Hit http://archive.ubuntu.com edgy-proposed/main Packages
Hit http://archive.ubuntu.com edgy-proposed/multiverse Packages
Hit http://archive.ubuntu.com edgy-proposed/universe Packages
Hit http://archive.ubuntu.com edgy-proposed/restricted Sources
Hit http://archive.ubuntu.com edgy-proposed/main Sources
Hit http://archive.ubuntu.com edgy-proposed/multiverse Sources
Hit http://archive.ubuntu.com edgy-proposed/universe Sources
Fetched 8B in 2s (4B/s)  
Reading package lists... Done
bigray5264@Dell-C840:~$ 

```

---

### Post by taurus on 2007-02-16
Actually, I meant

```
sudo aptitude upgrade
```

---

### Post by BigRay5264 on 2007-02-16
> **taurus said:**
> Actually, I meant

```
sudo aptitude upgrade
```

```
bigray5264@Dell-C840:~$ sudo aptitude upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  automatix2 imagemagick libmagick9 tzdata 
4 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 12.3kB will be used.
Do you want to continue? [Y/n/?]
```

not sure if I should of said Y or not

---

### Post by BigRay5264 on 2007-02-16
also I get this if I try to reinstall the package

[IMG]http://img47.imageshack.us/img47/5460/screenshot2cropwp3.png[/IMG]

---

### Post by taurus on 2007-02-16
You need to answer **Y** to that question.

---

### Post by BigRay5264 on 2007-02-16
> **taurus said:**
> You need to answer **Y** to that question.

```
bigray5264@Dell-C840:~$ sudo aptitude upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  automatix2 imagemagick libmagick9 tzdata 
4 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 12.3kB will be used.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate file for the nerolinux package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
bigray5264@Dell-C840:~$ 

```

---

### Post by taurus on 2007-02-16
```
sudo dpkg -r nerolinux
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by BigRay5264 on 2007-02-16
> **taurus said:**
> ```
sudo dpkg -r nerolinux
sudo aptitude update
sudo aptitude upgrade
```

```
bigray5264@Dell-C840:~$ sudo dpkg -r nerolinux
dpkg: error processing nerolinux (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 nerolinux
bigray5264@Dell-C840:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 http://www.getautomatix.com edgy Release.gpg [189B]
Ign http://www.getautomatix.com edgy/main Translation-en_US
Hit http://www.getautomatix.com edgy Release                                    
Get:2 http://archive.canonical.com edgy-commercial Release.gpg [191B]           
Ign http://archive.canonical.com edgy-commercial/main Translation-en_US         
Hit http://www.getautomatix.com edgy/main Packages                              
Get:3 http://archive.ubuntu.com edgy-backports Release.gpg [191B]               
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US             
Hit http://archive.canonical.com edgy-commercial Release                        
Get:4 http://security.ubuntu.com edgy-security Release.gpg [191B]               
Ign http://security.ubuntu.com edgy-security/main Translation-en_US             
Get:5 http://us.archive.ubuntu.com edgy Release.gpg [191B]                      
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US                    
Ign http://dl.google.com stable Release.gpg                                     
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US       
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US         
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US       
Get:6 http://archive.ubuntu.com edgy-security Release.gpg [191B]                
Ign http://archive.ubuntu.com edgy-security/main Translation-en_US              
Ign http://archive.ubuntu.com edgy-security/restricted Translation-en_US        
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US       
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US         
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US       
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US              
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US                
Ign http://us.archive.ubuntu.com edgy/multiverse Translation-en_US              
Get:7 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]              
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US            
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US      
Hit http://security.ubuntu.com edgy-security Release                            
Ign http://dl.google.com stable/non-free Translation-en_US                      
Hit http://archive.canonical.com edgy-commercial/main Packages                  
Ign http://archive.ubuntu.com edgy-security/universe Translation-en_US          
Ign http://archive.ubuntu.com edgy-security/multiverse Translation-en_US        
Get:8 http://archive.ubuntu.com edgy-proposed Release.gpg [191B]                
Ign http://archive.ubuntu.com edgy-proposed/restricted Translation-en_US        
Ign http://archive.ubuntu.com edgy-proposed/main Translation-en_US              
Ign http://archive.ubuntu.com edgy-proposed/multiverse Translation-en_US        
Ign http://archive.ubuntu.com edgy-proposed/universe Translation-en_US          
Hit http://archive.ubuntu.com edgy-backports Release                            
Hit http://archive.ubuntu.com edgy-security Release                             
Hit http://dl.google.com stable Release                                         
Hit http://archive.ubuntu.com edgy-proposed Release                             
Hit http://security.ubuntu.com edgy-security/main Packages                      
Hit http://dl.google.com stable/non-free Packages                               
Hit http://archive.ubuntu.com edgy-backports/main Packages                      
Hit http://security.ubuntu.com edgy-security/restricted Packages                
Hit http://security.ubuntu.com edgy-security/universe Packages       
Hit http://security.ubuntu.com edgy-security/multiverse Packages     
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com edgy Release                        
Hit http://archive.ubuntu.com edgy-backports/restricted Packages     
Hit http://archive.ubuntu.com edgy-backports/universe Packages       
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages     
Hit http://security.ubuntu.com edgy-security/main Sources                       
Hit http://security.ubuntu.com edgy-security/restricted Sources                 
Hit http://security.ubuntu.com edgy-security/universe Sources                   
Hit http://security.ubuntu.com edgy-security/multiverse Sources                 
Hit http://archive.ubuntu.com edgy-security/main Packages                       
Hit http://archive.ubuntu.com edgy-security/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates Release
Hit http://archive.ubuntu.com edgy-security/universe Packages       
Hit http://archive.ubuntu.com edgy-security/multiverse Packages     
Hit http://archive.ubuntu.com edgy-proposed/restricted Packages     
Hit http://archive.ubuntu.com edgy-proposed/main Packages           
Hit http://archive.ubuntu.com edgy-proposed/multiverse Packages     
Hit http://us.archive.ubuntu.com edgy/main Packages                 
Hit http://archive.ubuntu.com edgy-proposed/universe Packages       
Hit http://archive.ubuntu.com edgy-proposed/restricted Sources      
Hit http://archive.ubuntu.com edgy-proposed/main Sources            
Hit http://archive.ubuntu.com edgy-proposed/multiverse Sources      
Hit http://archive.ubuntu.com edgy-proposed/universe Sources
Hit http://us.archive.ubuntu.com edgy/restricted Packages
Hit http://us.archive.ubuntu.com edgy/universe Packages
Hit http://us.archive.ubuntu.com edgy/multiverse Packages
Hit http://us.archive.ubuntu.com edgy/main Sources
Hit http://us.archive.ubuntu.com edgy/restricted Sources
Hit http://us.archive.ubuntu.com edgy/universe Sources
Hit http://us.archive.ubuntu.com edgy/multiverse Sources
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates/universe Sources
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Sources
Fetched 8B in 1s (6B/s)  
Reading package lists... Done
bigray5264@Dell-C840:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  automatix2 imagemagick libmagick9 tzdata 
4 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 12.3kB will be used.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate file for the nerolinux package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
bigray5264@Dell-C840:~$ 
```

---

### Post by taurus on 2007-02-16
```
sudo aptitude --purge remove nerolinux
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by BigRay5264 on 2007-02-16
> **taurus said:**
> ```
sudo aptitude --purge remove nerolinux
sudo aptitude update
sudo aptitude upgrade
```

does it matter if entering commands all at once or individually?

```
bigray5264@Dell-C840:~$ sudo aptitude --purge remove nerolinux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  imagemagick 
The following packages have been kept back:
  automatix2 libmagick9 tzdata 
The following packages will be REMOVED:
  nerolinux 
0 packages upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
dpkg: error processing nerolinux (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Errors were encountered while processing:
 nerolinux
Aborted (core dumped)
bigray5264@Dell-C840:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Ign http://dl.google.com stable Release.gpg                                     
Ign http://dl.google.com stable/non-free Translation-en_US                      
Hit http://dl.google.com stable Release                                         
Hit http://dl.google.com stable/non-free Packages                               
Get:1 http://archive.canonical.com edgy-commercial Release.gpg [191B]           
Ign http://archive.canonical.com edgy-commercial/main Translation-en_US         
Get:2 http://archive.ubuntu.com edgy-backports Release.gpg [191B]               
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US             
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US       
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US         
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US       
Get:3 http://us.archive.ubuntu.com edgy Release.gpg [191B]                      
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US                    
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US              
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US                
Ign http://us.archive.ubuntu.com edgy/multiverse Translation-en_US              
Get:4 http://security.ubuntu.com edgy-security Release.gpg [191B]               
Ign http://security.ubuntu.com edgy-security/main Translation-en_US             
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US       
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US         
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US       
Get:5 http://www.getautomatix.com edgy Release.gpg [189B]                       
Ign http://www.getautomatix.com edgy/main Translation-en_US                     
Get:6 http://archive.ubuntu.com edgy-security Release.gpg [191B]                
Ign http://archive.ubuntu.com edgy-security/main Translation-en_US
Ign http://archive.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://archive.ubuntu.com edgy-security/universe Translation-en_US
Ign http://archive.ubuntu.com edgy-security/multiverse Translation-en_US
Get:7 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]              
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US            
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US      
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US        
Ign http://us.archive.ubuntu.com edgy-updates/multiverse Translation-en_US      
Hit http://www.getautomatix.com edgy Release                                    
Hit http://us.archive.ubuntu.com edgy Release                                   
Hit http://security.ubuntu.com edgy-security Release                            
Hit http://archive.canonical.com edgy-commercial Release                        
Get:8 http://archive.ubuntu.com edgy-proposed Release.gpg [191B]                
Ign http://archive.ubuntu.com edgy-proposed/restricted Translation-en_US        
Ign http://archive.ubuntu.com edgy-proposed/main Translation-en_US              
Ign http://archive.ubuntu.com edgy-proposed/multiverse Translation-en_US        
Ign http://archive.ubuntu.com edgy-proposed/universe Translation-en_US
Hit http://archive.ubuntu.com edgy-backports Release
Hit http://archive.ubuntu.com edgy-security Release
Hit http://us.archive.ubuntu.com edgy-updates Release              
Hit http://archive.ubuntu.com edgy-proposed Release                
Hit http://www.getautomatix.com edgy/main Packages
Hit http://us.archive.ubuntu.com edgy/main Packages                
Hit http://security.ubuntu.com edgy-security/main Packages                      
Hit http://us.archive.ubuntu.com edgy/restricted Packages                       
Hit http://us.archive.ubuntu.com edgy/universe Packages             
Hit http://us.archive.ubuntu.com edgy/multiverse Packages           
Hit http://archive.canonical.com edgy-commercial/main Packages                  
Hit http://security.ubuntu.com edgy-security/restricted Packages                
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://us.archive.ubuntu.com edgy/main Sources                   
Hit http://us.archive.ubuntu.com edgy/restricted Sources             
Hit http://us.archive.ubuntu.com edgy/universe Sources               
Hit http://us.archive.ubuntu.com edgy/multiverse Sources             
Hit http://archive.ubuntu.com edgy-backports/main Packages           
Hit http://security.ubuntu.com edgy-security/multiverse Packages
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://security.ubuntu.com edgy-security/universe Sources
Hit http://security.ubuntu.com edgy-security/multiverse Sources
Hit http://archive.ubuntu.com edgy-backports/restricted Packages
Hit http://archive.ubuntu.com edgy-backports/universe Packages
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://archive.ubuntu.com edgy-security/main Packages           
Hit http://archive.ubuntu.com edgy-security/restricted Packages
Hit http://archive.ubuntu.com edgy-security/universe Packages
Hit http://archive.ubuntu.com edgy-security/multiverse Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://archive.ubuntu.com edgy-proposed/restricted Packages
Hit http://archive.ubuntu.com edgy-proposed/main Packages
Hit http://archive.ubuntu.com edgy-proposed/multiverse Packages
Hit http://archive.ubuntu.com edgy-proposed/universe Packages
Hit http://archive.ubuntu.com edgy-proposed/restricted Sources
Hit http://archive.ubuntu.com edgy-proposed/main Sources
Hit http://archive.ubuntu.com edgy-proposed/multiverse Sources
Hit http://archive.ubuntu.com edgy-proposed/universe Sources
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates/universe Sources
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Sources
Fetched 8B in 3s (2B/s)  
Reading package lists... Done
bigray5264@Dell-C840:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  automatix2 imagemagick libmagick9 tzdata 
4 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 12.3kB will be used.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate file for the nerolinux package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
bigray5264@Dell-C840:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  automatix2 imagemagick libmagick9 tzdata 
4 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 12.3kB will be used.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate file for the nerolinux package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
bigray5264@Dell-C840:~$ 

```

---

### Post by old_geekster on 2007-02-16
If you haven't done so, you should try Gnomebaker.  It is a CD/DVD burner that has a great GUI interface.  I have read good things about it and have used it myself.

Try it, you may just not want to try NeroLinux.

---

### Post by BigRay5264 on 2007-02-16
> **old_geekster said:**
> If you haven't done so, you should try Gnomebaker.  It is a CD/DVD burner that has a great GUI interface.  I have read good things about it and have used it myself.

Try it, you may just not want to try NeroLinux.

You know what? At this point I'm just looking to get Nerolinux off my machine and be back to a normal state.I can't even use Synaptic at this point

---

### Post by BigRay5264 on 2007-02-16
Why do I see a Ubuntu reinstall in my future? :confused:

---

### Post by socngill on 2007-02-16
Somebody with the same problem!  Any ideas how to just remove it?  It doesn't show up in the add/remove option either?  Which is a bit wierd.  If there is an easy way to uninstall programs it would be great as I keep getting errors with Wine as well - in fact it was trying to uninstall Wine that brought up this error with Nero Linux.  So advice on getting Wine to work would be great as well ;)

---

### Post by BigRay5264 on 2007-02-16
The worst part is I can't update or install any packages until this is resolved...I really don't want to start over again from scratch...just got everything working right

---

### Post by socngill on 2007-02-16
> **BigRay5264 said:**
> The worst part is I can't update or install any packages until this is resolved...I really don't want to start over again from scratch...just got everything working right

I have exactly the same problem.  Everytime I try to update anything that bloody error message pops up!!  Like you it's taken me about a week of tweaking to get Ubuntu the way I want it and the last thing I want to do is start over again.

Does it not have a roll back function????  Or am I showing my Windows background!!

---

### Post by MrKlean on 2007-02-16
I prefer K3B over NeroLinux....just my thots ; )

---

### Post by socngill on 2007-02-16
> **MrKlean said:**
> I prefer K3B over NeroLinux....just my thots ; )

Your thoughts are most welcome (and I shall probably not bother with Nero after this fiasco!) but do you know how to solve our problem?  We can't delete NeroLinux and get rid of this annoying error message.

---

### Post by szabog555 on 2007-02-16
"Dirty" solution:

In /var/lib/dpkg/info, edit the following files (you need sudo to do this):
nerolinux.postinst
nerolinux.prerm

Delete the words "function" from those files. (Not the lines containing it!)

Run sudo dpkg --remove nerolinux

nerolinux is away, synaptic works....

Regards,
Gabor

---

### Post by Shay Stephens on 2007-02-16
As someone who used nero on windows, and then then nerolinux on ubuntu, I can safely say that gnomebaker is not a full substitute for nero.  gnomebaker does not have any data verification at all.  After messing around for a while, I have settled on K3b.  It offers all the basics of nero and does data verification.  Since switching to K3b, I have not need nerolinux for anything.

---

### Post by 1001001 on 2007-02-16
I am having the same problems installing and uninstalling nerolinux 2.1.0.4

I still had nerolinux-2.1.0.3-x86.deb on my hard drive so I decided to extract the files and use the diff command to see what changes were made to the files that were giving me errors (nerolinux.postinst and nerolinux.prerm)

It seems nerolinux 2.1.0.4 scripts use () after the function name while 2.1.0.3 did not.

For example:
version 2.1.0.4 ==> function CreateDesktopFile()

version 2.1.0.3 ==> function CreateDesktopFile

I am not a script expert so I don't know if this is the reason for all the problems. All I know is after I removed the "()" from the function names, I was able to remove nerolinux 2.1.0.4.

I have gone back to using 2.1.0.3 which is not giving me any problems. 

I actually like nerolinux. I have created 100s of CD with no errors. Great program in Windows and in Ubuntu. Hope they fix the problems with 2.1.0.4.

---

### Post by CodyJarrett on 2007-02-17
This command finally got rid of the cursed thing for me:
```
sudo dpkg --remove --force-depends --force-remove-reinstreq nerolinux
```

you might need to remove all files beginning with nerolinux from the /var/lib/dpkg/info/ folder.

Hope this helps.

---

### Post by zvacet on 2007-02-18
I see you allways get the same question:¨are you root&#733;witch probably means you are not.Try type sudo -i,and after that give the comand.Did you looked in usr/bin?maybe there is uninstall file,but you have to be root.that all I can think of,cose I uninstall nero with synaptic with no problem.

---

### Post by yabbadabbadont on 2007-02-18
I have found that the best way to upgrade nerolinux is to completely remove the previous version first, then install the new one.  I've never had any problems doing it that way.

sudo apt-get --purge remove nerolinux
sudo dpkg -i newnerolinuxpackagenamehere

Your ~/.nerorc will still be there with your license key and settings but it is still a good idea to check your preferences once you run the new version.

---

### Post by Jphenow on 2007-02-18
> **szabog555 said:**
> "Dirty" solution:

In /var/lib/dpkg/info, edit the following files (you need sudo to do this):
nerolinux.postinst
nerolinux.prerm

Delete the words "function" from those files. (Not the lines containing it!)

Run sudo dpkg --remove nerolinux

nerolinux is away, synaptic works....

Regards,
Gabor

how the heck do you get into sudo, and edit these files, only way I would know is through a terminal and i dont know how to mess with files once there

---

### Post by Maestro23 on 2007-02-18
> **Jphenow said:**
> how the heck do you get into sudo, and edit these files, only way I would know is through a terminal and i dont know how to mess with files once there

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Files and directories in "/" are owned by [COLOR="Red"]root[/COLOR].  You need to use "sudo" with your terminal commands to edit them.

This site will introduce you to basic terminal commands and Linux directory/file structure: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by yabbadabbadont on 2007-02-18
> In /var/lib/dpkg/info, edit the following files (you need sudo to do this):
nerolinux.postinst
nerolinux.prerm

Delete the words "function" from those files. (Not the lines containing it!)

Run sudo dpkg --remove nerolinux

Assuming that you are using Gnome, open a terminal window.
```
cd /var/lib/dpkg/info
sudo gedit nerolinux.postinst

Make the edits suggested above, that is, edit out the word "function" 
wherever it appears in the file, but not the entire line that it appears in.  
Save the file after you have changed it and exit.

sudo gedit nerolinux.prerm

Do the same thing to this file, save your changes and exit.

sudo dpkg --remove nerolinux
```
NOTE: I have not done this myself as I have no need to.  
I am just trying to explain his instructions.  Good luck.  :D

---

### Post by ramjet_1953 on 2007-02-18
Hi, Guys!

For what it's worth, IMHO,  I really don't know why you are bothering with Nero Linux anyway.

It is functionally and visually inferior to K3b and K9copy.

I tried Nero Linux, but ditched it after trying K3b and K9copy. They work fine under both GNOME and KDE.

Also K9 copy allows you to shrink a DVD9 onto a DVD5 with no noticeable loss of picture quality.

Regards,
Roger  :cool:

---

### Post by yabbadabbadont on 2007-02-18
> **ramjet_1953 said:**
> Hi, Guys!

For what it's worth, IMHO,  I really don't know why you are bothering with Nero Linux anyway.

It is functionally and visually inferior to K3b and K9copy.

I tried Nero Linux, but ditched it after trying K3b and K9copy. They work fine under both GNOME and KDE.

Also K9 copy allows you to shrink a DVD9 onto a DVD5 with no noticeable loss of picture quality.

Regards,
Roger  :cool:

In my case, nerolinux always works with my two burners.  Cdrecord, which is used by almost all OSS GUI frontends (including k3b), fails most of the time with my drives.  Older versions of cdrecord used to work with them and growisofs still works, but not the current versions of cdrecord used by most Linux distributions.  Plus, I already had a license for it from the windows versions.  Also, I don't care to install the kde libs.

---

### Post by hukeli on 2007-02-19
The reason of this problem is that on Ubuntu Edgy /bin/sh points to /bin/dash instead of /bin/bash by default, and NeroLinux's install scripts probably use some bash-specific features. So you just need to extracted the deb and modified the install/remove scripts by altering the first line to #!/bin/bash, then repacked the deb and install it, this should solve the problem, and you can use NeroLinux again.

p.s., for exact steps, see here: [http://blog.keli.info/view/19](http://blog.keli.info/view/19)

---

### Post by acascianelli on 2007-02-19
> **CodyJarrett said:**
> This command finally got rid of the cursed thing for me:
```
sudo dpkg --remove --force-depends --force-remove-reinstreq nerolinux
```

you might need to remove all files beginning with nerolinux from the /var/lib/dpkg/info/ folder.

Hope this helps.

I had the same problem, this fixed mine.  It's weird cause I have Nerolinux working on my other Edgy system at work just fine.

---

### Post by yabbadabbadont on 2007-02-19
Wouldn't it be simpler to use update-alternatives to change the default shell back to bash?  (the sane choice :D)

---

### Post by hukeli on 2007-02-19
> **yabbadabbadont said:**
> Wouldn't it be simpler to use update-alternatives to change the default shell back to bash?  (the sane choice :D)

yes, that would be easier :-) 

though dash is much faster and more memory efficient than bash, so some people might prefer to keep it as the default shell.

---

### Post by yabbadabbadont on 2007-02-19
> **hukeli said:**
> yes, that would be easier :-) 

though dash is much faster and more memory efficient than bash, so some people might prefer to keep it as the default shell.

That doesn't do them much good when every install/utility/program script pretty much in existence assumes it is using bash...  (which is very bad of the script writers.  Bad scripters!  Bad scripters!  <thwaps them on the nose with rolled up newspaper>  That'll teach em.  :lol:)

---

### Post by MrKlean on 2007-02-19
Yabba, me thinks you have too much time on yer hands LOL!!   There was an article donw comparing NeroLinux to K3B...and K3B was rated far superior.... if any one cares ; )  I tried them both, in fact the others too.... and I agree...K3B works best for me ; )

---

### Post by yabbadabbadont on 2007-02-19
> **MrKlean said:**
> Yabba, me thinks you have too much time on yer hands LOL!!   There was an article donw comparing NeroLinux to K3B...and K3B was rated far superior.... if any one cares ; )  I tried them both, in fact the others too.... and I agree...K3B works best for me ; )

Exactly, K3B works best for you, not for me however.  Like I said eariler, K3B (via cdrecord) makes coasters with my two drives between 40 to 60 percent of the time (depending on which drive it is).  Don't get me wrong, I like K3B and used to use it religiously.  It is cdrecord that gives me problems.  In the end it just comes down to, "use whatever works."  :D

---

### Post by thegreath on 2007-03-20
> **acascianelli said:**
> I had the same problem, this fixed mine.  It's weird cause I have Nerolinux working on my other Edgy system at work just fine.

I also had the same problem, except with resolvconf. I just replaced the nerolinux at the end with resolvconf and it fixed the problem.

I just typed in terminal:

sudo dpkg --remove --force-depends --force-remove-reinstreq resolvconf

---

