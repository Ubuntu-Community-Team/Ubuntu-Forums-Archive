---
title: "help in installin mercury messenger"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by black_ice on 2006-12-16
hello all ; 

i want to install mercury so i get it in .deb packages and i installed it 

[PHP] root@Ubuntu:/home/adam/Desktop# dpkg -i mercury-messenger_1710_S7_i386.deb 
(Reading database ... 96036 files and directories currently installed.)
Preparing to replace mercury-messenger 1710_S7 (using mercury-messenger_1710_S7_i386.deb) ...
Unpacking replacement mercury-messenger ...
Setting up mercury-messenger (1710_S7) ...
[/PHP]

and i make sure that i installed it with 
[PHP] root@Ubuntu:/home/adam/Desktop# which mercury
/usr/bin/mercury
[/PHP]

when i want to run it i got the following 

[PHP]root@Ubuntu:/home/adam/Desktop# /usr/bin/mercury 
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
[/PHP]

HELP PLZ :(

---

### Post by taurus on 2006-12-16
Looks like you are missing some libraries for the mercury!!!  

```
ldd /usr/bin/mercury
```
p.s.  Mercury is in the repos so any reason you don't want to use that version?

---

### Post by black_ice on 2006-12-16
i got thw follwing [PHP] root@Ubuntu:/home/adam/Desktop# ldd /usr/bin/mercury
        not a dynamic executable
[/PHP]

i need it cuz most of messengers doesnot fit me at all :S

---

### Post by taurus on 2006-12-16
```
file /usr/bin/mercury
```

---

### Post by black_ice on 2006-12-16
i got the following :S 
[PHP] root@Ubuntu:/home/adam/Desktop# file /usr/bin/mercury 
/usr/bin/mercury: symbolic link to `/usr/lib/mercury/Mercury[/PHP]

---

### Post by taurus on 2006-12-16
Then run

```
ldd /usr/lib/mercury/Mercury
```
Again, I assume you know that there is a version of mercury in the repos and you can install it with either synaptic/apt-get/aptitude!!!

---

### Post by black_ice on 2006-12-16
nothing happend also 

by the way thanx but how can install programe that not located at the add remove list or synaptic ?
i really need mercury :(

---

### Post by taurus on 2006-12-16
Applications -> Accessories -> Terminal
```
sudo dpkg -r mercury-messenger
sudo aptitude update
sudo aptitude install mercury
```
p.s.  Make sure you have both universe & multiverse enable in /etc/apt/sources.list...

---

### Post by black_ice on 2006-12-16
thanx thanx but how can install multiverse?? sorry for interrupt:)

---

### Post by taurus on 2006-12-16
In /etc/apt/sources.list, you need to remove the # sign in front of the lines with universe and multiverse at the end (the lines usually start with deb)...  

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
After you have made the changes and saved it. run

```
sudo aptitude update
sudo aptitude install mercury
```

---

### Post by black_ice on 2006-12-16
i remove hashs from the line with deb in the first and here is the file 

[PHP] root@Ubuntu:/usr/bin# cat /etc/apt/sources.list
# 
 deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://eg.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://eg.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://eg.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://eg.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://eg.archive.ubuntu.com/ubuntu/ edgy universe
 deb-src http://eg.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://eg.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
 deb-src http://eg.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
 deb http://security.ubuntu.com/ubuntu edgy-security universe
 deb-src http://security.ubuntu.com/ubuntu edgy-security universe
[/PHP]

---

### Post by taurus on 2006-12-16
And what happens when you run those two commands?

```
sudo aptitude update
sudo aptitude install mercury
```

---

### Post by black_ice on 2006-12-16
that is what happened 

[PHP] root@Ubuntu:~# sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restricted Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restricted Translation-en_US
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]               
Ign http://security.ubuntu.com edgy-security/main Translation-en_US             
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US        
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Hit http://security.ubuntu.com edgy-security Release
Get:2 http://eg.archive.ubuntu.com edgy Release.gpg [191B]                      
Ign http://eg.archive.ubuntu.com edgy/main Translation-en_US                    
Hit http://security.ubuntu.com edgy-security/main Packages                      
Ign http://eg.archive.ubuntu.com edgy/restricted Translation-en_US              
Ign http://eg.archive.ubuntu.com edgy/universe Translation-en_US                
Ign http://eg.archive.ubuntu.com edgy/multiverse Translation-en_US              
Ign http://eg.archive.ubuntu.com edgy/universe Translation-en_US                
Get:3 http://eg.archive.ubuntu.com edgy-updates Release.gpg [191B]              
Ign http://eg.archive.ubuntu.com edgy-updates/main Translation-en_US            
Hit http://security.ubuntu.com edgy-security/restricted Packages                
Hit http://security.ubuntu.com edgy-security/main Sources                       
Hit http://security.ubuntu.com edgy-security/restricted Sources                 
Ign http://eg.archive.ubuntu.com edgy-updates/restricted Translation-en_US      
Ign http://eg.archive.ubuntu.com edgy-updates/multiverse Translation-en_US      
Ign http://eg.archive.ubuntu.com edgy-updates/universe Translation-en_US        
Get:4 http://eg.archive.ubuntu.com edgy-backports Release.gpg [191B]            
Hit http://security.ubuntu.com edgy-security/universe Packages                  
Hit http://security.ubuntu.com edgy-security/universe Sources                   
Hit http://security.ubuntu.com edgy-security/multiverse Packages                
Hit http://security.ubuntu.com edgy-security/universe Packages                  
Ign http://eg.archive.ubuntu.com edgy-backports/main Translation-en_US          
Ign http://eg.archive.ubuntu.com edgy-backports/restricted Translation-en_US    
Ign http://eg.archive.ubuntu.com edgy-backports/universe Translation-en_US      
Ign http://eg.archive.ubuntu.com edgy-backports/multiverse Translation-en_US    
Hit http://eg.archive.ubuntu.com edgy Release                                   
Hit http://eg.archive.ubuntu.com edgy-updates Release                           
Hit http://eg.archive.ubuntu.com edgy-backports Release                         
Hit http://eg.archive.ubuntu.com edgy/main Packages                             
Hit http://eg.archive.ubuntu.com edgy/restricted Packages                       
Hit http://eg.archive.ubuntu.com edgy/main Sources                              
Hit http://eg.archive.ubuntu.com edgy/restricted Sources                        
Hit http://eg.archive.ubuntu.com edgy/universe Packages                         
Hit http://eg.archive.ubuntu.com edgy/universe Sources                          
Hit http://eg.archive.ubuntu.com edgy/multiverse Packages                       
Hit http://eg.archive.ubuntu.com edgy/universe Packages                         
Hit http://eg.archive.ubuntu.com edgy-updates/main Packages                     
Hit http://eg.archive.ubuntu.com edgy-updates/restricted Packages               
Hit http://eg.archive.ubuntu.com edgy-updates/main Sources                      
Hit http://eg.archive.ubuntu.com edgy-updates/restricted Sources                
Hit http://eg.archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://eg.archive.ubuntu.com edgy-updates/universe Packages
Hit http://eg.archive.ubuntu.com edgy-backports/main Packages
Hit http://eg.archive.ubuntu.com edgy-backports/restricted Packages
Hit http://eg.archive.ubuntu.com edgy-backports/universe Packages
Hit http://eg.archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://eg.archive.ubuntu.com edgy-backports/main Sources
Hit http://eg.archive.ubuntu.com edgy-backports/restricted Sources
Hit http://eg.archive.ubuntu.com edgy-backports/universe Sources
Hit http://eg.archive.ubuntu.com edgy-backports/multiverse Sources
Fetched 4B in 46s (0B/s) 
Reading package lists... Done
root@Ubuntu:~# sudo aptitude install mercury
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
root@Ubuntu:~# 

[/PHP]

---

### Post by taurus on 2006-12-16
What happens if you just type "**mercury**" from a terminal?  

By the way, you may want to put a # in front of the first two lines (for the CD-ROM) in /etc/apt/sources.list.  Now that you have internet connection, no need to use the CD-ROM anymore...

---

### Post by black_ice on 2006-12-16
that is what happened 

[PHP] root@Ubuntu:~# sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restricted Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restricted Translation-en_US
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]               
Ign http://security.ubuntu.com edgy-security/main Translation-en_US             
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US        
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Hit http://security.ubuntu.com edgy-security Release
Get:2 http://eg.archive.ubuntu.com edgy Release.gpg [191B]                      
Ign http://eg.archive.ubuntu.com edgy/main Translation-en_US                    
Hit http://security.ubuntu.com edgy-security/main Packages                      
Ign http://eg.archive.ubuntu.com edgy/restricted Translation-en_US              
Ign http://eg.archive.ubuntu.com edgy/universe Translation-en_US                
Ign http://eg.archive.ubuntu.com edgy/multiverse Translation-en_US              
Ign http://eg.archive.ubuntu.com edgy/universe Translation-en_US                
Get:3 http://eg.archive.ubuntu.com edgy-updates Release.gpg [191B]              
Ign http://eg.archive.ubuntu.com edgy-updates/main Translation-en_US            
Hit http://security.ubuntu.com edgy-security/restricted Packages                
Hit http://security.ubuntu.com edgy-security/main Sources                       
Hit http://security.ubuntu.com edgy-security/restricted Sources                 
Ign http://eg.archive.ubuntu.com edgy-updates/restricted Translation-en_US      
Ign http://eg.archive.ubuntu.com edgy-updates/multiverse Translation-en_US      
Ign http://eg.archive.ubuntu.com edgy-updates/universe Translation-en_US        
Get:4 http://eg.archive.ubuntu.com edgy-backports Release.gpg [191B]            
Hit http://security.ubuntu.com edgy-security/universe Packages                  
Hit http://security.ubuntu.com edgy-security/universe Sources                   
Hit http://security.ubuntu.com edgy-security/multiverse Packages                
Hit http://security.ubuntu.com edgy-security/universe Packages                  
Ign http://eg.archive.ubuntu.com edgy-backports/main Translation-en_US          
Ign http://eg.archive.ubuntu.com edgy-backports/restricted Translation-en_US    
Ign http://eg.archive.ubuntu.com edgy-backports/universe Translation-en_US      
Ign http://eg.archive.ubuntu.com edgy-backports/multiverse Translation-en_US    
Hit http://eg.archive.ubuntu.com edgy Release                                   
Hit http://eg.archive.ubuntu.com edgy-updates Release                           
Hit http://eg.archive.ubuntu.com edgy-backports Release                         
Hit http://eg.archive.ubuntu.com edgy/main Packages                             
Hit http://eg.archive.ubuntu.com edgy/restricted Packages                       
Hit http://eg.archive.ubuntu.com edgy/main Sources                              
Hit http://eg.archive.ubuntu.com edgy/restricted Sources                        
Hit http://eg.archive.ubuntu.com edgy/universe Packages                         
Hit http://eg.archive.ubuntu.com edgy/universe Sources                          
Hit http://eg.archive.ubuntu.com edgy/multiverse Packages                       
Hit http://eg.archive.ubuntu.com edgy/universe Packages                         
Hit http://eg.archive.ubuntu.com edgy-updates/main Packages                     
Hit http://eg.archive.ubuntu.com edgy-updates/restricted Packages               
Hit http://eg.archive.ubuntu.com edgy-updates/main Sources                      
Hit http://eg.archive.ubuntu.com edgy-updates/restricted Sources                
Hit http://eg.archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://eg.archive.ubuntu.com edgy-updates/universe Packages
Hit http://eg.archive.ubuntu.com edgy-backports/main Packages
Hit http://eg.archive.ubuntu.com edgy-backports/restricted Packages
Hit http://eg.archive.ubuntu.com edgy-backports/universe Packages
Hit http://eg.archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://eg.archive.ubuntu.com edgy-backports/main Sources
Hit http://eg.archive.ubuntu.com edgy-backports/restricted Sources
Hit http://eg.archive.ubuntu.com edgy-backports/universe Sources
Hit http://eg.archive.ubuntu.com edgy-backports/multiverse Sources
Fetched 4B in 46s (0B/s) 
Reading package lists... Done
root@Ubuntu:~# sudo aptitude install mercury
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
root@Ubuntu:~# 

[/PHP]

---

### Post by taurus on 2006-12-16
Just start the program to see if it's on your machine or not!!!

```
mercury
```

---

### Post by lamego on 2006-12-16
The mercury package on the repositories is not the mercury messenger as you are expecting:
```
(dapper.i386)lamego@lamego-desktop:~/debs/b/bjs-0.0.5$ apt-cache show mercury
Package: mercury
Priority: optional
Section: universe/devel
Installed-Size: 109984
Maintainer: Peter Hawkins <peterh@debian.org>
Architecture: i386
Version: 0.11.0.rotd.20040511-5
Depends: libc6 (>= 2.3.2.ds1-4), make
Conflicts: mmake
Filename: pool/universe/m/mercury/mercury_0.11.0.rotd.20040511-5_i386.deb
Size: 25301708
MD5sum: 0181ec9f503e2d44dd3ea53cec557fe7
Description: A new logic/functional programming language

```

---

### Post by black_ice on 2006-12-16
command not found

---

### Post by taurus on 2006-12-16
Fire up synaptic (System -> Administrator) and in the Search field, type **mercury** to see if it can find it...

---

### Post by Seti on 2006-12-18
AFAIK there is no .deb package for Mercury on ubuntu.
You could always try finding the RPM and converting it with alien, worth giving a try.

---

### Post by Voxxi on 2006-12-18
I did a Google, and found a [(Non-english) site]("http://translate.google.com/translate?hl=en&sl=pt&u=http://projeto-messias.sourceforge.net/mercury/&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Dsite:http://projeto-messias.sourceforge.net/mercury/%26hl%3Den%26lr%3D%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3D1iX") that seems to have a .deb for it.

From what Google auto-translate tells me, its a stable ( 1.8 ) Mercury release.

---

### Post by Seti on 2006-12-18
Thanks for the link, make sure you have jvm running and this package *should* work.
Gonna try it when I get home later.

Cheers, 

J

---

### Post by erizo on 2006-12-28
Hi, I installed mercury from the .deb package and the installation was successful.
I got the message: "installation complete, all the dependencies OK".
but when I double click the icon nothing happens.....
any clue?

---

