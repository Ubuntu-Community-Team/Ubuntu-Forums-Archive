---
title: "[SOLVED] 2 errors messages"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by jryprt on 2007-10-18
Hi : I am getting this error 
E: msttcorefonts: subprocess post-installation script returned error exit status 1
E: ubuntu-restricted-extras: dependency problems - leaving unconfigured
after startup & getting new updates . How do I fix this.
Thanks Jerry

---

### Post by jryprt on 2007-10-18
Hi : I am getting this error
E: msttcorefonts: subprocess post-installation script returned error exit status 1
E: ubuntu-restricted-extras: dependency problems - leaving unconfigured
after startup & getting new updates . How do I fix this.
Thanks Jerry

---

### Post by bapoumba on 2007-10-18
Please post your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by Technoviking on 2007-10-18
Try this
```
sudo apt-get install -f
```

---

### Post by overdrank on 2007-10-18
> **jryprt said:**
> Hi : I am getting this error
E: msttcorefonts: subprocess post-installation script returned error exit status 1
E: ubuntu-restricted-extras: dependency problems - leaving unconfigured
after startup & getting new updates . How do I fix this.
Thanks Jerry

HI and please don't make multiple threads on the same subject. Which version of ubuntu are you using  Feisty, gutsy? DO you get those errors during update or are you installing something?

---

### Post by bapoumba on 2007-10-18
Threads (slowly) merged, thanks overdrank!

---

### Post by jryprt on 2007-10-18
jerry@ip68-13-167-47:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main
jerry@ip68-13-167-47:~$ 
jerry@ip68-13-167-47:~$

---

### Post by jryprt on 2007-10-18
> **overdrank said:**
> HI and please don't make multiple threads on the same subject. Which version of ubuntu are you using  Feisty, gutsy? DO you get those errors during update or are you installing something?
 
ook at my Signature it sayes 7.04 with is feisty & the update is for compiz-core

---

### Post by bapoumba on 2007-10-18
Please try Mike's suggestion. Your sources.list is fine.

---

### Post by jryprt on 2007-10-18
> **Mike said:**
> Try this
```
sudo apt-get install -f
```

I get this 

jerry@ip68-13-167-47:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up msttcorefonts (1.8ubuntu1) ...
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--14:51:05--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198,384 (194K) [application/octet-stream]

100%[====================================>] 198,384      173.41K/s             

14:51:06 (172.96 KB/s) - `./andale32.exe' saved [198384/198384]

--14:51:06--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe)
           => `./arialb32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168,176 (164K) [application/octet-stream]

100%[====================================>] 168,176      146.40K/s             

14:51:08 (146.13 KB/s) - `./arialb32.exe' saved [168176/168176]

--14:51:08--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)
           => `./arial32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554,208 (541K) [application/octet-stream]

100%[====================================>] 554,208      266.76K/s             

14:51:10 (266.08 KB/s) - `./arial32.exe' saved [554208/554208]

--14:51:10--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe)
           => `./comic32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246,008 (240K) [application/octet-stream]

100%[====================================>] 246,008      188.10K/s             

14:51:12 (187.53 KB/s) - `./comic32.exe' saved [246008/246008]

--14:51:12--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
           => `./courie32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646,368 (631K) [application/octet-stream]

100%[====================================>] 646,368      278.53K/s             

14:51:15 (277.70 KB/s) - `./courie32.exe' saved [646368/646368]

--14:51:15--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
           => `./georgi32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392,440 (383K) [application/octet-stream]

100%[====================================>] 392,440      236.04K/s             

14:51:17 (235.41 KB/s) - `./georgi32.exe' saved [392440/392440]

--14:51:17--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
           => `./impact32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173,288 (169K) [application/octet-stream]

100%[====================================>] 173,288      154.65K/s             

14:51:18 (154.00 KB/s) - `./impact32.exe' saved [173288/173288]

--14:51:18--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
           => `./times32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661,728 (646K) [application/octet-stream]

100%[====================================>] 661,728      286.11K/s             

