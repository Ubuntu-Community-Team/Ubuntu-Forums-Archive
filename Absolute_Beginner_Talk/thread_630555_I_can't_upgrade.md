---
title: "I can't upgrade"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by sentientd on 2007-12-03
When I try to upgrade to 7.04 using the Update Manager, I get the following error...

"Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/Release.gpg](http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/Release.gpg) Could not resolve 'nvidia.limitless.lupine.me.uk'
Failed to fetch [http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/i18n/Translation-en_US.bz2](http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/i18n/Translation-en_US.bz2) Could not resolve 'nvidia.limitless.lupine.me.uk'
Failed to fetch [http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/binary-i386/Packages.gz](http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/binary-i386/Packages.gz) Could not resolve 'nvidia.limitless.lupine.me.uk'"

I can't imagine that I'm having any network problems because everything else seems to be working fine. 

I can't upgrade because my only option is to press "Close" and then nothing happens at all.

I've been having problems with my drivers... but I really just want to upgrade.... urg...

I'm really new and I don't have any idea what to do about this.

---

### Post by FuturePilot on 2007-12-03
Can you post your sources.list 
```
cat /etc/apt/sources.list
```

---

### Post by sentientd on 2007-12-03
> **FuturePilot said:**
> Can you post your sources.list 
```
cat /etc/apt/sources.list
```

Is this it?

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted multiverse universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted multiverse universe main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse universe main

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse universe main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse universe main
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

---

### Post by FuturePilot on 2007-12-03
Yes that is it.
```
deb http://us.archive.ubuntu.com/ubuntu/ edgy restricted multiverse universe main
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy restricted multiverse universe main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates restricted multiverse universe main
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates restricted multiverse universe main

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
[B]# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe[/B]

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[B]# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse[/B]

deb http://security.ubuntu.com/ubuntu edgy-security restricted multiverse universe main
deb-src http://security.ubuntu.com/ubuntu edgy-security restricted multiverse universe main
[B]# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe[/B]
**[COLOR="Blue"]deb http://nvidia.limitless.lupine.me.uk/ubuntu edgy stable[/COLOR]**
[B][COLOR="Blue"]deb http://ubuntu.beryl-project.org/ edgy main
deb http://ubuntu.beryl-project.org feisty main
deb-src http://ubuntu.beryl-project.org feisty main[/COLOR][/B]
```
Uncomment the lines in **Bold** by removing the # in the front.
Comment out the lines in [COLOR="Blue"]Blue[/COLOR] by placing a # in front of the line
Then run
```
sudo apt-get update
sudo apt-get -u upgrade
```
before attempting to upgrade to Feisty

---

### Post by sentientd on 2007-12-03
> **FuturePilot said:**
> 
Uncomment the lines in **Bold** by removing the # in the front.
Comment out the lines in [COLOR="Blue"]Blue[/COLOR] by placing a # in front of the line
Then run
```
sudo apt-get update
sudo apt-get -u upgrade
```
before attempting to upgrade to Feisty

So do I copy that entire large box of text directly into my terminal and press enter after commenting and uncommenting the specific sections?

Then do I press enter?

I did that and I also tried putting in the next two lines of code individually.

I got this:

