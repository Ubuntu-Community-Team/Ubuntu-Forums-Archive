---
title: "Apt-Get and Add/Remove problems"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by erik087 on 2007-10-19
Hi, everyone.

I'm hoping you guys can help me out with some problems I'm having after a fresh Gutsy install.  BTW, I'm familiar with Unix (which I use at work), but don't really have any Linux experience.

Anyway, the install went fine and I was able to download and configure my nvidia drivers in Synaptic Package Manager.  I also installed the Compiz configuration manager without any problems.

However, there are lots of other things that I'm unable to install.  For instance, Using Package Manager or sudo apt-get to install KDE gives me problems:

erik@erik-desktop:~$ sudo apt-get install kde-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kde-core is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kde-core has no installation candidate

Or this:

erik@erik-desktop:~$ sudo apt-get install kde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde: Depends: kde-core (>= 5:47) but it is not installable
       Depends: kde-amusements (>= 5:47) but it is not going to be installed
       Depends: kdeaccessibility (>= 4:3.4.3) but it is not installable
       Depends: kdeaddons (>= 4:3.4.3) but it is not installable
       Depends: kdeadmin (>= 4:3.4.3) but it is not going to be installed
       Depends: kdeartwork (>= 4:3.4.3) but it is not installable
       Depends: kdegraphics (>= 4:3.4.3) but it is not going to be installed
       Depends: kdemultimedia (>= 4:3.4.3) but it is not going to be installed
       Depends: kdenetwork (>= 4:3.4.3) but it is not going to be installed
       Depends: kdepim (>= 4:3.4.3) but it is not going to be installed
       Depends: kdeutils (>= 4:3.4.3) but it is not going to be installed
       Depends: kdewebdev (>= 4:3.4.3) but it is not installable
E: Broken packages

Also, if I try to install Thuderbird from Add/Remove I get this:

Mozilla Thunderbird Mail/News cannot be installed on your computer type (i386).  Either the application requires special hardware features or the vendor decided to not support your computer type.

The "cannot be installed on your computer type" error shows up for A LOT of the software in the Add/Remove menu.

I've run sudo apt-get update (necessary?) and this is the output:

erik@erik-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources              
Fetched 3B in 10s (0B/s)                                                       
Reading package lists... Done

Here are some system specs:
Intel Core 2 Duo E6600
2GB DDR2 RAM
Nvidia 8800 GTS (640MB)
Clean Gutsy install from CD

I'm sure there are some stupid things that I just haven't grasped yet, but I'd really appreciate someone pointing me in the right direction.

Thanks!

-Erik

---

### Post by erik087 on 2007-10-19
update:

I found that "canonical" was not checked in software sources.  I've checked that and it looks like the kde install is now proceeding.


Any ideas about the problems installing Thunderbird?

Thanks.

---

### Post by mndzmyst on 2007-10-19
Not sure if it's the same issue, but when install gutsy I had to choose the main server. For some reason the servers here did not work. Maybe you could try that.

---

### Post by darklemming54 on 2007-10-19
I had the same problem.  See [URL="http://ubuntuforums.org/showthread.php?t=580979&highlight=computer+special+hardware"]this thread.
[/URL]

---

### Post by mlentink on 2007-10-19
> For instance, Using Package Manager or sudo apt-get to install KDE gives me problems
Any reason why you didn't:
```
sudo apt-get install kubuntu-desktop
```?

---

### Post by saj0577 on 2007-10-19
Its due to the new version 7.10 i have not found a way to override it as i have installed 7.10 now so you may want to upgrade to 7.10 if you do not wish to do so Im sorry cant help you.

Saj

---

### Post by erik087 on 2007-10-19
> **darklemming54 said:**
> I had the same problem.  See [URL="http://ubuntuforums.org/showthread.php?t=580979&highlight=computer+special+hardware"]this thread.
[/URL]

You saved my life. :)  It was the third-party software tab that I had missed.

Thanks everyone for the help!

---