14:51:21 (285.21 KB/s) - `./times32.exe' saved [661728/661728]

--14:51:21--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
           => `./trebuc32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357,200 (349K) [application/octet-stream]

100%[====================================>] 357,200      239.10K/s             

14:51:22 (238.45 KB/s) - `./trebuc32.exe' saved [357200/357200]

--14:51:22--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
           => `./verdan32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351,992 (344K) [application/octet-stream]

100%[====================================>] 351,992      235.18K/s             

14:51:24 (234.38 KB/s) - `./verdan32.exe' saved [351992/351992]

--14:51:24--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
           => `./webdin32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185,072 (181K) [application/octet-stream]

100%[====================================>] 185,072      162.64K/s             

14:51:26 (162.13 KB/s) - `./webdin32.exe' saved [185072/185072]

Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
mkdir: `/usr/share/fonts/truetype/msttcorefonts' exists but is not a directory
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-restricted-extras:
 ubuntu-restricted-extras depends on msttcorefonts; however:
  Package msttcorefonts is not configured yet.
dpkg: error processing ubuntu-restricted-extras (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 msttcorefonts
 ubuntu-restricted-extras
E: Sub-process /usr/bin/dpkg returned an error code (1)
jerry@ip68-13-167-47:~$

---

### Post by jryprt on 2007-10-18
I still get this 
E: msttcorefonts: subprocess post-installation script returned error exit status 1
E: ubuntu-restricted-extras: dependency problems - leaving unconfigured

---

### Post by bapoumba on 2007-10-18
Please try:
```
dkpg-reconfigure fontconfig
```
And paste the output.

---

### Post by jryprt on 2007-10-18
> **bapoumba said:**
> Please try:
```
dkpg-reconfigure fontconfig
```
And paste the output.

I got this

jerry@ip68-13-167-47:~$ dkpg-reconfigure fontconfig
bash: dkpg-reconfigure: command not found
jerry@ip68-13-167-47:~$ 


Thanks Jerry

---

### Post by bapoumba on 2007-10-18
My bad sorry.. (its a little hectic tonight), there are _two_ typos..
```
sudo dpkg-reconfigure fontconfig
```
Apologies.

---

### Post by jryprt on 2007-10-18
> **bapoumba said:**
> My bad sorry.. (its a little hectic tonight), there are _two_ typos..
```
sudo dpkg-reconfigure fontconfig
```
Apologies.

No Apologies need - you are helping me 
I got this 

jerry@ip68-13-167-47:~$ sudo dpkg-reconfigure fontconfig
Password:
Cleaning up font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating category type1..
Updating category truetype..
Updating category cid..
Regenerating fonts cache... done.
jerry@ip68-13-167-47:~$

---

### Post by bapoumba on 2007-10-18
And do you have an error to 
```
sudo aptitude update
```

---

### Post by jryprt on 2007-10-18
> **bapoumba said:**
> And do you have an error to 
```
sudo aptitude update
```

I got this & after I tried the update & still got the 2 errors

jerry@ip68-13-167-47:~$ sudo aptitude update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Translation-en_US                      
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty Release                                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages                   
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Fetched 384B in 4m0s (2B/s)
Reading package lists... Done
jerry@ip68-13-167-47:~$

---

### Post by bapoumba on 2007-10-18
No error, looks good to me :)

---

### Post by jryprt on 2007-10-18
Here is 3 screenshot

---

### Post by bapoumba on 2007-10-18
What is that compiz from a ppa you are using? Current feisty compiz-core package is 1:0.3.6.

---

### Post by jryprt on 2007-10-18
> **bapoumba said:**
> What is that compiz from a ppa you are using? Current feisty compiz-core package is 1:0.3.6.
Where & how do I find this info.

---

### Post by bapoumba on 2007-10-18
> **jryprt said:**
> Where & how do I find this info.
Hmm, it's in your firts screenshot. The compiz-core package is at a version higher than the feisty one..
How did you install compiz ?

---

### Post by overdrank on 2007-10-18
> **jryprt said:**
> Here is 3 screenshot

