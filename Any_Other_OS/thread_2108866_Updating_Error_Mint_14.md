---
title: "Updating Error Mint 14"
date: 2013-01-25
forum: Any Other OS
---

### Post by Scozzar on 2013-01-25
Okay, so I have two issues.  I am running **Linux Mint 14 KDE 64bit.**  The printer I am trying to use is a **Canon PIXMA Mp 280**.  I have looked at the various threads on Ubuntu Forums for this exact same printer, but I'm not sure what to do.  I've looked at the [this](http://ubuntuforums.org/showthread.php?t=1582497) thread and downloaded the 3.40.1 drivers.  But I don't know what to do with them.  When I opend them up, it's just a bunch of tar.gz folders and the install.sh.  I tried running the .sh using sudo bash _____ there was an error.  I can provide screenshots of what I'm looking at if you want.

Okay, next problem.


Whenever I update using "sudo apt-get update" the terminal does the usual, but then towards the bottom I get tons of "cannot access (internet address) 404" or something along those lines.  WATCH OUT!  I'm posting what I am talking about..

```
Err http://archive.canonical.com nadia/partner amd64 Packages                                                                                                                                   
  404  Not Found [IP: 91.189.92.191 80]                                                                                                                                                         
Err http://archive.canonical.com nadia/partner i386 Packages                                                                                                                                    
  404  Not Found [IP: 91.189.92.191 80]                                                                                                                                                         
Ign http://archive.canonical.com nadia/partner Translation-en_US      
Ign http://archive.canonical.com nadia/partner Translation-en                                          
Err http://security.ubuntu.com nadia-security/main amd64 Packages                                                                                                                              
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com nadia-security/restricted amd64 Packages                                                                                                                        
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com nadia-security/universe amd64 Packages                                                                                                                          
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com nadia-security/multiverse amd64 Packages                                                                                                                        
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com nadia-security/main i386 Packages                                                                                                                               
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com nadia-security/restricted i386 Packages                                                                                                                         
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com nadia-security/universe i386 Packages                                                                                                                           
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com nadia-security/multiverse i386 Packages                                                                                                                         
  404  Not Found [IP: 91.189.91.13 80]
Ign http://security.ubuntu.com nadia-security/main Translation-en_US                                                                                                                           
Ign http://security.ubuntu.com nadia-security/main Translation-en                                                                                                                              
Ign http://security.ubuntu.com nadia-security/multiverse Translation-en_US                                                                                                                     
Ign http://security.ubuntu.com nadia-security/multiverse Translation-en                                                                                                                        
Ign http://security.ubuntu.com nadia-security/restricted Translation-en_US                                                                                                                     
Ign http://security.ubuntu.com nadia-security/restricted Translation-en                                                                                                                        
Ign http://security.ubuntu.com nadia-security/universe Translation-en_US                                                                                                                       
Ign http://security.ubuntu.com nadia-security/universe Translation-en                                                                                                                          
Err http://packages.medibuntu.org nadia/free amd64 Packages                                                                                                                                    
  404  Not Found
Err http://packages.medibuntu.org nadia/non-free amd64 Packages                                                                                                                                
  404  Not Found
Err http://packages.medibuntu.org nadia/free i386 Packages                                                                                                                                     
  404  Not Found
Err http://packages.medibuntu.org nadia/non-free i386 Packages                                                                                                                                 
  404  Not Found
Ign http://packages.medibuntu.org nadia/free Translation-en_US                                                                                                                                 
Ign http://packages.medibuntu.org nadia/free Translation-en
Ign http://packages.medibuntu.org nadia/non-free Translation-en_US
Ign http://packages.medibuntu.org nadia/non-free Translation-en
Err http://archive.ubuntu.com nadia/main amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://archive.ubuntu.com nadia/restricted amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://archive.ubuntu.com nadia/universe amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://archive.ubuntu.com nadia/multiverse amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://archive.ubuntu.com nadia/main i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://archive.ubuntu.com nadia/restricted i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://archive.ubuntu.com nadia/universe i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://archive.ubuntu.com nadia/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Ign http://archive.ubuntu.com nadia/main Translation-en_US
Ign http://archive.ubuntu.com nadia/main Translation-en
Ign http://archive.ubuntu.com nadia/multiverse Translation-en_US
Ign http://archive.ubuntu.com nadia/multiverse Translation-en
Ign http://archive.ubuntu.com nadia/restricted Translation-en_US
Ign http://archive.ubuntu.com nadia/restricted Translation-en
Ign http://archive.ubuntu.com nadia/universe Translation-en_US
Ign http://archive.ubuntu.com nadia/universe Translation-en
Err http://archive.ubuntu.com nadia-updates/main amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://archive.ubuntu.com nadia-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://archive.ubuntu.com nadia-updates/universe amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://archive.ubuntu.com nadia-updates/multiverse amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://archive.ubuntu.com nadia-updates/main i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://archive.ubuntu.com nadia-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://archive.ubuntu.com nadia-updates/universe i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://archive.ubuntu.com nadia-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Ign http://archive.ubuntu.com nadia-updates/main Translation-en_US
Ign http://archive.ubuntu.com nadia-updates/main Translation-en
Ign http://archive.ubuntu.com nadia-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com nadia-updates/multiverse Translation-en
Ign http://archive.ubuntu.com nadia-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com nadia-updates/restricted Translation-en
Ign http://archive.ubuntu.com nadia-updates/universe Translation-en_US
Ign http://archive.ubuntu.com nadia-updates/universe Translation-en
Fetched 185 kB in 26s (6,856 B/s)
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/nadia-security/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/nadia-security/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/nadia-security/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/nadia-security/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/nadia-security/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/nadia-security/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/nadia-security/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/nadia-security/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/nadia/partner/binary-amd64/Packages  404  Not Found [IP: 91.189.92.191 80]

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/nadia/partner/binary-i386/Packages  404  Not Found [IP: 91.189.92.191 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nadia/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nadia/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nadia/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nadia/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nadia/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nadia/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nadia/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nadia/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nadia-updates/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nadia-updates/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nadia-updates/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nadia-updates/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nadia-updates/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nadia-updates/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nadia-updates/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nadia-updates/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://packages.medibuntu.org/dists/nadia/free/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://packages.medibuntu.org/dists/nadia/non-free/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://packages.medibuntu.org/dists/nadia/free/binary-i386/Packages  404  Not Found

W: Failed to fetch http://packages.medibuntu.org/dists/nadia/non-free/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

I'm not sure if it's affecting the software manager either.  It says there are 2085 packages total avaliable, but I know there is more like 40000 packages....I believe that the two issues are related.  I can;t install the necessary packages to install the printer...

---

### Post by pdc on 2013-01-25
> .I believe that the two issues are related. I can;t install the necessary packages to install the printer... 

>  I've looked at the this thread and downloaded the 3.40.1 drivers.

1) Install the MP280 driver

if you downloaded the .tar.gz to your Downloads directory, if you want to copy and paste some commands: open a terminal

> cd Downloads

> tar -zxvf cnijfilter-mp280series-3.40-1-deb.tar.gz

> cd cnijfilter-mp280series-3.40-1-deb

> ./install.sh

......the install script should see if you have 32bit or 64bit (you tell us you have 64bit) and all should be good: post back if not

....those on the Mint forum would be curious that you post on the Ubuntu forum ..........

.....I won't comment here on the apt-get update issues

your printer has the scanner side: Canon make scangear available to run the scanner: do you want advice on how to install and run that: it is a good programme

---

### Post by Scozzar on 2013-01-26
Well I did a clean install.  I still get the update errors.  I can install the drivers, but I don't know if I'm going to do a clean install again.  I posted here because the Mint forums are pretty much dead.  I can post my sources.list if you want.  I believe that that is screwing up.

---

### Post by xenopeek on 2013-01-26
The following command will edit two sources files on Linux Mint 14 KDE, and make sure they are using the Ubuntu release name in their configuration (as these sources files are for Ubuntu or related repositories) and not the Linux Mint release name.
```
sudo sed -i 's/nadia/quantal/' /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/ubuntu.list
```
After running that command, please try doing:
```
apt update
```
Any more errors, please share here and include the output of:
```
inxi -r
```

---

### Post by Erik1984 on 2013-01-26
That's what I noticed too. The mint release names don't seem to exist on the Ubuntu server (not all that strange :P) as package folders.

---

### Post by Scozzar on 2013-01-26
> **xenopeek said:**
> The following command will edit two sources files on Linux Mint 14 KDE, and make sure they are using the Ubuntu release name in their configuration (as these sources files are for Ubuntu or related repositories) and not the Linux Mint release name.
```
sudo sed -i 's/nadia/quantal/' /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/ubuntu.list
```After running that command, please try doing:
```
apt update
```Any more errors, please share here and include the output of:
```
inxi -r
```

OH...MY....GOD....It worked I think.  I updated it!  Then I ran sudo apt-get update and updated that!!!  I'm gonna tell everyone about this.  THANK YOU

---

### Post by xenopeek on 2013-01-26
Thanks for confirming the solution. Enjoy Linux Mint and KDE all upgraded ;)

---

