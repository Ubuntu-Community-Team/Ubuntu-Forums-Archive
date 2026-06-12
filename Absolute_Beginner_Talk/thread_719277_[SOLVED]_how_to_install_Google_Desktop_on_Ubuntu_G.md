---
title: "[SOLVED] how to install Google Desktop on Ubuntu Gutsy"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-03-09
Hello,
the following is an attempt to install Google Desktop (according to directions given at [http://linuxondesktop.blogspot.com/2007/11/creating-your-ultimate-ubuntu-710.html](http://linuxondesktop.blogspot.com/2007/11/creating-your-ultimate-ubuntu-710.html)). I noticed the "ERROR" line and thought I shouldn't go on. Can you please advise. Thanks. 

---------------------
daniele@al-Adab:~$ wget [http://dl.google.com/linux/google-repo-setup.sh](http://dl.google.com/linux/google-repo-setup.sh)
--09:35:15--  [http://dl.google.com/linux/google-repo-setup.sh](http://dl.google.com/linux/google-repo-setup.sh)
           => `google-repo-setup.sh.2'
Resolving dl.google.com... 209.85.135.176
Connecting to dl.google.com|209.85.135.176|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,784 (11K) [application/x-sh]

100%[====================================>] 10,784        44.33K/s             

09:35:16 (44.31 KB/s) - `google-repo-setup.sh.2' saved [10784/10784]

daniele@al-Adab:~$ sudo bash google-repo-setup.sh
Configuring for 'apt' package manager.

Using '/usr/bin/wget' to download key.

ERROR: Failed to download Google key from [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub).
daniele@al-Adab:~$ 
------------------------

---

### Post by hyperair on 2008-03-09
Install the ca-certificates package from Synaptic, or using apt-get:
```
sudo apt-get install ca-certificates
```

Then follow the instructions again. They should work properly this time.

---

### Post by kleo skywalker on 2008-03-09
I'm posting without looking at the tutorial you're trying to follow, but that's only because Google has clear and detailed instructions on their website.
You can just download and install the .deb package from [here]("http://desktop.google.com/en/linux/download.html") - you just have to click the package, GDebi Package Installer will do the rest. Or you could follow the steps [here]("http://www.google.com/linuxrepositories/ubuntu704.html") to add it to the repositories.

---

### Post by billgoldberg on 2008-03-09
I didn't read the instructions but google earth is in the medibuntu repositories.

It's better than installing it from a deb, because if you use the repo's google earth can be updated through the update manager.

Adding the medibuntu repo takes 30 seconds.

[link]("http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/")

---

### Post by al.adab on 2008-03-09
Many thanks hyperair!!! It works now.

---

### Post by luvit on 2008-03-14
That software is awesome! I use it everyday!
concise instructions for installing [_[COLOR=RoyalBlue]Google Toolbar[/COLOR]_]("http://www.yay4u.com/2008/03/installing-google-toolbar-on-ubuntu.html")
concise instructions for installing [_[COLOR=RoyalBlue]Google Desktop[/COLOR]_]("http://www.yay4u.com/2008/03/google-desktop-for-linux-firefox.html")
for real beginners ...I hope it's useful!;)

---

### Post by RedRat on 2008-03-14
> **luvit said:**
> That software is awesome! I use it everyday!
concise instructions for installing [_[COLOR=RoyalBlue]Google Toolbar[/COLOR]_]("http://www.yay4u.com/2008/03/installing-google-toolbar-on-ubuntu.html")
concise instructions for installing [_[COLOR=RoyalBlue]Google Desktop[/COLOR]_]("http://www.yay4u.com/2008/03/google-desktop-for-linux-firefox.html")
for real beginners ...I hope it's useful!;)

Hey I am curious. I too installed Google Desktop but after about a month my computer appeared to really slow down, particularly writing or copying files from one folder to another. I un-installed Google Desktop and my computer returned to normal. The only thing I could figure was it was taking so much time indexing files and their location. Has anybody else seen this???

---

### Post by luvit on 2008-03-14
I have not seen this. It would be interesting if you reinstalled to see if you would see these symptoms again ;)

---

### Post by RedRat on 2008-03-14
> **luvit said:**
> I have not seen this. It would be interesting if you reinstalled to see if you would see these symptoms again ;)

Well I also noticed it when I had that on Windows also, that is why I thought it was the indexing that caused it. The problem I have is that I download a lot of stuff and then burn it to a CD/DVD so there are a lot of changes going on. Since Desktop is/was a beta, I figured the guys at Google were still tinkering with it. I might give it a shot again in about 6 months when Ubuntu 8.04 is out and stabilized.

---

### Post by love2learn on 2008-03-24
I too am trying to get this installed from the same walkthrough but get this.

-------@-----laptop:~$ sudo apt-get install google-desktop-linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package google-desktop-linux

thanks for the help in advance

---

### Post by hyperair on 2008-03-24
Run ```
sudo apt-get update
```

---

### Post by love2learn on 2008-03-24
-@-laptop:~$ sudo apt-get update
[sudo] password for --:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) dists/stable/non-free/binary-i386/ Release.gpg        
Ign [http://dl.google.com](http://dl.google.com) dists/stable/non-free/binary-i386/ Translation-en_US  
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US                 
Hit [http://dl.google.com](http://dl.google.com) dists/stable/non-free/binary-i386/ Release            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US     
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Hit [http://dl.google.com](http://dl.google.com) dists/stable/non-free/binary-i386/ Packages           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                                                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
Fetched 4B in 22s (0B/s) 
Reading package lists... Done
--@--laptop:~$ sudo apt-get install google-desktop-linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package google-desktop-linux
---@-laptop:~$ 

I ran the apt update but still to no avail.

---

### Post by RedRat on 2008-03-24
I think you have to get this directly from the Google pages, I think that is where I got mine. I know that Google Earth is in the repository but I don't think Google Desktop is in the Apt-Get repository, could be wrong though. That is what the error message is telling you.

If I remember correctly, they had several packages, one for Debian.

---

### Post by love2learn on 2008-03-24
solved once again,
Thanks It was WAAAY  too easy going directly to google.

Thanks again

---