HI and I do not mean to  intrude bapoumba but I have seen these errors several times. If you will go to synaptic and search and remove everything that has to do with compiz and then use this thread to install  Mr Greencastle part of compiz-fiusion
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)
Just the part with compiz-fusion and the reops. It has worked for me.

---

### Post by jryprt on 2007-10-18
There is a orange box on the top panel  with a + on it it says ( there is 1 update available)
the frist screenshot show up after I click on the + box

---

### Post by jryprt on 2007-10-18
> **bapoumba said:**
> Hmm, it's in your firts screenshot. The compiz-core package is at a version higher than the feisty one..
How did you install compiz ?
I used this guide  [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

---

### Post by bapoumba on 2007-10-18
@ overdrank, that's fine, you can take it from here, I'm not much compiz and compiz-what-not savvy ;)

---

### Post by jryprt on 2007-10-18
> **overdrank said:**
> HI and I do not mean to  intrude bapoumba but I have seen these errors several times. If you will go to synaptic and search and remove everything that has to do with compiz and then use this thread to install  Mr Greencastle part of compiz-fiusion
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)
Just the part with compiz-fusion and the reops. It has worked for me.

I will try this & get back

---

### Post by jryprt on 2007-10-18
> **jryprt said:**
> I will try this & get back
I tryed to remove compiz and got the same errors 
screenshot

---

### Post by overdrank on 2007-10-18
> **jryprt said:**
> I tryed to remove compiz and got the same errors 
screenshot

Ok try and us these command
```
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade
```
and please post the output of each. :KS

---

### Post by jryprt on 2007-10-18
> **overdrank said:**
> Ok try and us these command
```
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade
```
and please post the output of each. :KS

jerry@ip68-13-167-47:~$ sudo apt-get autoclean
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
jerry@ip68-13-167-47:~$ 
jerry@ip68-13-167-47:~$ sudo apt-get update
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]       
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources                   
Fetched 194B in 20s (10B/s)                                                    
Reading package lists... Done
jerry@ip68-13-167-47:~$ 
jerry@ip68-13-167-47:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  compiz-core
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/188kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  compiz-core
Install these packages without verification [y/N]? y
(Reading database ... 159793 files and directories currently installed.)
Preparing to replace compiz-core 1:0.5.2+git20070918-0ubuntu5~ppa1 (using .../compiz-core_1%3a0.5.2+git20070918-0ubuntu5~ppa1_i386.deb) ...
Unpacking replacement compiz-core ...
Setting up msttcorefonts (1.8ubuntu1) ...
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--17:35:40--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198,384 (194K) [application/octet-stream]

100%[====================================>] 198,384      170.19K/s             

17:35:42 (169.59 KB/s) - `./andale32.exe' saved [198384/198384]

--17:35:42--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe)
           => `./arialb32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168,176 (164K) [application/octet-stream]

100%[====================================>] 168,176      166.51K/s             

17:35:43 (166.04 KB/s) - `./arialb32.exe' saved [168176/168176]

--17:35:43--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)
           => `./arial32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554,208 (541K) [application/octet-stream]

100%[====================================>] 554,208      261.03K/s             

17:35:46 (260.26 KB/s) - `./arial32.exe' saved [554208/554208]

--17:35:46--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe)
           => `./comic32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246,008 (240K) [application/octet-stream]

100%[====================================>] 246,008      211.44K/s             

17:35:47 (210.80 KB/s) - `./comic32.exe' saved [246008/246008]

--17:35:47--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
           => `./courie32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646,368 (631K) [application/octet-stream]

100%[====================================>] 646,368      281.37K/s             

17:35:50 (280.33 KB/s) - `./courie32.exe' saved [646368/646368]

--17:35:50--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
           => `./georgi32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392,440 (383K) [application/octet-stream]

100%[====================================>] 392,440      237.21K/s             

17:35:52 (236.59 KB/s) - `./georgi32.exe' saved [392440/392440]

--17:35:52--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
           => `./impact32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173,288 (169K) [application/octet-stream]

100%[====================================>] 173,288      154.78K/s             

