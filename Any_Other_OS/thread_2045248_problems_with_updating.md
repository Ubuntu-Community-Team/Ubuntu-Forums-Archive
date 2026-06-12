---
title: "problems with updating"
date: 2012-08-20
forum: Any Other OS
---

### Post by jlsalavea on 2012-08-20
complete beginner here, hubby installed linux mint (helena i believe) on his asus eee pc and then decided he didnt have time to learn how to use it...so i get to do it. yay. anyway, i had problems installing google chrome, which led me to find out that i have problems with everything on here...but i will start with updates. i cannot update, i keep getting errors. 
this is what i just got when i tried to check for updates. 

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.189 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.189 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.184 80]
Some index files failed to download, they have been ignored, or old ones used instead.

any help would be greatly appreciated, though this seems like it will be one of those huge endeavors for anyone who decides to help. thanks again!

---

### Post by Bashing-om on 2012-08-20
jlsalavea; 
  Hi ! welcome to the forum. /We are all here to help/
This can't be too serious of a problem... sooooo..
see if this command (from the command line) fixes your source list.
```
sudo apt-get update
```if not, advise us of the errors you get ....and 
post these results
```
lsb_release -a
```to see what release you are running
and
```
cat /etc/apt/sources.list > sources.list.txt
```to see what you source list is. The latter command will output the text file sources.list.txt in the your current working directory////cut and paste it between code tags (# at top of post screen)....
[INDENT]we await your reply <==BDQ
[/INDENT]

---

### Post by Perfect Storm on 2012-08-20
Moved to Other OS/Distro Talk.

---

### Post by Bucky Ball on 2012-08-21
Welcome.

Open Software Sources or update manager. If the latter, click the settings button in bottom left corner. In the list of repositories or 'Other Software' tab you will see the offending repos. Untick them. Karmic is old and are probably redundant for you.

That should fix the problem. Then, try these two commands in a terminal (Applications>Accessories>Terminal):

```
sudo apt-get update
sudo apt-get upgrade
```The second command will upgrade apps and dependencies, NOT the release. Good luck. ;)

---

### Post by jlsalavea on 2012-08-21
thanks for the replies!

bashing, i typed in what you said, and got this. wasnt sure what was relevant, and what was not, so i copied it all. (this is just for the first command)

thanks for the replies guys!

