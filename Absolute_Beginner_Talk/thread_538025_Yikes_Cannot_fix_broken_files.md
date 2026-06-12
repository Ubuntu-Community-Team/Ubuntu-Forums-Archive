---
title: "Yikes Cannot fix broken files"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by sdgreen on 2007-08-29
SYSTEM:

Running Ubuntu ver 7.04 on a IBM 6792 with a 2.4ghz processor, 1.2gigs ram, nvidia 6600GT videa, two 80gig 7200rpm drives.


PROBLEM:

How to remove broken files.


SITUATION:

I was installing new printer files from the Brother Linux printer support for a MFC 5460CN Printer. All seemed to go well until reboot and sign on when system came up with the update symbol. On clicking, the update system indicated broken files. On attempt to remove via synaptic, system indicated errors in that it could not find offending files and displayed E: brscan2: subprocess post-removal script returned error exit status 1
E: mfc5460cncupswrapper: subprocess pre-removal script returned error exit status 127 from Synaptic

The two broken files that I cannot seem to remove  are: 
brscan2, mfc5460cncupswrapper

ATTEMPTED REPAIR FAILS USING (output below)

apt-get install -f
update-desktop-database
aptitude clean

What is curious is that the files cannot be found, and indeed looking at the file system neither the indicated file directories or files can be found on ht system.

root@sdgreen-desktop:/home/sdgreen# sudo update-desktop-database
root@sdgreen-desktop:/home/sdgreen# sudo aptitude clean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
root@sdgreen-desktop:/home/sdgreen# sudo aptitude update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_CA
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release.gpg [191B]                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Translation-en_CA                  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Translation-en_CA            
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                  
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_CA           
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]             
Get:5 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_CA               
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release.gpg [191B]            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Translation-en_CA          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Translation-en_CA    
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports Release.gpg [191B]          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/main Translation-en_CA        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/restricted Translation-en_CA  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe Translation-en_CA    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_CA           
Get:8 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_CA       
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/multiverse Translation-en_CA  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_CA     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_CA       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_CA     
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_CA         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_CA       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_CA     
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Translation-en_CA       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                      
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_CA            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_CA      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_CA        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Packages                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Packages                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Sources                            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Sources                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_CA      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release                          
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_CA                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_CA               
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_CA      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_CA            
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Packages                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Packages             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Sources                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Sources              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/main Packages                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/restricted Packages           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe Packages             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/multiverse Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_CA      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages                
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Fetched 13B in 1s (8B/s) 
Reading package lists... Done
root@sdgreen-desktop:/home/sdgreen# apt-get install desktop-file-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
desktop-file-utils is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mfc5460cncupswrapper: Depends: mfc5460cnlpr but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@sdgreen-desktop:/home/sdgreen# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libwavpack0 libntfs8 libtunepimp3
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  brscan2 mfc5460cncupswrapper
0 upgraded, 0 newly installed, 2 to remove and 5 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 155813 files and directories currently installed.)
Removing brscan2 ...
rmdir: /usr/local/Brother/sane/GrayCmData/ALL: No such file or directory
rmdir: /usr/local/Brother/sane/GrayCmData/AL: No such file or directory
rmdir: /usr/local/Brother/sane/GrayCmData: No such file or directory
rmdir: /usr/local/Brother/sane: No such file or directory
dpkg: error processing brscan2 (--remove):
 subprocess post-removal script returned error exit status 1
Removing mfc5460cncupswrapper ...
/var/lib/dpkg/info/mfc5460cncupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc5460cn/cupswrapper/cupswrappermfc5460cn: not found
dpkg: error processing mfc5460cncupswrapper (--remove):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc5460cncupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc5460cn/cupswrapper/cupswrappermfc5460cn: not found
cp: cannot stat `/usr/share/cups/model/brmfc5460cn.ppd': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 brscan2
 mfc5460cncupswrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@sdgreen-desktop:/home/sdgreen# 

Help.

---

### Post by sdgreen on 2007-08-29
Help anyone...

---

### Post by sdgreen on 2007-08-29
any help?

---

### Post by sdgreen on 2007-08-29
+++ Bump ++++ 

Help please...

---

### Post by enderwig on 2007-08-29
have you tried the broken packages filter in synaptic?

---

### Post by sdgreen on 2007-08-29
yes does not work. comes back with error codes 1 and 127

---

### Post by enderwig on 2007-08-29
what is the output of 
```
cd /
sudo find -name *mfc5460cncupswrapper*
```

---

### Post by sdgreen on 2007-08-29
hmmm ... not certain what the following is

sdgreen@sdgreen-desktop:~$ cd /
sdgreen@sdgreen-desktop:/$ sudo find -name *mfc5460cncupswrapper*
Password:
./var/lib/dpkg/info/mfc5460cncupswrapper.preinst
./var/lib/dpkg/info/mfc5460cncupswrapper.list
./var/lib/dpkg/info/mfc5460cncupswrapper.postinst
./var/lib/dpkg/info/mfc5460cncupswrapper.prerm
./var/lib/dpkg/info/mfc5460cncupswrapper.postrm
./var/lib/dpkg/info/mfc5460cncupswrapper.conffiles
sdgreen@sdgreen-desktop:/$

---

### Post by enderwig on 2007-08-29
try this
```
dpkg --purge mfc5460cncupswrapper
```
if not then
```
dpkg --pending mfc5460cncupswrapper
```

---

### Post by sdgreen on 2007-08-29
First command produced:

sdgreen@sdgreen-desktop:/$ sudo dpkg --purge mfc5460cncupswrapper
Password:
(Reading database ... 155813 files and directories currently installed.)
Removing mfc5460cncupswrapper ...
/var/lib/dpkg/info/mfc5460cncupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc5460cn/cupswrapper/cupswrappermfc5460cn: not found
dpkg: error processing mfc5460cncupswrapper (--purge):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc5460cncupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc5460cn/cupswrapper/cupswrappermfc5460cn: not found
cp: cannot stat `/usr/share/cups/model/brmfc5460cn.ppd': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mfc5460cncupswrapper

Second Command produced:

sdgreen@sdgreen-desktop:/$ sudo dpkg --pending mfc5460cncupswrapper
dpkg: need an action option

---

### Post by enderwig on 2007-08-29
Sorry I can't help more, but I am afraid we have reached the extent of my  knowledge.  I hope another (more helpful :) ) person will reply.

---

### Post by sdgreen on 2007-08-29
I wonder what would happen if I just deleted the /var reference files?

Thanks for your help.

---

### Post by enderwig on 2007-08-29
I didn't want to recommend deleting files i was unsure of.  Maybe make copies elsewhere first then try deleting them, then sudo apt-get update

---

### Post by sdgreen on 2007-08-29
Ok, maybe I will give that a try. I too am not certain what happens. There seems to be some sort of database that records all of this. 
Seems to me tha if the system cannot find the files, then it should gracefully allow you to reset synaptic etc., so you can reinstall.

Thanks again. Hopefully another can help.

---