17:35:53 (154.31 KB/s) - `./impact32.exe' saved [173288/173288]

--17:35:53--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
           => `./times32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661,728 (646K) [application/octet-stream]

100%[====================================>] 661,728      286.61K/s             

17:35:56 (285.71 KB/s) - `./times32.exe' saved [661728/661728]

--17:35:56--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
           => `./trebuc32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357,200 (349K) [application/octet-stream]

100%[====================================>] 357,200      236.04K/s             

17:35:58 (235.40 KB/s) - `./trebuc32.exe' saved [357200/357200]

--17:35:58--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
           => `./verdan32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351,992 (344K) [application/octet-stream]

100%[====================================>] 351,992      235.25K/s             

17:36:00 (234.44 KB/s) - `./verdan32.exe' saved [351992/351992]

--17:36:00--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
           => `./webdin32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185,072 (181K) [application/octet-stream]

100%[====================================>] 185,072      159.73K/s             

17:36:01 (159.13 KB/s) - `./webdin32.exe' saved [185072/185072]

Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
mkdir: `/usr/share/fonts/truetype/msttcorefonts' exists but is not a directory
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-restricted-extras:
 ubuntu-restricted-extras depends on msttcorefonts; however:
  Package msttcorefonts is not configured yet.
dpkg: error processing ubuntu-restricted-extras (--configure):
 dependency problems - leaving unconfigured
Setting up compiz-core (0.5.2+git20070918-0ubuntu5~ppa1) ...
Errors were encountered while processing:
 msttcorefonts
 ubuntu-restricted-extras
E: Sub-process /usr/bin/dpkg returned an error code (1)
jerry@ip68-13-167-47:~$

---

### Post by overdrank on 2007-10-18
Ok please don't take this in a arrogant tone. But how did you install this msttcorefonts? DId you compile it? Because your apt source list did not contain it. Ok there is something else we can try to get rid of it if you are up to it.  Use the command ```
sudo aptitude
``` It will bring up a menu that will allow you several options to clean you system. Hope this helps!

---

### Post by jryprt on 2007-10-19
> **overdrank said:**
> Ok please don't take this in a arrogant tone. But how did you install this msttcorefonts? DId you compile it? Because your apt source list did not contain it. Ok there is something else we can try to get rid of it if you are up to it.  Use the command ```
sudo aptitude
``` It will bring up a menu that will allow you several options to clean you system. Hope this helps!

Ok I got this screen now what?

---

### Post by bapoumba on 2007-10-19
ncurses interface to aptitude is fine (I use aptitude only) but to find where a package comes from, you can use:
```
isabella@yeti:~ $ apt-cache madison msttcorefonts
msttcorefonts |        2.2 | http://archive.ubuntu.com gutsy/multiverse Packages
msttcorefonts |        2.2 | http://archive.ubuntu.com gutsy/multiverse Sources
```
Easier ;)

---

### Post by jryprt on 2007-10-19
> **bapoumba said:**
> ncurses interface to aptitude is fine (I use aptitude only) but to find where a package comes from, you can use:
```
isabella@yeti:~ $ apt-cache madison msttcorefonts
msttcorefonts |        2.2 | http://archive.ubuntu.com gutsy/multiverse Packages
msttcorefonts |        2.2 | http://archive.ubuntu.com gutsy/multiverse Sources
```
Easier ;)

Here is what I got 

jerry@ip68-13-167-47:~$ isabella@yeti:~ $ apt-cache madison msttcorefonts
bash: isabella@yeti:~: command not found
jerry@ip68-13-167-47:~$ apt-cache madison msttcorefonts
msttcorefonts | 1.8ubuntu1 | [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
msttcorefonts | 1.8ubuntu1 | [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
jerry@ip68-13-167-47:~$

---

### Post by bapoumba on 2007-10-19
Arf.. We're going in circles here.

You could try to completely remove msttcorefonts, either from synaptic if you are used to it (with the purge option) and then reinstall, or from the CLI:
```
sudo apt-get purge msttcorefonts
sudo apt-get install msttcorefonts
```

---

### Post by jryprt on 2007-10-19
> **bapoumba said:**
> Arf.. We're going in circles here.

You could try to completely remove msttcorefonts, either from synaptic if you are used to it (with the purge option) and then reinstall, or from the CLI:
```
sudo apt-get purge msttcorefonts
sudo apt-get install msttcorefonts
```
I used synaptic to remove msttcorefonts then tryed the update that is still in the orange box w/ the + is said it was done but the orange box w/ the + is still said 1 update is there .
than I did this
jerry@ip68-13-167-47:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
msttcorefonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up msttcorefonts (1.8ubuntu1) ...
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--07:51:26--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198,384 (194K) [application/octet-stream]

100%[====================================>] 198,384      177.39K/s             

07:51:27 (176.96 KB/s) - `./andale32.exe' saved [198384/198384]

