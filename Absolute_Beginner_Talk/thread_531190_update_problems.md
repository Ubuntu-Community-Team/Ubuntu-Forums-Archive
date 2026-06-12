---
title: "update problems"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by JonD25 on 2007-08-21
Ok, I've been having various update problems, and I'm not sure how to fix them. A bunch of my third party repositories I've added can't seem to connect. Here's the output from terminal.

```
$ sudo apt-get update
Password:
Err http://wine.lowvoice.nl feisty Release.gpg
  Could not resolve 'wine.lowvoice.nl'
Err http://wine.lowvoice.nl feisty/main Translation-en_US                      
  Could not resolve 'wine.lowvoice.nl'
Ign http://wine.lowvoice.nl feisty Release                                     
Ign http://wine.lowvoice.nl feisty/main Packages                               
Err http://wine.lowvoice.nl feisty/main Packages                               
  Could not resolve 'wine.lowvoice.nl'
Err http://www.telmail.fi feisty Release.gpg                                   
  Could not resolve 'www.telmail.fi'
Ign http://www.telmail.fi feisty Release                                       
Ign http://www.telmail.fi feisty/fonts Sources                                 
Get:1 http://archive.canonical.com feisty-commercial Release.gpg [191B]        
Ign http://archive.canonical.com feisty-commercial/main Translation-en_US      
Err http://www.telmail.fi feisty/fonts Sources                                 
  Could not resolve 'www.telmail.fi'
Get:2 http://dl.google.com stable Release.gpg [189B]                           
Ign http://dl.google.com stable/non-free Translation-en_US                     
Get:3 http://repository.debuntu.org feisty Release.gpg [189B]                  
Hit http://dl.google.com stable Release                                        
Hit http://archive.canonical.com feisty-commercial Release                     
Ign http://getswiftfox.com unstable Release.gpg                                
Get:4 http://archive.ubuntustudio.org feisty Release.gpg [189B]                
Ign http://archive.ubuntustudio.org feisty/main Translation-en_US              
Get:5 http://wine.budgetdedicated.com feisty Release.gpg [191B]                
Ign http://wine.budgetdedicated.com feisty/main Translation-en_US              
Get:6 http://www.getautomatix.com feisty Release.gpg [189B]                    
Ign http://www.getautomatix.com feisty/main Translation-en_US                  
Hit http://dl.google.com stable/non-free Packages                              
Ign http://getswiftfox.com unstable/non-free Translation-en_US                 
Get:7 http://hendrik.kaju.pri.ee feisty Release.gpg [189B]                     
Ign http://hendrik.kaju.pri.ee feisty/screenlets Translation-en_US             
Hit http://archive.canonical.com feisty-commercial/main Packages               
Hit http://www.getautomatix.com feisty Release                                 
Hit http://archive.ubuntustudio.org feisty Release                             
Hit http://wine.budgetdedicated.com feisty Release                             
Ign http://repository.debuntu.org feisty/multiverse Translation-en_US          
Ign http://getswiftfox.com unstable Release                                    
Hit http://hendrik.kaju.pri.ee feisty Release                                  
Get:8 http://archive.ubuntu.com feisty-backports Release.gpg [191B]            
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US          
Get:9 http://us.archive.ubuntu.com feisty Release.gpg [191B]                   
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                 
Get:10 http://security.ubuntu.com feisty-security Release.gpg [191B]           
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Hit http://www.getautomatix.com feisty/main Packages                           
Hit http://archive.ubuntustudio.org feisty/main Packages                       
Ign http://wine.budgetdedicated.com feisty/main Packages                       
Get:11 http://www.telemail.fi feisty Release.gpg [189B]                        
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US    
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US      
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US    
Get:12 http://archive.ubuntu.com feisty-updates Release.gpg [191B]             
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_US      
Hit http://repository.debuntu.org feisty Release                               
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US           
Ign http://getswiftfox.com unstable/non-free Packages                          
Get:13 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]          
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US   
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US      
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US    
Hit http://wine.budgetdedicated.com feisty/main Sources                        
Hit http://getswiftfox.com unstable/non-free Packages                          
Get:14 http://archive.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://archive.ubuntu.com feisty-security/main Translation-en_US           
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_US     
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_US       
Hit http://us.archive.ubuntu.com feisty Release                                
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_US     
Hit http://archive.ubuntu.com feisty-backports Release                         
Hit http://security.ubuntu.com feisty-security Release                         
Hit http://us.archive.ubuntu.com feisty-updates Release                        
Hit http://wine.budgetdedicated.com feisty/main Packages                       
Hit http://repository.debuntu.org feisty/multiverse Packages                   
Hit http://archive.ubuntu.com feisty-updates Release                           
Ign http://www.telemail.fi feisty/fonts Translation-en_US                      
Hit http://archive.ubuntu.com feisty-security Release                          
Hit http://us.archive.ubuntu.com feisty/main Packages                          
Hit http://us.archive.ubuntu.com feisty/restricted Packages                    
Hit http://us.archive.ubuntu.com feisty/main Sources                           
Hit http://security.ubuntu.com feisty-security/main Packages                   
Hit http://repository.debuntu.org feisty/multiverse Sources                    
Hit http://archive.ubuntu.com feisty-backports/main Packages                   
Hit http://archive.ubuntu.com feisty-backports/restricted Packages             
Hit http://archive.ubuntu.com feisty-backports/universe Packages               
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages             
Hit http://us.archive.ubuntu.com feisty/restricted Sources                     
Hit http://us.archive.ubuntu.com feisty/universe Packages                      
Hit http://us.archive.ubuntu.com feisty/universe Sources                       
Hit http://us.archive.ubuntu.com feisty/multiverse Packages                    
Hit http://us.archive.ubuntu.com feisty/multiverse Sources                     
Hit http://security.ubuntu.com feisty-security/restricted Packages             
Hit http://security.ubuntu.com feisty-security/main Sources                    
Hit http://security.ubuntu.com feisty-security/restricted Sources              
Hit http://us.archive.ubuntu.com feisty-updates/main Packages                  
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages            
Hit http://us.archive.ubuntu.com feisty-updates/main Sources                   
Hit http://hendrik.kaju.pri.ee feisty/screenlets Packages                      
Hit http://archive.ubuntu.com feisty-updates/universe Packages                 
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages               
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources             
Get:15 http://www.telemail.fi feisty Release [1228B]                           
Hit http://security.ubuntu.com feisty-security/universe Packages               
Hit http://security.ubuntu.com feisty-security/universe Sources                
Hit http://security.ubuntu.com feisty-security/multiverse Packages             
Hit http://security.ubuntu.com feisty-security/multiverse Sources              
Hit http://archive.ubuntu.com feisty-security/main Packages                    
Hit http://archive.ubuntu.com feisty-security/restricted Packages              
Hit http://archive.ubuntu.com feisty-security/universe Packages                
Hit http://archive.ubuntu.com feisty-security/multiverse Packages              
Ign http://www.telemail.fi feisty/fonts Packages                               
Get:16 http://www.telemail.fi feisty/fonts Packages [3271B]                    
Err http://download.tuxfamily.org feisty Release.gpg                           
  Could not connect to download.tuxfamily.org:80 (88.191.250.18), connection timed out
Err http://download.tuxfamily.org feisty/eyecandy Translation-en_US
  Could not connect to download.tuxfamily.org:80 (88.191.250.18), connection timed out
Err http://download.tuxfamily.org feisty Release.gpg      
  Could not connect to download.tuxfamily.org:80 (88.191.250.18), connection timed out
Err http://download.tuxfamily.org feisty/avant-window-navigator Translation-en_US
  Could not connect to download.tuxfamily.org:80 (88.191.250.18), connection timed out
Err http://download.tuxfamily.org feisty/exaile-svn Translation-en_US
  Could not connect to download.tuxfamily.org:80 (88.191.250.18), connection timed out
Fetched 4701B in 10m0s (8B/s)                             
Failed to fetch http://download.tuxfamily.org/3v1deb/dists/feisty/Release.gpg  Could not connect to download.tuxfamily.org:80 (88.191.250.18), connection timed out
Failed to fetch http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/i18n/Translation-en_US.bz2  Could not connect to download.tuxfamily.org:80 (88.191.250.18), connection timed out
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/Release.gpg  Could not connect to download.tuxfamily.org:80 (88.191.250.18), connection timed out
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/i18n/Translation-en_US.bz2  Could not connect to download.tuxfamily.org:80 (88.191.250.18), connection timed out
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/exaile-svn/i18n/Translation-en_US.bz2  Could not connect to download.tuxfamily.org:80 (88.191.250.18), connection timed out
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg  Could not resolve 'wine.lowvoice.nl'
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2  Could not resolve 'wine.lowvoice.nl'
Failed to fetch http://www.telmail.fi/mlind/ubuntu/dists/feisty/Release.gpg  Could not resolve 'www.telmail.fi'
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz  Could not resolve 'wine.lowvoice.nl'
Failed to fetch http://www.telmail.fi/mlind/ubuntu/dists/feisty/fonts/source/Sources.gz  Could not resolve 'www.telmail.fi'
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

It's also taking forever trying to connect to get all these updates. Have the repos changed? Is it a problem with my network connection? If they changed, it just seems really inconvenient, because it's not like I can keep up with all the different places where I found how to install all this different software, so if someone changes one, I basically get no more updates ever on that piece of software.

---

### Post by ddrichardson on 2007-08-21
Haave you tried it again? Only checked one of the problem repos and its up and running fine.

---

### Post by JonD25 on 2007-08-21
Yes. SEVERAL times. Over and over. Same thing every time. I usually use the GUI version, but I figured the terminal output would be more helpful.

---

### Post by ddrichardson on 2007-08-21
It is a particularly large source list. Ping the missing addresses first to make sure there isn't a resolution issue.

---

### Post by JonD25 on 2007-08-23
I tried that. Everything that I'm getting errors on, it says it can't find the addresses. download.tuxfamily.org can't even be found at all, let alone the specific ones for AWN and Compiz Fusion that I want. This is incredibly frustrating.

OK, I'm pretty sure it's my network, for whatever reason. I asked a friend on a different network to go to one that's not working for me, download.tuxfamily.org/3v1deb/, and she told me it came up fine for her.

---

### Post by ddrichardson on 2007-08-23
Have you tried putting in ip addresses rather than dns - just to clear that there are no DNS problems.

---

### Post by JonD25 on 2007-08-23
[http://88.191.250.18/](http://88.191.250.18/) doesn't work (I used Network Tools Lookup function to get that).

---

### Post by ddrichardson on 2007-08-23
Are you unable to access any services? Was your network working previously?

---

### Post by JonD25 on 2007-08-23
I could connect to he repo fine maybe a week ago. My internet is working perfectly fine now, seeing as how I'm using it now to make this post.

I'm on a college network now, and they tend to block some sites using WebSense, however if that were the problem, I'd just get a page that said it's been blocked. It wouldn't just time out on me like it's been doing. But, I suppose it could be something else to do with my network. Later today I'm going to connect to a different network off campus and see if it works.

---

### Post by ddrichardson on 2007-08-23
They aren't blocking those ports or sites are they?

---

### Post by JonD25 on 2007-08-23
I was right. It was just the college's network. I'm on my home network now, and it worked fine. Weird.

The thing is, if they were blocking those sites, it would tell me, "This site has been blocked by WebSense" or something like that. It never just times out on blocked sites. There has to be some other way they're blocking it though, whether intentionally or not. Weird. Guess I'll have to do all my updates at home from now on, even though I really mostly use this computer at work.

---

### Post by ddrichardson on 2007-08-23
I don't know - this is just a guess, but web pages are usually on port 80 - I'm not sure if apt-get is on the same port (probably it is). Its very easy to block ports.

---

