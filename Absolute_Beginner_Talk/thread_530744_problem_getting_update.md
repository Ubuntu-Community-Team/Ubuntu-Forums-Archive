---
title: "problem getting update"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by axemurder785 on 2007-08-20
I am trying to install wine. was told to type: "sudo aptitude update" in the terminal. when i did that this came up: sam@SAMONABUN:~$ sudo aptitude update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US       
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US     
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US         
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release [32.4kB]                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US       
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release [50.9kB]               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US            
Get:6 [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release.gpg [189B]                  
Ign [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch/main Translation-en_US                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                 
Get:7 [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release [5535B]                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                           
Ign [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                     
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages [14B]        
Hit [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages          
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages [54.7kB]
Get:10 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_US               
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages [6360B]   
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages [2100B]     
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release                              
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages [7785B]       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                        
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [66.6kB]        
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources                         
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                        
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages [6101B]   
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages [26.5kB]    
Fetched 260kB in 50s (5169B/s)                                                  
Reading package lists... Done
W: GPG error: [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

what does that mean that the public key is not available?

---

### Post by Hobo Joe on 2007-08-20
I'm not positive,(in fact, I could be horribly wrong) but I don't think that is anything that will affect you.

---

### Post by axemurder785 on 2007-08-20
ok, i guess it dosen't really matter anyway b/c i am getting a new dell xps pre-loaded with ubuntu in a month

---

### Post by splintercellguy on 2007-08-20
You forgot to add the repo key for the Wine repo that will mark it as trusted. You should do:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

EDIT: Oops, looks like you're not using Wine's repo. You'll have to add the GPG key in a similar fashion for the debian-multimedia repo.

---