--07:51:27--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe)
           => `./arialb32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168,176 (164K) [application/octet-stream]

100%[====================================>] 168,176      170.44K/s             

07:51:29 (169.95 KB/s) - `./arialb32.exe' saved [168176/168176]

--07:51:29--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)
           => `./arial32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554,208 (541K) [application/octet-stream]

100%[====================================>] 554,208      259.81K/s             

07:51:31 (259.03 KB/s) - `./arial32.exe' saved [554208/554208]

--07:51:31--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe)
           => `./comic32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246,008 (240K) [application/octet-stream]

100%[====================================>] 246,008      188.62K/s             

07:51:33 (188.09 KB/s) - `./comic32.exe' saved [246008/246008]

--07:51:33--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
           => `./courie32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646,368 (631K) [application/octet-stream]

100%[====================================>] 646,368      276.36K/s             

07:51:35 (275.42 KB/s) - `./courie32.exe' saved [646368/646368]

--07:51:35--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
           => `./georgi32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392,440 (383K) [application/octet-stream]

100%[====================================>] 392,440      242.05K/s             

07:51:37 (241.26 KB/s) - `./georgi32.exe' saved [392440/392440]

--07:51:37--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
           => `./impact32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173,288 (169K) [application/octet-stream]

100%[====================================>] 173,288      175.93K/s             

07:51:39 (175.53 KB/s) - `./impact32.exe' saved [173288/173288]

--07:51:39--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
           => `./times32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661,728 (646K) [application/octet-stream]

100%[====================================>] 661,728      292.01K/s             

07:51:41 (291.39 KB/s) - `./times32.exe' saved [661728/661728]

--07:51:41--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
           => `./trebuc32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357,200 (349K) [application/octet-stream]

100%[====================================>] 357,200      243.69K/s             

07:51:43 (243.04 KB/s) - `./trebuc32.exe' saved [357200/357200]

--07:51:43--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
           => `./verdan32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351,992 (344K) [application/octet-stream]

100%[====================================>] 351,992      220.04K/s             

07:51:45 (219.42 KB/s) - `./verdan32.exe' saved [351992/351992]

--07:51:45--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
           => `./webdin32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185,072 (181K) [application/octet-stream]

100%[====================================>] 185,072      162.38K/s             

07:51:46 (161.92 KB/s) - `./webdin32.exe' saved [185072/185072]

Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
mkdir: `/usr/share/fonts/truetype/msttcorefonts' exists but is not a directory
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
jerry@ip68-13-167-47:~$ 

Than I tryed the update again got this (5.png ) screenshot the output is 
jerry@ip68-13-167-47:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
msttcorefonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up msttcorefonts (1.8ubuntu1) ...
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--07:51:26--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198,384 (194K) [application/octet-stream]

100%[====================================>] 198,384      177.39K/s             

07:51:27 (176.96 KB/s) - `./andale32.exe' saved [198384/198384]

--07:51:27--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe)
           => `./arialb32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168,176 (164K) [application/octet-stream]

100%[====================================>] 168,176      170.44K/s             

07:51:29 (169.95 KB/s) - `./arialb32.exe' saved [168176/168176]

