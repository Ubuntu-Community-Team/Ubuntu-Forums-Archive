---
title: "Suddenly, I can't play videos"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by blazini on 2007-12-27
I got the update notification in my panel, so I dled the updates. It also popped up that I can update to  a new version of Ubuntu. The update only went halfway then errors popped up. I restarted, now none of my media player work at all besides VLC. Even that doesn't always work. Any idea where to start?

---

### Post by taurus on 2007-12-27
Try running these two commands from a terminal to see what's wrong with the update/upgrade.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by blazini on 2007-12-27
in the update, plenty of packages get come down fine then errors start...........

Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                          
  404 Not Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                      
  404 Not Found
Err [http://ubuntu.geole.info](http://ubuntu.geole.info) feisty/universe Packages                          
  404 Not Found
Err [http://ubuntu.geole.info](http://ubuntu.geole.info) feisty/multiverse Packages                        
  404 Not Found
Err [http://ubuntu.geole.info](http://ubuntu.geole.info) feisty/universe Sources                           
  404 Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources                     
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources                   
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                           
  404 Not Found
Err [http://ubuntu.geole.info](http://ubuntu.geole.info) feisty/multiverse Sources                         
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources             
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources                        
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                       
  404 Not Found
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                       
Get:11 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release.gpg [191B]                 
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Translation-en_US                
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release                               
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Packages                         
Fetched 6389B in 10s (587B/s)                                                  
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.gz)  404 Not Found [IP: 8.15.7.100 80]
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/feisty/universe/binary-amd64/Packages.gz](http://ubuntu.geole.info/dists/feisty/universe/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/feisty/multiverse/binary-amd64/Packages.gz](http://ubuntu.geole.info/dists/feisty/multiverse/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/feisty/universe/source/Sources.gz](http://ubuntu.geole.info/dists/feisty/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/feisty/multiverse/source/Sources.gz](http://ubuntu.geole.info/dists/feisty/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.



The upgrade comes up

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

I guess that means there's nothing to upgrade?

---

### Post by taurus on 2007-12-27
You have problem with some repos in your /etc/apt/sources.list.

```

Failed to fetch http://wine.lowvoice.nl/apt/dists/fe...64/Packages.gz 404 Not Found [IP: 8.15.7.100 80]
Failed to fetch http://medibuntu.sos-sts.com/repo/di...64/Packages.gz 404 Not Found
Failed to fetch http://ubuntu.geole.info/dists/feist...64/Packages.gz 404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/di...64/Packages.gz 404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/di...rce/Sources.gz 404 Not Found
Failed to fetch http://ubuntu.geole.info/dists/feist...64/Packages.gz 404 Not Found
Failed to fetch http://ubuntu.geole.info/dists/feist...rce/Sources.gz 404 Not Found
Failed to fetch http://ubuntu.geole.info/dists/feist...rce/Sources.gz 404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/di...rce/Sources.gz 404 Not Found

```

So, you need to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of those repos to comment them out.  Save the changes and close down gedit window.  Now, run those two commands again.

```
sudo apt-get update
sudo apt-get upgrade
```

And if you want to include Medibuntu, use this guide for the repo.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Also, comment out the beryl repos for Edgy.

---

### Post by blazini on 2007-12-27
Hey thanks man

I've got my repositories fixed, and I don't get any errors on the update, but all my media players still crash when I try to open a video.

---

### Post by taurus on 2007-12-27
Look at the link in my previous post. Medibuntu, for your codecs.

---

### Post by Seti on 2007-12-27
Also if you go to >System>Administration>Software Sources, change the site that you're getting your updates from. There's even a tool to determine the best server to download from.

As for the inability to play video, can you give a better description of the difficulty you're having there? is mplayer giving you an error? or is the video distorted?

---

### Post by blazini on 2007-12-27
taurus......
I updated all the codecs from the medibuntu repsitory and my media players still crash

seti...........
Kaffeine, mplayer and movieplayer all do the same thing. I doubleclick a video, the open but close/crash before displaying any video. VLC will open videos but only when I right click, choose open with other program, and use custom command "vlc player"

---

### Post by blazini on 2007-12-27
I think it has to do with the partial failed upgrade to Gutsy from Feisty. Is there anyway to either revert completely to feisty or go to gutsy? 

Edit: I get this error when I use the sudo apt-get upgrade command............
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Perfect Storm on 2007-12-27
> **blazini said:**
> taurus......
I updated all the codecs from the medibuntu repsitory and my media players still crash

seti...........
Kaffeine, mplayer and movieplayer all do the same thing. I doubleclick a video, the open but close/crash before displaying any video. VLC will open videos but only when I right click, choose open with other program, and use custom command "vlc player"

In properties of the media file then ---> "open with", you can set VLC to be default.

---

### Post by Seti on 2007-12-27
"I updated all the codecs from the medibuntu repsitory and my media players still crash"

Have you tried maybe restarting your X session after updating? Sometimes that helps.

---

### Post by blazini on 2007-12-28
> **Artificial Intelligence said:**
> In properties of the media file then ---> "open with", you can set VLC to be default.

Doesn't work. I can't right click on any media files, it doesn't do anything

---

### Post by Perfect Storm on 2007-12-28
Which DE do you have?

---

### Post by dark_harmonics on 2007-12-28
I hate to be the one to suggest this, but a partially failed upgrade can be an extremely hairy thing to fix. I had a similar situation with one of my computers and after fighting the 1000 small issues and building frustration with Ubuntu, I gave up and reinstalled my OS cleanly. 

Lets face it, no OS is stable after a failed upgrade. Its a testament to Ubuntu that it even works at all. You can certainly ignore my post, and others will definitely disagree, but if this were my computer I would be saving my files and preparing for a fresh, clean rebuild.

---

### Post by blazini on 2007-12-28
> **dark_harmonics said:**
> I hate to be the one to suggest this, but a partially failed upgrade can be an extremely hairy thing to fix. I had a similar situation with one of my computers and after fighting the 1000 small issues and building frustration with Ubuntu, I gave up and reinstalled my OS cleanly. 

Lets face it, no OS is stable after a failed upgrade. Its a testament to Ubuntu that it even works at all. You can certainly ignore my post, and others will definitely disagree, but if this were my computer I would be saving my files and preparing for a fresh, clean rebuild.I agree with ya, but the upgrade failed during the first step, where it was downloading things. I wouldn't think the OS would modify things during that phase.

Thanks to Taurus, my repositories are fixed. The upgrade seems to be working and I'm retrying it now. With any luck, the issues will fix themselves.

---

### Post by blazini on 2007-12-28
Ok the upgrade seemed to have fixed everything, my bluetooth even works now.

---

### Post by dark_harmonics on 2007-12-29
> **blazini said:**
> I agree with ya, but the upgrade failed during the first step, where it was downloading things. I wouldn't think the OS would modify things during that phase.

Thanks to Taurus, my repositories are fixed. The upgrade seems to be working and I'm retrying it now. With any luck, the issues will fix themselves.

oh ok. I was under the impressions that your upgrade ran partway through the installation part. You are correct (obviously since it worked haha!). The computer i had this happen to actually crashed during the installation not just when it downloads.

---

