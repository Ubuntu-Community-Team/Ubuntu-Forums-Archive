---
title: "[SOLVED] Firefox will not update?????"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by UMD TERPS FAN on 2008-02-10
I have Ubuntu 7.10 64 bit running on a AMD 64 bit chip.  The current version of Firefox i have is 2.0.06 an older version, the new version is 2.0.12.  However Firefox wont let me update to the newest version; when I go to check for updates it will not allow you click on it.  I can download the latest version from the Firefox website, but I have no clue how to install it.  Any help would be great!

Thanks,

Grant

---

### Post by Moop on 2008-02-10
You can update firefox by starting it in terminal  
[HTML]gksudo firefox[/HTML]

or check the repos for a newer version.

---

### Post by Majorix on 2008-02-10
I am not very positive (haven't been on a Gutsy box for a while) but I believe there should be a newer release in Gutsy repos. Try this:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by UMD TERPS FAN on 2008-02-10
> **Moop said:**
> You can update firefox by starting it in terminal  
[HTML]gksudo firefox[/HTML]

or check the repos for a newer version.

when i type that in the terminal it just opens firefox not updating it.....

-Grant

---

### Post by arkara on 2008-02-10
if you want to install firefox from the site
then you can download a deb package and do the job
to install the package you can just doulbe click it and click on the install button
ubuntu will install if automatically

---

### Post by UMD TERPS FAN on 2008-02-10
> **Majorix said:**
> I am not very positive (haven't been on a Gutsy box for a while) but I believe there should be a newer release in Gutsy repos. Try this:
```
sudo apt-get update && sudo apt-get upgrade
```

That didn't work either this is what it spit out:confused:

> grant@grant-laptop:~$ sudo apt-get update && sudo apt-get upgrade
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Fetched 2B in 0s (3B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I downloaded the newest version to my desktop, I just need to know how to install it.

Thanks,

-Grant

---

### Post by Majorix on 2008-02-10
The output of the command I told you seemed a little too short to me. Are you sure you haven't disabled some important repos? See here, this is the real output from that command:
```
sudo apt-get update 
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Get:1 http://tr.archive.ubuntu.com hardy Release.gpg [191B]                    
Ign http://tr.archive.ubuntu.com hardy/main Translation-en_US                  
Hit http://archive.canonical.com hardy Release                                 
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Ign http://tr.archive.ubuntu.com hardy/restricted Translation-en_US            
Ign http://tr.archive.ubuntu.com hardy/universe Translation-en_US              
Ign http://tr.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://tr.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://tr.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://tr.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://tr.archive.ubuntu.com hardy-updates/universe Translation-en_US      
Hit http://security.ubuntu.com hardy-security Release                          
Ign http://tr.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://tr.archive.ubuntu.com hardy-backports Release.gpg    
Ign http://tr.archive.ubuntu.com hardy-backports/main Translation-en_US
Ign http://tr.archive.ubuntu.com hardy-backports/restricted Translation-en_US
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://security.ubuntu.com hardy-security/main Packages                    
Ign http://tr.archive.ubuntu.com hardy-backports/universe Translation-en_US    
Ign http://tr.archive.ubuntu.com hardy-backports/multiverse Translation-en_US  
Hit http://tr.archive.ubuntu.com hardy-proposed Release.gpg                    
Ign http://tr.archive.ubuntu.com hardy-proposed/restricted Translation-en_US   
Ign http://tr.archive.ubuntu.com hardy-proposed/main Translation-en_US         
Ign http://tr.archive.ubuntu.com hardy-proposed/multiverse Translation-en_US   
Ign http://tr.archive.ubuntu.com hardy-proposed/universe Translation-en_US     
Hit http://archive.canonical.com hardy/partner Sources                         
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Get:2 http://tr.archive.ubuntu.com hardy Release [65.9kB]                      
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Hit http://tr.archive.ubuntu.com hardy-updates Release                         
Hit http://tr.archive.ubuntu.com hardy-backports Release              
Hit http://tr.archive.ubuntu.com hardy-proposed Release               
Get:3 http://tr.archive.ubuntu.com hardy/main Packages [1124kB]                
Get:4 http://tr.archive.ubuntu.com hardy/restricted Packages [6647B]           
Get:5 http://tr.archive.ubuntu.com hardy/main Sources [313kB]                  
Hit http://packages.medibuntu.org gutsy Release.gpg                            
Ign http://packages.medibuntu.org gutsy/free Translation-en_US                 
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_US             
Hit http://packages.medibuntu.org gutsy Release                                
Ign http://packages.medibuntu.org gutsy/free Packages                          
Ign http://packages.medibuntu.org gutsy/non-free Packages                      
Hit http://packages.medibuntu.org gutsy/free Packages                          
Hit http://packages.medibuntu.org gutsy/non-free Packages                      
Get:6 http://tr.archive.ubuntu.com hardy/restricted Sources [1599B]            
Get:7 http://tr.archive.ubuntu.com hardy/universe Packages [4303kB]            
Get:8 http://tr.archive.ubuntu.com hardy/universe Sources [1329kB]             
Get:9 http://tr.archive.ubuntu.com hardy/multiverse Packages [168kB]           
Get:10 http://tr.archive.ubuntu.com hardy/multiverse Sources [59.0kB]          
Hit http://tr.archive.ubuntu.com hardy-updates/main Packages                   
Hit http://tr.archive.ubuntu.com hardy-updates/restricted Packages             
Hit http://tr.archive.ubuntu.com hardy-updates/main Sources                    
Hit http://tr.archive.ubuntu.com hardy-updates/restricted Sources              
Hit http://tr.archive.ubuntu.com hardy-updates/universe Packages               
Hit http://tr.archive.ubuntu.com hardy-updates/universe Sources                
Hit http://tr.archive.ubuntu.com hardy-updates/multiverse Packages             
Hit http://tr.archive.ubuntu.com hardy-updates/multiverse Sources              
Hit http://tr.archive.ubuntu.com hardy-backports/main Packages                 
Hit http://tr.archive.ubuntu.com hardy-backports/restricted Packages           
Hit http://tr.archive.ubuntu.com hardy-backports/universe Packages             
Hit http://tr.archive.ubuntu.com hardy-backports/multiverse Packages           
Hit http://tr.archive.ubuntu.com hardy-proposed/restricted Packages            
Hit http://tr.archive.ubuntu.com hardy-proposed/main Packages                  
Hit http://tr.archive.ubuntu.com hardy-proposed/multiverse Packages            
Hit http://tr.archive.ubuntu.com hardy-proposed/universe Packages              
Fetched 7371kB in 26s (277kB/s)                                                
Reading package lists... Done
```

I would post the output of "cat /etc/apt/sources.list" here for people to check.

---

### Post by UMD TERPS FAN on 2008-02-10
> **arkara said:**
> if you want to install firefox from the site
then you can download a deb package and do the job
to install the package you can just doulbe click it and click on the install button
ubuntu will install if automatically

I downloaded the firefox-2.0.0.12.tar.gz to my desktop, when I double click it there is no install button.  There a extract button, but I have no clue where to extract it to..:confused: I'm a noob i know :(
 
Thanks

Grant

---

### Post by steveneddy on 2008-02-10
The version in Ubuntu is stable and will run fine. It will get updated when it is determined that the new version that is packaged for Ubuntu is stable.

---

### Post by UMD TERPS FAN on 2008-02-10
> **steveneddy said:**
> The version in Ubuntu is stable and will run fine. It will get updated when it is determined that the new version that is packaged for Ubuntu is stable.

so version 2.0.0.6 is the only version Ubuntu supports, not the new version 2.0.0.12?

-Grant

---

### Post by Majorix on 2008-02-10
It currently supports upto 2.0.0.10.

---

### Post by Moop on 2008-02-10
The command I gave you opens firefox in sudo mode. You should be able to manually update firefox.   Help-Check for updates.

---

### Post by UMD TERPS FAN on 2008-02-10
> **Moop said:**
> The command I gave you opens firefox in sudo mode. You should be able to manually update firefox.   Help-Check for updates.

I did that, but "check for updates" is still italicized (meaning it wont let me click on it....man this is weird:confused:

-Grant

---

### Post by SunnyRabbiera on 2008-02-10
> **UMD TERPS FAN said:**
> so version 2.0.0.6 is the only version Ubuntu supports, not the new version 2.0.0.12?

-Grant

you can go as far as firefox version 2.0.0.10 as thats as high it is in the repositories.
You may be able to get the more current version though if you update your repositories...
The easiest way to do this is use synaptic, and or apt.

---

### Post by Majorix on 2008-02-10
> **SunnyRabbiera said:**
> you can go as far as firefox version 2.0.0.10 as thats as high it is in the repositories.
You may be able to get the more current version though if you update your repositories...
The easiest way to do this is use synaptic, and or apt.

There is no "more current version" for Ubuntu (officially) as I am on Hardy with 2.0.0.10.

I still believe the OP should fix their sources.list as I suggested.

---

### Post by UMD TERPS FAN on 2008-02-10
> **SunnyRabbiera said:**
> you can go as far as firefox version 2.0.0.10 as thats as high it is in the repositories.
You may be able to get the more current version though if you update your repositories...
The easiest way to do this is use synaptic, and or apt.

I looked in the synaptic package manager, and could not find the newest version.  Man this is whacked....

-Grant

---

### Post by Majorix on 2008-02-10
Are you ignoring me?

You WON'T find firefox in your Synaptic because you DON'T have the repos for it enabled.

---

### Post by Kilz on 2008-02-10
In the first post in this section the orignal poster stated they were running the 64bit version. I am running 64bit Feisty and the Firefox version is 2.0.0.12. Check out the screenshot. But I think Majorix is right there is a apt repository problem, the apt update list is way to small.

---

### Post by UMD TERPS FAN on 2008-02-10
> **Majorix said:**
> Are you ignoring me?

You WON'T find firefox in your Synaptic because you DON'T have the repos for it enabled.

Ok I checked every box in the repo and this is what I got:
> 
grant@grant-laptop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for grant:
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg [191B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Sources
Fetched 766B in 1s (575B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


However I found the 2.0.0.12 in the package manager and installed it.  When I go to help>about mozilla, its says i have 2.0.0.12.  So I guess it installed.  Thanks for the help!

Grant

---

### Post by rainwalker on 2008-02-10
Firefox comes with Ubuntu, and it's only updated when the Ubuntu developers determine that it is stable enough to be updated. I'm currenlty running 2.0.0.12, so you should have an update for it soon.

---

### Post by randy78 on 2008-02-10
Am I the only one who uses the UbuntuZilla package!?

It's completely automated once you install it...

[http://sourceforge.net/project/showfiles.php?group_id=202789&package_id=241580]("http://sourceforge.net/project/showfiles.php?group_id=202789&package_id=241580")

Just download the Deb file for your processor type, double click it and install it...

Then, in a terminal, just run:
ubuntuzilla.py -p firefox

And it will update!

You can also use this to install the newest version of Thunderbird too ;)

Hope this helps :guitar:

---

### Post by steveneddy on 2008-02-10
That's weird. My Synaptic still says 2.0.0.11.

I guess it'll hit in a few days.

---

### Post by Kilz on 2008-02-11
> **randy78 said:**
> Am I the only one who uses the UbuntuZilla package!?

It's completely automated once you install it...

[http://sourceforge.net/project/showfiles.php?group_id=202789&package_id=241580]("http://sourceforge.net/project/showfiles.php?group_id=202789&package_id=241580")

Just download the Deb file for your processor type, double click it and install it...

Then, in a terminal, just run:
ubuntuzilla.py -p firefox

And it will update!

You can also use this to install the newest version of Thunderbird too ;)

Hope this helps :guitar:

UbuntuZilla is a nice script. But 64bit users , like the original poster in this thread, may want to use a 64bit browser. UbuntuZilla only installs a 32bit browser, because it downloads the browser from Mozilla, and Mozilla only makes 32bit versions.

---