--07:51:29--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)
           => `./arial32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554,208 (541K) [application/octet-stream]

100%[====================================>] 554,208      259.81K/s             

07:51:31 (259.03 KB/s) - `./arial32.exe' saved [554208/554208]

--07:51:31--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe)
           => `./comic32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246,008 (240K) [application/octet-stream]

100%[====================================>] 246,008      188.62K/s             

07:51:33 (188.09 KB/s) - `./comic32.exe' saved [246008/246008]

--07:51:33--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
           => `./courie32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646,368 (631K) [application/octet-stream]

100%[====================================>] 646,368      276.36K/s             

07:51:35 (275.42 KB/s) - `./courie32.exe' saved [646368/646368]

--07:51:35--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
           => `./georgi32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392,440 (383K) [application/octet-stream]

100%[====================================>] 392,440      242.05K/s             

07:51:37 (241.26 KB/s) - `./georgi32.exe' saved [392440/392440]

--07:51:37--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
           => `./impact32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173,288 (169K) [application/octet-stream]

100%[====================================>] 173,288      175.93K/s             

07:51:39 (175.53 KB/s) - `./impact32.exe' saved [173288/173288]

--07:51:39--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
           => `./times32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661,728 (646K) [application/octet-stream]

100%[====================================>] 661,728      292.01K/s             

07:51:41 (291.39 KB/s) - `./times32.exe' saved [661728/661728]

--07:51:41--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
           => `./trebuc32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357,200 (349K) [application/octet-stream]

100%[====================================>] 357,200      243.69K/s             

07:51:43 (243.04 KB/s) - `./trebuc32.exe' saved [357200/357200]

--07:51:43--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
           => `./verdan32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351,992 (344K) [application/octet-stream]

100%[====================================>] 351,992      220.04K/s             

07:51:45 (219.42 KB/s) - `./verdan32.exe' saved [351992/351992]

--07:51:45--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
           => `./webdin32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185,072 (181K) [application/octet-stream]

100%[====================================>] 185,072      162.38K/s             

07:51:46 (161.92 KB/s) - `./webdin32.exe' saved [185072/185072]

Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
mkdir: `/usr/share/fonts/truetype/msttcorefonts' exists but is not a directory
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
jerry@ip68-13-167-47:~$ 

the update manager still show 1 upadte (1.png) screenshot

---

### Post by bapoumba on 2007-10-19
This is from your log, look at the lines in red:
```
jerry@ip68-13-167-47:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree
Reading state information... Done
[COLOR="Red"]msttcorefonts is already the newest version.[/COLOR]
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
```
This means msttcorefonts had not been removed.
Please try to remove it from the CLI:
```
sudo apt-get purge msttcorefonts

```

---

### Post by jryprt on 2007-10-19
> **bapoumba said:**
> This is from your log, look at the lines in red:
```
jerry@ip68-13-167-47:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree
Reading state information... Done
[COLOR="Red"]msttcorefonts is already the newest version.[/COLOR]
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
```
This means msttcorefonts had not been removed.
Please try to remove it from the CLI:
```
sudo apt-get purge msttcorefonts

```

I got this 

jerry@ip68-13-167-47:~$ sudo apt-get purge msttcorefonts
Password:
E: Invalid operation purge
jerry@ip68-13-167-47:~$

---

### Post by bapoumba on 2007-10-19
> **jryprt said:**
> I got this 

jerry@ip68-13-167-47:~$ sudo apt-get purge msttcorefonts
Password:
E: Invalid operation purge
jerry@ip68-13-167-47:~$

Hmm, look at what you should be getting:

```
isabella@yeti:~ $ sudo apt-get purge msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  msttcorefonts*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 193kB disk space will be freed.
Do you want to continue [Y/n]? 

