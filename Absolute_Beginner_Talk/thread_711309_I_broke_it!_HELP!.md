---
title: "I broke it! HELP!"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by 3wells on 2008-02-29
Will no longer update
Synaptic manager reports  >>>

         E: The package hl1230lpr needs to be reinstalled, but I can't find an archive for it.
         E: Internal error opening cache (1). Please report.

Tried - sudo apt-get autoclean

synaptic progy doesn't work, so, cant remove orphaned stuff...


I tried recovery mode - no joy...

This happened because I tried to get my printer going on my own - tried many differt thing - arriving here!

I've tried a few progys, they still work.

How do I get rid of the partially installed printer stuff?

Is there another recovery procedure? What can I do? I on't especially want to start over.

Can I reinstall from cd and retain the upgrades that I've managed to get to work?

3

---

### Post by taurus on 2008-02-29
```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by 3wells on 2008-02-29
Did the sudos.. same result, no updater, no synaptic manager?

How can I hack the hl1230pr junk out? I tried in 'root', couldn't. All aces denied...

3

Quote:

ross@ross-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package hl1230lpr needs to be reinstalled, but I can't find an archive for it.
ross@ross-desktop:~$ sudo dpkg --configure -a
Setting up kubuntu-docs (7.10-5) ...
Using `/usr/share/ubuntu-artwork/home/kfirefox-index.html' to provide `firefox-homepage'.
ln: `/usr/share/ubuntu-artwork/home/images': cannot overwrite directory
dpkg: error processing kubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of brother-lpr-drivers-extra:
 brother-lpr-drivers-extra depends on brother-lpr-drivers-common; however:
  Package brother-lpr-drivers-common is not installed.
dpkg: error processing brother-lpr-drivers-extra (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kubuntu-docs
 brother-lpr-drivers-extra
ross@ross-desktop:~$ sudo apt-get update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Translation-en_CA                   
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) gusty Release.gpg                           
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) gusty/all Translation-en_CA       
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]          
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_CA               
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_CA                     
Get:4 [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release [6738B]              
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) gusty Release                               
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_CA           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_CA             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_CA           
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg [191B]          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_CA        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_CA  
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) gusty/all Packages                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_CA        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_CA
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_CA   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_CA       
Err [http://repoubuntusoftware.info](http://repoubuntusoftware.info) gusty/all Packages                          
  302 Found
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_CA
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Translation-en_CA
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Sources
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release [44.0kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Fetched 50.9kB in 2s (24.8kB/s)
Failed to fetch [http://repoubuntusoftware.info/dists/gusty/all/binary-i386/Packages.gz](http://repoubuntusoftware.info/dists/gusty/all/binary-i386/Packages.gz) 302 Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
ross@ross-desktop:~$

---

### Post by 3wells on 2008-02-29
Really FUBAR here - still ned help! Back on pg 1!

---

### Post by 3wells on 2008-02-29
I've been at this for 2 hours - nothing works....About to put back windoze! Anyone -PLEASE!

hl1230lpr will NOT go away!

sudo apt-get remove hl1230lpr >> nope

sudo dpkg --force-remove-reinstreq -P hl1230lpr >> nope


b

---

### Post by timbounceback on 2008-02-29
Perhaps it is because "http://repoubuntusoftware.info/dists...86/Packages.gz" is down? By the way, I wouldn't recommend using Automatix, do some googling and you'll see why.

---

### Post by Tanno on 2008-03-01
Well, I'm afraid that I'm in the same boat.

```
tanno@Tanno-Linux:~$ sudo apt-get install -f
[sudo] password for tanno:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
tanno@Tanno-Linux:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1
tanno@Tanno-Linux:~$
```

---

### Post by 3wells on 2008-03-01
Log in as 'root'

sudo dpkg --force-remove-reinstreq -P hl1230lpr >>> done! Synaptic & Updates work again!

Still get an error > E: kubuntu-docs: subprocess post-installation script returned error exit status 1

The Fix for this >

In synaptic, select kubuntu-docs, mark for complete removal, apply, reinstall.

Now - cleanup....

sudo apt-get autoclean
localepurge
deborphan > sudo deborphan | xargs sudo apt-get -y remove --purge

I'm just learning (it's my day off)! It's only been a week or so, playing with Linux, I think I've made some progress!

Damn it, the printer still does not work!

3

---

### Post by 3wells on 2008-03-06
Fixed - sort of -  I got printer up & runnig!

A bit complicated & maybe 'causse I'm not sure what I'm doing...

As follows >>>

" All I had to do is the following on my computer that is not directly hooked up to the printer / but rather through the LAN:
System>>Administration>>Printing -- Basic Server Settings I have "Show printers by other systems" ticked, "Share published printers connected to this system" ticked, "Allow remote administration" ticked then I clicked "Apply". Then I clicked on the "New Printer" icon and clicked on Windows Printer via Samba you gotta add the Saba through add/remove) and clicked on the "Browse" button to locate my printer on my "MSHOME" network. It showed up just fine and works " 

Well it didn't!

Then >>>

I installed the Unix cups pkg (Brother hl1230lpr), which allows me to address my routers IP > 192.168.2.1, gave it a name > LPT1, that (I think) was it...

If I had to retrace my steps - well, I don't think I could!

Minor bug, after a successful print, the printer gives me two additional blank pages? I can't seem to fix this? Anyway, from no printing to two addition blanks, better!

If someone knows a simple fix (complicated is okay too) send it along!

3

---

