---
title: "Screwed up synaptic!"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by fjf on 2007-05-11
I tried to install easyubuntu as described here ([http://ubuntuforums.org/showthread.php?t=430619)](http://ubuntuforums.org/showthread.php?t=430619)).  The first command (wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -) seemed to work (I got no error message, at least!).  The second did not work (sudo mv /usr/lib/easyubuntu/packagelist-edgy.xml /usr/lib/easyubuntu/packagelist-feisty.xml) and the bad thing is that now synaptic does not work and says:

Eynamic MMap ran out of room, Eynamic MMap ran out of room, Eynamic MMap ran out of room, Eynamic MMap ran out of room, Eynamic MMap ran out of room, Eynamic MMap ran out of room, etc.


I could not find anything searching the forum, and I have no clue about what I did wrong (I come from windoze xp).  Anyone could help me fixing this?. Thanks!.

---

### Post by useResa on 2007-05-11
Could you try from a terminal the following command and issue the result
```
sudo apt-get update
```

---

### Post by fjf on 2007-05-11
I get:

Des:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Translation-es                       
Des:2 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-es         
Des:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Translation-es             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Translation-es                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Translation-es                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Translation-es                 
Des:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Translation-es               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Translation-es         
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg                          
  No pude conectarme a antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Conexión rechazada)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Translation-es       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Translation-es         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Translation-es       
Obj [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Des:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-es             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-es       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-es         
Obj [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release                         
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Translation-es                  
  No pude conectarme a antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Conexión rechazada)
Des:6 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]                    
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-es                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-es       
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Translation-es              
  No pude conectarme a antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Conexión rechazada)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg                          
  No pude conectarme a antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Conexión rechazada)
Des:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-es               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-es         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-es           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-es         
Des:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-es              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-es        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-es          
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Translation-es                  
  No pude conectarme a antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Conexión rechazada)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Translation-es              
  No pude conectarme a antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Conexión rechazada)
Des:9 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release [6738B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-es        
Des:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                     
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-es                       
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-es                 
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-es                   
Obj [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-es                 
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release                                   
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release                           
Obj [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages                   
Des:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release [38,4kB]             
Obj [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages             
Obj [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources                    
Obj [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources              
Obj [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages               
Obj [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Obj [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Obj [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release       
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release      
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release               
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages                             
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages                    
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources                           
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources                     
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages                      
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources                       
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages                    
Des:12 [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages [9099B]             
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources   
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources 
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Des:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages [3223B]
Des:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages [14B]
Des:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages [14B]
Des:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages [14B]
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages               
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                 
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages                    
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages              
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Descargados 57,9kB en 6s (9635B/s)                                             
Imposible obtener [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg)  No pude conectarme a antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Conexión rechazada)
Imposible obtener [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-es.bz2](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-es.bz2)  No pude conectarme a antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Conexión rechazada)
Imposible obtener [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-es.bz2](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-es.bz2)  No pude conectarme a antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Conexión rechazada)
Imposible obtener [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg)  No pude conectarme a antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Conexión rechazada)
Imposible obtener [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/i18n/Translation-es.bz2](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/i18n/Translation-es.bz2)  No pude conectarme a antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Conexión rechazada)
Imposible obtener [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/i18n/Translation-es.bz2](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/i18n/Translation-es.bz2)  No pude conectarme a antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Conexión rechazada)
Fallo de segmentación (core dumped)


Whatever that means.  The error messages are in spanish.

No pude conectarme a = couldn't connect to
Conexión rechazada = connection rejected
Imposible obtener = impossible to get
Fallo de segmentación = segmentation failure

---

### Post by dichtbijzee on 2007-05-11
ok, what you could do is edit /etc/apt/sources.list.
all in terminal
first backup: 

```
cp /etc/apt/sources.list  /etc/apt/sources.list.back1
```

then edit sources.list

```
gksudo gedit /etc/apt/sources.list
```

and comment these entries:
[http://antesis.freecontrib.org/mirr*](http://antesis.freecontrib.org/mirr*)

so they look lik this:
#[http://antesis.freecontrib.org/mirr*](http://antesis.freecontrib.org/mirr*)

save and exit gedit.

finally do an update:

```
sudo apt-get update
```

---

### Post by Najand on 2007-05-11
Open a terminal, Run:
```

gksu gedit /etc/apt/sources.list

```
and then put "#" marks before every line starting with " deb http://antesis.freecontrib.org/"
Save it and then run:
```

sudo apt-get update
```

---

### Post by fjf on 2007-05-11
Thaks for your help!.  Still core dumped:

~$ sudo apt-get update
Des:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Translation-es                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Translation-es                 
Des:2 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-es         
Des:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Translation-es             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Translation-es       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Translation-es                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Translation-es                 
Des:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Translation-es               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Translation-es         
Des:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-es             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Translation-es         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Translation-es       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-es       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-es         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-es       
Obj [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Obj [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release                         
Des:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-es           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-es     
Des:7 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]                    
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-es                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-es           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-es         
Des:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-es              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-es        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-es          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-es        
Obj [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Des:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                      
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-es                       
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-es                 
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-es                   
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-es                 
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release                                   
Obj [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages                   
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release                           
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                         
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                          
Obj [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                 
Obj [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages             
Obj [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources                 
Obj [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources           
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages     
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources      
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages 
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources                       
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages                    
Obj [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages            
Obj [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources             
Obj [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages          
Obj [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources           
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources                     
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages            
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages          
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Obj [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages   
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Descargados 9B en 5s (2B/s)  
Fallo de segmentación (core dumped)

---

### Post by Najand on 2007-05-11
Use all of these with the same order:
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update

```

---

### Post by fjf on 2007-05-11
You guys are fast! ;)  I tried, but still core dumped:

fjf@fjf-desktop:~$ sudo apt-get clean
fjf@fjf-desktop:~$ sudo apt-get autoclean
Fallo de segmentación (core dumped)
fjf@fjf-desktop:~$ 

Will I have to reinstall Ubuntu?.  Seems to be resisting all attempts to fix it.

---

### Post by Najand on 2007-05-11
Nah, changed apt-get word with aptitude and try again.

---

### Post by fjf on 2007-05-11
fjf@fjf-desktop:~$ sudo aptitude clean
Fallo de segmentación (core dumped)
fjf@fjf-desktop:~$

---

### Post by Najand on 2007-05-11
Well... open the synaptic and see if there are som broken packages around?

---

### Post by fjf on 2007-05-11
OK, I fixed it.  I just emptied the sources.lst file and re-activated the repositories from synaptic.  Works now.  Thanks for all the help!.

Regards

---

