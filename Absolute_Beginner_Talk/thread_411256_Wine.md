---
title: "Wine"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Harkainos on 2007-04-16
I am having trouble getting wine to install to the Ubuntu 6.10.
I am very new to Linux. I took some classes... but they don't go into any depth.

I needed to open 'Extra Repositories' - per [http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)
and I followed the instructions on [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

The repositories wouldn't open - because the particular file doesn't exist?

then

I went to [http://www.winehq.com/](http://www.winehq.com/) and walked through their tutorial 
and I followed the instructions on [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

In both cases I cut/paste and in both cases nothing happened....

Am I missing something

---

### Post by ahaslam on 2007-04-16
Try this: [http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.35~winehq0~ubuntu~6.10-2_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.35~winehq0~ubuntu~6.10-2_i386.deb)

Much easier & no potential for regressions twice a month ;)

PS. the server is very slow atm, maybe that's the root of your problem.

---

### Post by YokoZar on 2007-04-16
> **Harkainos said:**
> I went to [http://www.winehq.com/](http://www.winehq.com/) and walked through their tutorial and I followed the instructions on [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

In both cases I cut/paste and in both cases nothing happened....

Am I missing something*Nothing* happened?  No error messages or anything? Maybe you already have Wine installed.

Could you tell us what the output of **dpkg -s wine** is please?

---

### Post by Harkainos on 2007-04-16
It did give me an error on one page... that some file wasn't there. I will need to rerun it and find out what the errors was..... 

I think it was an error like:

/etc/apt/source.lib doesn't exist..... but when i look in there it is there.... not sure what that is about lol


The last line before it closes is 'Package wine has no installation candidate'

---

### Post by Wikzo on 2007-04-16
*** Off topic***

Sorry, I just use this thread... but don't want to make a new one for a simple quiestion.

I have used Google, but I can't find a list over programs working in Wine. Can anyone please give me a link?

---

### Post by Harkainos on 2007-04-16
Per [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) I need to open terminal and type:

sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list

I just cut and paste.... first are those 2 different commands? Do I need to run each line seperately? I tried both ways and I get an error:


/etc/apt/sources.list : No such file or Directory

When I go to that directory, I see source.list_backup... but no source.list file

On psychocats the writer makes it sound like i created the directory and am supposed to 'cut and paste' the rest in.... what am i missing?

---

### Post by zvacet on 2007-04-16
[http://appdb.winehq.org/]("http://appdb.winehq.org/")

---

### Post by Harkainos on 2007-04-16
WOOOHOOOOO!!!!! I think I figured it out..... If you do have any other advise please lemme know. As you can tell I am very new

---

### Post by Harkainos on 2007-04-16
@ Anthony:

It gave me an Error: Wrong architecture i386'



Is the server down right now or something? I have the repositories open it just isn't downloading

---

### Post by Harkainos on 2007-04-16
I keep trying to download wine and it gives me an error:


No candidate version found for wine
No packages will be installed, upgraded, or removed.

---

### Post by ibanezix on 2007-04-16
You can read the instructions here:

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

on how to manually add their own repository and sudo apt-get install it then.

---

### Post by Maestro23 on 2007-04-16
*Enable all repositories.

Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

---

### Post by Harkainos on 2007-04-16
I did exactly what was on that page. Previous to my post and that was the final result.

---

### Post by Harkainos on 2007-04-16
I have enabled all repositories. I have walked through each step on the [www.winehq.com](www.winehq.com) download page. I have also run through the psycocats/ubuntu/wine page. Each time I try to download wine i get this error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for wine
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done


What is happening. I understand that wine isn't being installed. I am just curious why.

---

### Post by Maestro23 on 2007-04-16
Copy andPaste your /etc/apt/sources.list

> cat /etc/apt/sources.list

---

### Post by ahaslam on 2007-04-16
Try following the rest of the wine guide, under 'Building the Wine Package from Source using APT.'

PS. the server seems fine now ;)

---

### Post by Harkainos on 2007-04-16
Nah... I read there were a lot of bugs. LOL!!!

I am using 6.10.

I have followed both winehq.com and psycocats.com/ubuntu/wine walkthroughs. I was able to enable the repositories... just not downloading wine

---

### Post by Harkainos on 2007-04-16
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main 



This was taken directly from [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) page


Maybe someone could CAT their source.lib that does have wine... then I could use that

---

### Post by taurus on 2007-04-16
Did you remember to update the sources.list first before you attended to install wine?

```
sudo aptitude update
sudo aptitude install wine
```

---

### Post by Harkainos on 2007-04-16
yes

---

### Post by Maestro23 on 2007-04-16
*Edit:  Taurus beat me to it.

---

### Post by taurus on 2007-04-16
Any reason why you always post the same topics twice, wine and can't boot Windows?

[http://ubuntuforums.org/showthread.php?t=410930](http://ubuntuforums.org/showthread.php?t=410930)

---

### Post by Harkainos on 2007-04-16
That was a mistake. I couldn't find the last thread, so I made this one. Turns out it was like on page 7...
As for the windows one I was trying to keep it in this forum. but that didn't work :)

---

### Post by taurus on 2007-04-16
> **Harkainos said:**
> That was a mistake. I couldn't find the last thread, so I made this one. Turns out it was like on page 7...

I will merge the other one into this one.

> As for the windows one I was trying to keep it in this forum. but that didn't work :)

I moved and merged your Windows question into the Windows subforum.

---

### Post by Harkainos on 2007-04-16
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Get:2 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]           
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US         
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                 
Get:4 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg [191B]                   
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_US                 
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Fetched 6B in 1s (4B/s)
Reading package lists... Done

nick@nick-desktop:~$ sudo aptitude install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for wine
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

For some reason it isn't pulling up wine. Am I missing it in the repository? or list?

---

### Post by Harkainos on 2007-04-16
I think I found the source of my problem.... i just dont know what it means. Any clues?

nick@nick-desktop:~$ sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US        
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg [191B]                  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_US                
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                       
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release                               
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Fetched 6B in 1s (4B/s)  
[B]Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/Release](http://wine.budgetdedicated.com/apt/dists/edgy/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.[/B]

---

### Post by Harkainos on 2007-04-16
I am such a goon!!! Apparently, I downloaded the 64bit version of Ubuntu - thinking it was referring to my processor. I reinstalled Ubuntu using the i386 version. Now I can see my NTFS partitions. I will try to install Wine now. More to come later.

---

### Post by Harkainos on 2007-04-16
Good news. Wine did install (that that i have the correct OS), I can also see the NTFS partitions. Am I able to load one of those games using wine, or do I need to reinstall them?

---

