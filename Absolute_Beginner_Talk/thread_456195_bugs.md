---
title: "bugs"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-05-27
```
zerobinary@zerobinary:~$ sudo apt-get install postgresql-8.2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
postgresql-8.2 is already the newest version.
postgresql-8.2 set to manual installed.
The following packages were automatically installed and are no longer required:
  artsbuilder python-kiwi libgtk-jni libpcrecpp0 libcairo-java
  libbluetooth2-dev libusb-dev librpcsecgss2 libjasper-runtime libgmp3c2
  libxml++2.6c2a libglib-java docker python-setuptools libpq4 gazpacho
  libgconfmm-2.6-1c2 mkvtoolnix libswt3.2-gtk-jni libimlib2 multisync
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up postgresql-8.2 (8.2.4-1~edgy1) ...
 * Starting PostgreSQL 8.2 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2007-05-23 18:06:52 PDT LOG:  could not load root certificate file "root.crt": no SSL error reported
2007-05-23 18:06:52 PDT DETAIL:  Will not verify client certificates.
2007-05-23 18:06:53 PDT LOG:  could not translate host name "localhost", service "5432" to address: Name or service not known
2007-05-23 18:06:53 PDT WARNING:  could not create listen socket for "localhost"
2007-05-23 18:06:53 PDT FATAL:  could not create any TCP/IP sockets
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.2, action "start" failed.
dpkg: error processing postgresql-8.2 (--configure):
```
```
E: postgresql-8.2: subprocess post-installation script returned error exit status 1
E: postgresql-plpython-8.2: dependency problems - leaving unconfigured
E: glom: dependency problems - leaving unconfigured
E: postgresql-contrib-8.2: dependency problems - leaving unconfigured
```
```
zerobinary@zerobinary:~$  sudo apt-get install pgadmin3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  artsbuilder python-kiwi libgtk-jni libpcrecpp0 libcairo-java
  libbluetooth2-dev libusb-dev librpcsecgss2 libjasper-runtime libgmp3c2
  libglib-java docker python-setuptools gazpacho mkvtoolnix libswt3.2-gtk-jni
  libimlib2 multisync
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  pgadmin3-data
Recommended packages:
  pgagent
The following NEW packages will be installed:
  pgadmin3 pgadmin3-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 4693kB of archives.
After unpacking 18.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com feisty/universe pgadmin3-data 1.4.3-2ubuntu1 [2545kB]
Get:2 http://us.archive.ubuntu.com feisty/universe pgadmin3 1.4.3-2ubuntu1 [2148kB]
Fetched 4693kB in 1m10s (66.9kB/s)                                             
Selecting previously deselected package pgadmin3-data.
(Reading database ... 160492 files and directories currently installed.)
Unpacking pgadmin3-data (from .../pgadmin3-data_1.4.3-2ubuntu1_all.deb) ...
Selecting previously deselected package pgadmin3.
Unpacking pgadmin3 (from .../pgadmin3_1.4.3-2ubuntu1_i386.deb) ...
Setting up postgresql-8.2 (8.2.4-1~edgy1) ...
 * Starting PostgreSQL 8.2 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2007-05-25 18:20:41 PDT LOG:  could not load root certificate file "root.crt": no SSL error reported
2007-05-25 18:20:41 PDT DETAIL:  Will not verify client certificates.
2007-05-25 18:20:41 PDT LOG:  could not translate host name "localhost", service "5432" to address: Name or service not known
2007-05-25 18:20:41 PDT WARNING:  could not create listen socket for "localhost"
2007-05-25 18:20:41 PDT FATAL:  could not create any TCP/IP sockets
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.2, action "start" failed.
dpkg: error processing postgresql-8.2 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of glom:
 glom depends on postgresql-8.2; however:
  Package postgresql-8.2 is not configured yet.
dpkg: error processing glom (--configure):
 dependency problems - leaving unconfigured
Setting up postgresql-8.1 (8.1.8-1ubuntu3) ...
 * Starting PostgreSQL 8.1 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2007-05-25 18:20:42 PDT LOG:  could not load root certificate file "root.crt": No SSL error reported
2007-05-25 18:20:42 PDT DETAIL:  Will not verify client certificates.
2007-05-25 18:20:42 PDT LOG:  could not translate host name "localhost", service "5433" to address: Name or service not known
2007-05-25 18:20:42 PDT WARNING:  could not create listen socket for "localhost"
2007-05-25 18:20:42 PDT FATAL:  could not create any TCP/IP sockets
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.1, action "start" failed.
dpkg: error processing postgresql-8.1 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql-contrib-8.2:
 postgresql-contrib-8.2 depends on postgresql-8.2; however:
  Package postgresql-8.2 is not configured yet.
dpkg: error processing postgresql-contrib-8.2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-plpython-8.2:
 postgresql-plpython-8.2 depends on postgresql-8.2; however:
  Package postgresql-8.2 is not configured yet.
dpkg: error processing postgresql-plpython-8.2 (--configure):
 dependency problems - leaving unconfigured
Setting up pgadmin3-data (1.4.3-2ubuntu1) ...
Setting up pgadmin3 (1.4.3-2ubuntu1) ...

Errors were encountered while processing:
 postgresql-8.2
 glom
 postgresql-8.1
 postgresql-contrib-8.2
 postgresql-plpython-8.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
i try to sudo dpkg -r --force-all postgreql-8.2
and reinstall it still no goal i can't update nothing nor install using sudo apt-get install

---

### Post by Happy_Man on 2007-05-27
```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get update
```

See if those help....

---

### Post by zerobinary on 2007-05-27
```
zerobinary@zerobinary:~$ sudo apt-get autoremove
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  artsbuilder python-kiwi libgtk-jni libpcrecpp0 libcairo-java
  libbluetooth2-dev libusb-dev librpcsecgss2 libjasper-runtime libgmp3c2
  libglib-java docker python-setuptools gazpacho mkvtoolnix libswt3.2-gtk-jni
  libimlib2 multisync