dasjinka@dasjinka-desktop:~$ sudo apt-get update
Password:
Err [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy Release.gpg
  Could not resolve 'nvidia.limitless.lupine.me.uk'
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US      
Get:2 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release.gpg [191B]                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg [191B]                  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_US                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US             
Err [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy/stable Translation-en_US         
  Could not resolve 'nvidia.limitless.lupine.me.uk'
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Translation-en_US                
Get:5 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg [191B]                
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                   
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US     
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release                               
Ign [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy Release                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Ign [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy/stable Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages                      
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release                             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources                          
Err [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy/stable Packages                  
  Could not resolve 'nvidia.limitless.lupine.me.uk'
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                            
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources     
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Packages               
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources                     
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages                       
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Sources     
Fetched 386B in 1s (252B/s)                                 
Failed to fetch [http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/Release.gpg](http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/Release.gpg)  Could not resolve 'nvidia.limitless.lupine.me.uk'
Failed to fetch [http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/i18n/Translation-en_US.bz2](http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/i18n/Translation-en_US.bz2)  Could not resolve 'nvidia.limitless.lupine.me.uk'
Failed to fetch [http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/binary-i386/Packages.gz](http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/binary-i386/Packages.gz)  Could not resolve 'nvidia.limitless.lupine.me.uk'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
dasjinka@dasjinka-desktop:~$ sudo apt-get -u upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I'm probably doing it wrong! 

I went back into the Upgrade manager and tried to upgrade but I had the same problem still.

---

### Post by rsambuca on 2007-12-03
You have to make those suggested edits using a text editor```
gksudo gedit /etc/apt/sources.list
```  I must say, however, that judging by your sources list, there is a very good chance that the upgrade will not go very smoothly.  Please make sure you have backed up all of your sensitive data first.

---

### Post by sentientd on 2007-12-03
> **rsambuca said:**
> You have to make those suggested edits using a text editor```
gksudo gedit /etc/apt/sources.list
```  I must say, however, that judging by your sources list, there is a very good chance that the upgrade will not go very smoothly.  Please make sure you have backed up all of your sensitive data first.

Yeah, I did the edits in the text editor. I guess maybe I'm lucky nothing happened anyways. 

I'd like to avoid having to reinstall because my husband set most things up for me, but after the kernel update things went awry. And the husband is overseas right now.  So I guess I'll just deal with it. 

Maybe I'll try again tomorrow. 

What sorts of things are wrong with my sources list? Can I fix any of them easily?

---

### Post by rsambuca on 2007-12-03
> **sentientd said:**
> Yeah, I did the edits in the text editor. I guess maybe I'm lucky nothing happened anyways. 

I'd like to avoid having to reinstall because my husband set most things up for me, but after the kernel update things went awry. And the husband is overseas right now.  So I guess I'll just deal with it. 

Maybe I'll try again tomorrow. 

What sorts of things are wrong with my sources list? Can I fix any of them easily?

I think you didn't save the changes to the sources.list, because the repository errors are still there.  You must use the command I gave you (with gksudo) and then press 'save' after the edits.  Try the edits again and then post your 

cat /etc/apt/sources.list again.


My concern over a smooth update for you is that you are using a few non-Ubuntu repositories.  That doesn't mean an upgrade won't work, but the more outside sources you use, the more likely you are to have problems.

---

### Post by sentientd on 2007-12-03
> **rsambuca said:**
> I think you didn't save the changes to the sources.list, because the repository errors are still there.  You must use the command I gave you (with gksudo) and then press 'save' after the edits.  Try the edits again and then post your 

cat /etc/apt/sources.list again.

Thanks!

Okay here we go! When you said Text editor I thought you meant quite literally the text editor program :P!  Cause I couldn't paste it into the terminal and make edits I had to paste it into a text file, edit it there, and then copy and paste it into the terminal... but this is something completely different I think! :P

Hope I didn't mess it up!

Here's what I get when I do 
cat /etc/apt/sources.list


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted multiverse universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted multiverse universe main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse universe main

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse universe main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse universe main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
# deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
# deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
# deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

---

### Post by LowSky on 2007-12-03
better off just doing a fresh install with gutsy

---

### Post by Sarteck on 2007-12-03
Looks great, now you can try a **sudo apt-get update**, then upgrade.  :)

---

### Post by sentientd on 2007-12-03
> **Sarteck said:**
> Looks great, now you can try a **sudo apt-get update**, then upgrade.  :)

Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg [191B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release                     
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release [50.9kB]   
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release                        
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                  
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages [6149B]
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources               
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages [5586B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [65.4kB]
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages [118kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources             
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources [928B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources [1007B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources [8913B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources [22.8kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources      
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [65.4kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources [8913B]
99% [16 Sources bzip2 0]                                
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_edgy-security_universe_source_Sources - open (2 No such file or directory)
Fetched 354kB in 2s (166kB/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.bz2)  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_edgy-security_universe_source_Sources - open (2 No such file or directory)
Reading package lists... Done
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Hmm... I think I am detecting some problems here :P

---

### Post by Sarteck on 2007-12-03
Here, I'll post a little guide that'll walk you through it a bit differently.  In the meantime, if someone has an alternate solution, feel free to post it.

---

### Post by FuturePilot on 2007-12-03
Nevermind

---

### Post by rsambuca on 2007-12-03
You need to use the text editor and fix your sources.  You have two duplicated sources.  Delete the lines I have highlighted in red.

> cat /etc/apt/sources.list


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted multiverse universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted multiverse universe main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse universe main

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse universe main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse universe main
[COLOR="Red"]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe[/COLOR]
# deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
# deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
# deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
# deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main 

---

### Post by rsambuca on 2007-12-03
> **FuturePilot said:**
> Try commenting out the first two lines that look like this
```
deb http://us.archive.ubuntu.com/ubuntu/ edgy restricted multiverse universe main
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy restricted multiverse universe main

```Then run 
```
sudo apt-get update
```

Sorry, that is wrong.

---

### Post by FuturePilot on 2007-12-03
Oops. :eek:

---

### Post by Sarteck on 2007-12-03
[EDIT]Try rsambuca's solution first--it's a lot more simple and will probably work better.  ^^;



First and foremost, backup any files you want to keep.  Using this method should NOT mess with the files in your /home/USER directories, but it's better to be safe than sorry.  I recommend burning your /home directory to DVD if it's small enough, or maybe copying it (tarred and/or gzipped) to a separate partition on your hard drive, if you have one.  If you need any help with this step, just let us know.

Now, to the meat and gravy of upgrading.


We are going to backup your original sources list, because we are going to edit it in a bit.  To back it up, ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```This *copies* it to the new filename, sources.list.bak in the /etc/apt/ directory.

Next, we are going to replace all occurrences of the word "edgy" with the word "feisty" in your sources list.  You -can- do this manually in a text editor, but it's much more simple with the command```
sudo sed -e &#8217;s/\edgy/ feisty/g&#8217; -i /etc/apt/sources.list
```

Now let's try to update the sources list again with the command I had you run before:```
sudo apt-get update
```

We'll pause here to see if/what errors you get.  (And if your problem is solved by the time I post this, then forget this post.  :D)

---

### Post by rsambuca on 2007-12-03
> **Sarteck said:**
> [EDIT]Try rsambuca's solution first--it's a lot more simple and will probably work better.  ^^;



First and foremost, backup any files you want to keep.  Using this method should NOT mess with the files in your /home/USER directories, but it's better to be safe than sorry.  I recommend burning your /home directory to DVD if it's small enough, or maybe copying it (tarred and/or gzipped) to a separate partition on your hard drive, if you have one.  If you need any help with this step, just let us know.

Now, to the meat and gravy of upgrading.


We are going to backup your original sources list, because we are going to edit it in a bit.  To back it up, ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```This *copies* it to the new filename, sources.list.bak in the /etc/apt/ directory.

Next, we are going to replace all occurrences of the word "edgy" with the word "feisty" in your sources list.  You -can- do this manually in a text editor, but it's much more simple with the command```
sudo sed -e &#8217;s/\edgy/ feisty/g&#8217; -i /etc/apt/sources.list
```

Now let's try to update the sources list again with the command I had you run before:```
sudo apt-get update
```

We'll pause here to see if/what errors you get.  (And if your problem is solved by the time I post this, then forget this post.  :D)

Wow.  This is definitely not the recommend method of upgrading from Edgy to Feisty.

---

### Post by Sarteck on 2007-12-03
Really?  It is on Ubuntugeek.com, heh.  The Command-Line Interface method.

---

### Post by sentientd on 2007-12-03
Alright! I just backed some files up. So lets see what happens now!

---

### Post by sentientd on 2007-12-03
> **rsambuca said:**
> You need to use the text editor and fix your sources.  You have two duplicated sources.  Delete the lines I have highlighted in red.

Okay this should be better:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted multiverse universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted multiverse universe main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse universe main

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse universe main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse universe main
# deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
# deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
# deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
# deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

---

### Post by sentientd on 2007-12-03
> **Sarteck said:**
> 

Next, we are going to replace all occurrences of the word "edgy" with the word "feisty" in your sources list.  You -can- do this manually in a text editor, but it's much more simple with the command```
sudo sed -e ’s/\edgy/ feisty/g’ -i /etc/apt/sources.list
```



Okay,

I tried that part and this came out:

dasjinka@dasjinka-desktop:~$ sudo sed -e ’s/\edgy/ feisty/g’ -i /etc/apt/sources.list
sed: -e expression #1, char 1: unknown command: `

I can't tell which char is wrong... if thats what its trying to tell me... :P

---

### Post by rsambuca on 2007-12-03
> **sentientd said:**
> Okay,

I tried that part and this came out:

dasjinka@dasjinka-desktop:~$ sudo sed -e ’s/\edgy/ feisty/g’ -i /etc/apt/sources.list
sed: -e expression #1, char 1: unknown command: `

I can't tell which char is wrong... if thats what its trying to tell me... :P

Just open your update manager.  If things are set up properly, you should see a prompt to upgrade to a new version.

[https://help.ubuntu.com/community/FeistyUpgrades]("https://help.ubuntu.com/community/FeistyUpgrades")

---

### Post by sentientd on 2007-12-03
> **rsambuca said:**
> Just open your update manager.  If things are set up properly, you should see a prompt to upgrade to a new version.

[https://help.ubuntu.com/community/FeistyUpgrades]("https://help.ubuntu.com/community/FeistyUpgrades")

Ohhhh YES!!! It looks like it's going to work! \\:D/

I'll let you know!

---

### Post by Sarteck on 2007-12-03
> **sentientd said:**
> Okay,

I tried that part and this came out:

dasjinka@dasjinka-desktop:~$ sudo sed -e &#8217;s/\edgy/ feisty/g&#8217; -i /etc/apt/sources.list
sed: -e expression #1, char 1: unknown command: `

I can't tell which char is wrong... if thats what its trying to tell me... :P

It's just not recognizing the quotation mark--you'd have to put in a regular one, I suppose.  Heh.  But first, try as rsambuca suggested, to see if that will work for you.  If not, then we'll go the "hard" route.  If so, then we won't even have to worry about it.  :)

[EDIT] Nevermind, I see that you are already. :D  Great, hope it works.

---

### Post by sentientd on 2007-12-04
Alright!  

I fell asleep while I was upgrading, but I finally made it to Gutsy!

The upgrade aborted about 2/3 of the way through to 7.10 :confused:

But everything seems to be working anyways. I guess I'll find out what's screwed up later :-\"

Also Gutsy prompted me to sort out my Nvidia problems. So that's great! :mrgreen:

I lost my window borders for a while there ](*,) and had to work that out. Beryl seemed to have something to do with it... or maybe not. So I've decided to abandon it.

I'm working on getting Compiz-Fusion set up. It seems to be the very same thing it just works better. :) Maybe there are some additional features, I haven't gone through it all yet.

Haha! Changing the cube caps seems to be sort of wonky. I was able to change the top one... I don't know when it finally decided to actually change but I looked up there later it was working. The bottom one.. not so much. :roll: lol

So all in all I think things seem to be going pretty well! :-D

Thank you guys!!! You're awesome! 

Even tho its been a little frustrating its also been lots and lots of fun! 

Thanks a lot!!!! :KS

---

