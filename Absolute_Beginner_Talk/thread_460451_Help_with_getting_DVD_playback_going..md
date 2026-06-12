---
title: "Help with getting DVD playback going."
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by amazingtaters on 2007-05-31
I was trying to get DVD playback to work, and was following the Enabling Multimedia in Feisty guide. I got down to last step, typed in to the terminal: sudo apt-get install libdvdcss2 w32codecs, and this is what came up in terminal. Please help.





```
:~$ wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
Password:
OK
kyle@Lappy386:~$ sudo apt-get update
Get:1 http://us.archive.ubuntu.com feisty Release.gpg [191B]                   
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US           
Get:2 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]           
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US   
Hit http://us.archive.ubuntu.com feisty Release                                
Hit http://us.archive.ubuntu.com feisty-updates Release                        
Hit http://us.archive.ubuntu.com feisty/main Packages                          
Hit http://us.archive.ubuntu.com feisty/restricted Packages                    
Hit http://us.archive.ubuntu.com feisty/main Sources                           
Hit http://us.archive.ubuntu.com feisty/restricted Sources                     
Hit http://us.archive.ubuntu.com feisty/universe Packages                      
Hit http://us.archive.ubuntu.com feisty/universe Sources                       
Hit http://us.archive.ubuntu.com feisty/multiverse Packages                    
Hit http://us.archive.ubuntu.com feisty/multiverse Sources                     
Get:3 http://wine.budgetdedicated.com feisty Release.gpg [191B]
Ign http://wine.budgetdedicated.com feisty/main Translation-en_US            
Get:4 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US        
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com feisty-updates/main Packages        
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages  
Hit http://us.archive.ubuntu.com feisty-updates/main Sources         
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources   
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://wine.budgetdedicated.com feisty Release
Err http://wine.budgetdedicated.com feisty Release
  
Hit http://security.ubuntu.com feisty-security Release
Get:5 http://wine.budgetdedicated.com feisty Release [1007B]
Ign http://wine.budgetdedicated.com feisty Release        
Hit http://security.ubuntu.com feisty-security/main Packages
Ign http://wine.budgetdedicated.com feisty/main Packages
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://wine.budgetdedicated.com feisty/main Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://wine.budgetdedicated.com feisty/main Packages
Fetched 1201B in 4s (300B/s)
Reading package lists... Done
W: GPG error: http://wine.budgetdedicated.com feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
kyle@Lappy386:~$ sudo apt-get install libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
```

---

### Post by yabbadabbadont on 2007-05-31
Neither of those are in the repositories for legal reasons.  To install libdvdcss2 run, in a terminal window, "sudo /usr/share/doc/libdvdread3/install-css.sh".  (without the quotes).  For the win32 codecs, you will have to get them from the mediaubuntu (or whatever it is called) site referred to in the wiki.

Edit: You will need to have the libdvdread3 package installed first.  :)

---

### Post by yabbadabbadont on 2007-05-31
OK, found the appropriate link for you:  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by amazingtaters on 2007-05-31
thanks for the help, I'm still looking for the w32 codecs but I'm on my way

---

### Post by yabbadabbadont on 2007-05-31
[http://medibuntu.sos-sts.com/repo/pool/feisty/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb](http://medibuntu.sos-sts.com/repo/pool/feisty/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb)

---

### Post by amazingtaters on 2007-05-31
wow thanks. I was having a time with those w32's

---

### Post by amazingtaters on 2007-05-31
w32codecs and libdvdcss2 packs are installed but still no dvd playback. Ideas? What would be needed to tell if it's a hardware problem or something.

---

### Post by amazingtaters on 2007-05-31
fixed it by switching out totem with the totem-xine frontend.

---

### Post by yabbadabbadont on 2007-05-31
That was going to be my next suggestion...  :D

I'm glad it is working for you now.

---

### Post by daimaru on 2007-05-31
> **amazingtaters said:**
> w32codecs and libdvdcss2 packs are installed but still no dvd playback. Ideas? What would be needed to tell if it's a hardware problem or something.
instead of installing the necessary stuff manually why dont you just use [automatix]("http://www.getautomatix.com") it never failed me and my dvd playback works just fine.
once you have automatix installed go to apps-->systemtools-->automatix 
in automatix click on "codecs and plugins" and choose "AUD-DVD Codecs" thats it .
edit: and if you want to do it manually go to [ubuntuguide.org]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs") follow the instructions and you have the same result.

---