The following packages will be REMOVED:
  artsbuilder docker gazpacho libbluetooth2-dev libcairo-java libglib-java
  libgmp3c2 libgtk-jni libimlib2 libjasper-runtime libpcrecpp0 librpcsecgss2
  libswt3.2-gtk-jni libusb-dev mkvtoolnix multisync python-kiwi
  python-setuptools
0 upgraded, 0 newly installed, 18 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 37.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 161957 files and directories currently installed.)
Removing artsbuilder ...
Removing docker ...
Removing gazpacho ...
Removing libbluetooth2-dev ...
Removing libcairo-java ...
Removing libglib-java ...
Removing libgmp3c2 ...
Removing libgtk-jni ...
Removing libimlib2 ...
Removing libjasper-runtime ...
Removing mkvtoolnix ...
Removing libpcrecpp0 ...
Removing librpcsecgss2 ...
Removing libswt3.2-gtk-jni ...
Removing libusb-dev ...
Removing multisync ...
Removing python-kiwi ...
Removing python-setuptools ...
Setting up postgresql-8.2 (8.2.4-1~edgy1) ...
 * Starting PostgreSQL 8.2 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2007-05-27 19:11:47 PDT LOG:  could not load root certificate file "root.crt": no SSL error reported
2007-05-27 19:11:47 PDT DETAIL:  Will not verify client certificates.
2007-05-27 19:11:47 PDT LOG:  could not translate host name "localhost", service "5432" to address: Name or service not known
2007-05-27 19:11:47 PDT WARNING:  could not create listen socket for "localhost"
2007-05-27 19:11:47 PDT FATAL:  could not create any TCP/IP sockets
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.2, action "start" failed.
dpkg: error processing postgresql-8.2 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of glom:
 glom depends on postgresql-8.2; however:
  Package postgresql-8.2 is not configured yet.
dpkg: error processing glom (--configure):
 dependency problems - leaving unconfigured
Setting up postgresql-8.1 (8.1.8-1ubuntu3) ...
 * Starting PostgreSQL 8.1 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2007-05-27 19:11:48 PDT LOG:  could not load root certificate file "root.crt": No SSL error reported
2007-05-27 19:11:48 PDT DETAIL:  Will not verify client certificates.
2007-05-27 19:11:48 PDT LOG:  could not translate host name "localhost", service "5433" to address: Name or service not known
2007-05-27 19:11:48 PDT WARNING:  could not create listen socket for "localhost"
2007-05-27 19:11:48 PDT FATAL:  could not create any TCP/IP sockets
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.1, action "start" failed.
dpkg: error processing postgresql-8.1 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql-contrib-8.2:
 postgresql-contrib-8.2 depends on postgresql-8.2; however:
  Package postgresql-8.2 is not configured yet.
dpkg: error processing postgresql-contrib-8.2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-plpython-8.2:
 postgresql-plpython-8.2 depends on postgresql-8.2; however:
  Package postgresql-8.2 is not configured yet.