```

Please try with aptitude:
```
sudo aptitude purge msttcorefonts
```

```
isabella@yeti:~ $ sudo aptitude purge msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  msttcorefonts{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 193kB will be freed.
Do you want to continue? [Y/n/?] 
```
If it wants to remove a buch of other things hit No and paste them in here.

And please post the output to :
```
aptitude show msttcorefonts
```

---

### Post by jryprt on 2007-10-19
> **bapoumba said:**
> Hmm, look at what you should be getting:

```
isabella@yeti:~ $ sudo apt-get purge msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  msttcorefonts*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 193kB disk space will be freed.
Do you want to continue [Y/n]? 

```

Please try with aptitude:
```
sudo aptitude purge msttcorefonts
```

```
isabella@yeti:~ $ sudo aptitude purge msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  msttcorefonts{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 193kB will be freed.
Do you want to continue? [Y/n/?] 
```
If it wants to remove a buch of other things hit No and paste them in here.

And please post the output to :
```
aptitude show msttcorefonts
```


Did this

jerry@ip68-13-167-47:~$ sudo aptitude purge msttcorefonts
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  compiz-core 
The following packages will be REMOVED:
  msttcorefonts{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 213kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 159789 files and directories currently installed.)
Removing msttcorefonts ...
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Headline-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Gulim-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
Purging configuration files for msttcorefonts ...
jerry@ip68-13-167-47:~$ 

Than this

jerry@ip68-13-167-47:~$ aptitude show msttcorefonts
Package: msttcorefonts
State: not installed
Version: 1.8ubuntu1
Priority: optional
Section: multiverse/x11
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 213k
Depends: wget (>= 1.9.1-4), cabextract, xfonts-utils, debconf (>= 1.2.0) |
         debconf-2.0, defoma
Recommends: x-ttcidfont-conf
Description: Installer for Microsoft TrueType core fonts
 This package allows for easy installation of the Microsoft True Type Core Fonts
 for the Web including: 
 
  Andale Mono
  Arial Black
  Arial (Bold, Italic, Bold Italic)
  Comic Sans MS (Bold)
  Courier New (Bold, Italic, Bold Italic)
  Georgia (Bold, Italic, Bold Italic)
  Impact
  Times New Roman (Bold, Italic, Bold Italic)
  Trebuchet (Bold, Italic, Bold Italic)
  Verdana (Bold, Italic, Bold Italic)
  Webdings
 
 You will need an Internet connection to download these fonts if you don't
 already have them.

jerry@ip68-13-167-47:~$

---

### Post by bapoumba on 2007-10-19
Okay, so msttcorefonts is out of your way. You'll reinstall this package when the compiz issue is gone. 
Do you still have an issue with compiz, BTW ?

---

### Post by jryprt on 2007-10-19
> **bapoumba said:**
> Okay, so msttcorefonts is out of your way. You'll reinstall this package when the compiz issue is gone. 
Do you still have an issue with compiz, BTW ?

Yes I try to update after update says it done the update mamager (onange box with +)
is still there with 1 update still there same one.Look a screenshot 
0 B have to be downloaded
look at next post for screenshots

---

### Post by jryprt on 2007-10-19
> **jryprt said:**
> Yes I try to update after update says it done the update mamager (onange box with +)
is still there with 1 update still there same one.Look a screenshot 
0 B have to be downloaded
here is screenshot

---

### Post by jryprt on 2007-10-19
Ok I did sudo aptitude purge msttcorefonts it removed  msttcorefonts then removed all thing that are compiz in synaptic , all so emerald now the update manager (orange box with + ib top panel is gone.

Thank you bapoumba

---

### Post by bapoumba on 2007-10-19
You're welcome :)
So do you need any of these packages you have removed? Now that the package managers are happy, you could see to reinstall them.

---

### Post by jryprt on 2007-10-19
> **bapoumba said:**
> You're welcome :)
So do you need any of these packages you have removed? Now that the package managers are happy, you could see to reinstall them.
No everythings OK I do not know how msttcorefonts was installed or for what but do not need it 
Thanks Jerry

---

### Post by bapoumba on 2007-10-19
> **jryprt said:**
> No everythings OK I do not know how msttcorefonts was installed or for what but do not need it 
Thanks Jerry
msttcorefonts is an installer for some Microsoft fonts. It may have been installed as a dependency for some other package.

---