bashing, i typed in what you said and this is what popped up. not sure what was relevant, and what you didnt need, so i just copied all of it.
Get:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) helena Release.gpg [198B]
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/main Translation-en_US
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/upstream Translation-en_US
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/import Translation-en_US
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/backport Translation-en_US            
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/romeo Translation-en_US               
Get:2 [http://packages.linuxmint.com](http://packages.linuxmint.com) helena Release [12.1kB]                    
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/main Packages                         
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_US      
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/upstream Packages                     
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/import Packages                       
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/backport Packages                     
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/romeo Packages                        
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/main Sources                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                   
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/upstream Sources                      
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/import Sources                        
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/backport Sources                      
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/romeo Sources                         
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/main Packages                         
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/upstream Packages                     
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/import Packages                       
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/backport Packages                     
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/romeo Packages                        
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/main Sources                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/upstream Sources                      
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages             
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/import Sources                        
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/backport Sources                      
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/romeo Sources                         
Get:3 [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/main Packages [4,771B]              
Get:4 [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/upstream Packages [7,545B]          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages                       
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Get:5 [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/import Packages [5,771B]            
Get:6 [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/backport Packages [20B]             
Get:7 [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/romeo Packages [1,332B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US                
Get:8 [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/main Sources [4,520B]               
Get:9 [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/upstream Sources [3,007B]           
Get:10 [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/import Sources [994B]              
Get:11 [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/backport Sources [20B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages               
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Get:12 [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/romeo Sources [888B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages             
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
  404  Not Found [IP: 91.189.92.190 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
  404  Not Found [IP: 91.189.92.190 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages                         
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages               
  404  Not Found [IP: 91.189.92.190 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages             
  404  Not Found [IP: 91.189.92.190 80]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages                 
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages               
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                             
  404  Not Found [IP: 91.189.92.188 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages                       
  404  Not Found [IP: 91.189.92.188 80]
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                     
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages             
  404  Not Found [IP: 91.189.92.188 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages           
  404  Not Found [IP: 91.189.92.188 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages         
  404  Not Found [IP: 91.189.92.188 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages   
  404  Not Found [IP: 91.189.92.188 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages     
  404  Not Found [IP: 91.189.92.188 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages
  404  Not Found [IP: 91.189.92.188 80]
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages
Fetched 41.2kB in 2s (16.4kB/s)
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.188 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.188 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.188 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.188 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.188 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.188 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.188 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.188 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

second command, got this:
No LSB modules are available.
Distributor ID:    LinuxMint
Description:    Linux Mint 8 Helena - Main Edition
Release:    8
Codename:    helena

i entered the third command and then saw that you had said it would output a text file in my current working directory...i have no idea how to get to that. :P 

Bucky, i looked in my update manager and i could not find a settings option anywhere, so i didnt do anything; i didnt want to start unticking boxes and make the problem worse. :D

---

### Post by Bucky Ball on 2012-08-21
Update Manager>Settings button is in the bottom left hand corner of that GUI, or should be. Do you have a 'Software Sources' entry under System>Administration, if that still exists (I use Xubuntu)? 

If so, just untick the offending repo. You can do it in a terminal by:

```
sudo nano /etc/apt/sources.list
```Could be an idea to make a copy before playing with this:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```To move it back if you screw up:

```
sudo cp /etc/apt/sources.list.bak /etc/apt/sources.list
```Then hash out the repo or remove it, for instance:

```
# deb [http://giss.tv/~vale/ubuntu32/hardy]("http://giss.tv/%7Evale/ubuntu32/hardy") ./
```

Rather than:

```
deb [http://giss.tv/~vale/ubuntu32/hardy]("http://giss.tv/%7Evale/ubuntu32/hardy") ./
```

---

### Post by jlsalavea on 2012-08-21
i dont know what the offending repo is, or how to find out. total noob here.

---

### Post by Bucky Ball on 2012-08-21
```
W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...86/Packages.gz]("http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz")  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...86/Packages.gz]("http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz")  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...86/Packages.gz]("http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz")  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...86/Packages.gz]("http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz")  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz")  404  Not Found [IP: 91.189.92.188 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz")  404  Not Found [IP: 91.189.92.188 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz")  404  Not Found [IP: 91.189.92.188 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz")  404  Not Found [IP: 91.189.92.188 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz")  404  Not Found [IP: 91.189.92.188 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz")  404  Not Found [IP: 91.189.92.188 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz")  404  Not Found [IP: 91.189.92.188 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz")  404  Not Found [IP: 91.189.92.188 80]
```

After the http:// there is the address of the repo. The one being reported will be clearly identifiable in your sources.list. Add a '#' then a space before the ones you want to disable.

---

### Post by jlsalavea on 2012-08-23
alright, after googling how to work nano, i hashed out the repo's, and was able to update. but when i try sudo apt-get upgrade, i get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

i also tried to install some things with the software manager, and under the list of installed apps were the things i was trying to download...but the only option i have is to install it again, i choose that, no errors pop up, but i canno find the programs. then i try sudo apt-get install (program name) and i get the error 

E: could not find package (program name)

thanks for all the help so far, I was really close to just giving this damn thing away, but you guys have changed my mind. :D

---

### Post by Bucky Ball on 2012-08-23
No probs. Please provide the names of some of the apps you're attempting to install. If you are going for gimp, for example, try these:

```
locate gimp
whereis gimp
find gimp
```The upgrade message is normal; you don't have any packages or dependencies to upgrade. *Always* do 'sudo apt-get update' prior to issuing the upgrade command. 

So you're saying the programs you are managing to install through Software Centre are installing but not appearing in your Applications menu? You can also try issuing just the name of something you know is installed (if you are asked to reinstall, it's installed already, don't bother reinstalling):

```
audacity
```... if you happen to have just installed audacity. Running stuff from the terminal will also give you some idea of what's happened if the program crashes as you'll see the error thrown there (or some clues about it). ;)

---