dpkg: error processing postgresql-plpython-8.2 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postgresql-8.2
 glom
 postgresql-8.1
 postgresql-contrib-8.2
 postgresql-plpython-8.2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
the first one not quite working

---

### Post by zerobinary on 2007-05-27
> zerobinary@zerobinary:~$ sudo apt-get clean
zerobinary@zerobinary:~$ sudo apt-get update
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy Release.gpg
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restricted Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restricted Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy Release    
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main Packages
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restricted Packages
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main Packages
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restricted Packages
Err cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg [191B]                  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_US                
Get:2 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty Release.gpg [191B]                        
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty/main Translation-en_US                      
Get:3 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]                    
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                  
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Get:5 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                 
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release                               
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg                         
Get:7 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg [359B]                
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-en_US              
Get:8 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release.gpg [191B]                  
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                  
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                 
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty Release                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US    
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US             
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Translation-en_US                
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US       
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                           
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US     
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                     
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US               
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Translation-en_US         
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty/main Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release                             
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release                             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Translation-en_US   
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release [44.7kB]              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                  
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty/main Packages                               
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release                               
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release                        
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Sources                        
Get:16 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release [2965B]                  
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages                    
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                   
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages                  
Err [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Sources                        
  404 Not Found [IP: 195.114.19.35 80]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages             
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages                       
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages             
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages [24.7kB]      
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release [44.7kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages [6269B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages [9473B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages [3321B]   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [24.7kB]       
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages [6269B]  
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources [4575B]         
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources [946B]    
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages [3321B]  
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages [9473B]    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                  
Fetched 186kB in 9s (19.7kB/s)                                                 
Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/dists/edgy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/dists/edgy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/dists/edgy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/dists/edgy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://ubuntu.beryl-project.org/apt/dists/feisty/main/source/Sources.gz](http://ubuntu.beryl-project.org/apt/dists/feisty/main/source/Sources.gz)  404 Not Found [IP: 195.114.19.35 80]
Reading package lists... Done
W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Duplicate sources.list entry [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

the second command not working too

---

### Post by Happy_Man on 2007-05-28
Ok.... for the first command:
> dpkg: error processing postgresql-8.1 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql-contrib-8.2:
 postgresql-contrib-8.2 depends on postgresql-8.2; however:
  Package postgresql-8.2 is not configured yet.
dpkg: error processing postgresql-contrib-8.2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-plpython-8.2:
 postgresql-plpython-8.2 depends on postgresql-8.2; however:
  Package postgresql-8.2 is not configured yet.
dpkg: error processing postgresql-plpython-8.2 (--configure):
 dependency problems - leaving unconfigured

It's basically complaining that the dependencies for the package aren't being installed before the package itself, so it throws a tantrum and exits. If you manually got your hands on these .debs, install postgresql-8.2 before the rest of them, see if that helps. If these are through Synaptic, I'm boggled. Those shouldn't be doing that then...... :confused:

The second one's not as bad. Just go into Synaptic options, look for the tab w/ custom repos, and get rid of the CD ones. The beryl server's down anyway, so try again tomorrow or something. Hope this helps!

---

### Post by zerobinary on 2007-05-29
i mean where cna u find the deb of postgre 8.4 lol
cna u give me a url for it

---

### Post by dashaun on 2007-05-29
> **Happy_Man said:**
> ```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get update
```

See if those help....

I'm stuck as well.  I'm up to this point.  Everything seems to be installed properly.  However, when I try to start postgres

```

>sudo /etc/init.d/postgres-8.2 start
 * Starting PostgreSQL 8.2 database server OK

```

It looks like it starts, but I get nothing.

Nothing in /var/log/postgres/

Nothing in /var/log/messages

Nothing running according to ps -ef

I'm stumped.

---

### Post by dashaun on 2007-05-29
I removed my /var/lib/postgresl at one point.

I figured it would get rebuilt.

It didn't.

Perhaps this is a good place to start.

How do I go about running "initdb"

When I try, it asks for PGDATA to be set in environment or for a destination directory.

I want to use ubuntu "default" values, what should I use?

---

### Post by zerobinary on 2007-05-30
maybe we should just delete the package but the problem is since the package already changed ur base code for ubuntu so removing will not help we should rebuild the package but the problem is that u can't use sudo apt-get install postgre 
so i don't know how to fix it someone help

---

