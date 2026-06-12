---
title: "Upgrade to Gutsy from Feisty"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by cazmatazzz on 2008-03-31
I cannot seem to upgrade to Gutsy from Feisty. Both methods on the website (network upgrade and alternate cd install upgrade) do not work. 

If i try the method through the update manager it does not tell me a new version is available. 
when i try the alternate cd install  it does not give me an option to upgrade, and  when i try alt+F2 and insert gksu "sh /cdrom/cdromupgrade" then nothing happens. 

i have already changed servers (software sources) but that didnt do much so i switched back to the main server. 

so can somebody please HELP to upgrade to gutsy??? this is no longer making sense to me!


here is some extra information which i dont know is useful or not:

caroline@Caz:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_AU
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_AU
Get:1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]        
Get:2 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper Release.gpg [189B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_AU      
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_AU                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_AU                    
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]            
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Translation-en_AU      
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_AU              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_AU              
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_AU            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_AU
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_AU 
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_AU
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_AU
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_AU
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages
Fetched 8B in 0s (14B/s) 
Reading package lists... Done
caroline@Caz:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  dpkg-dev fakeroot g++ g++-4.1 libatm1 libc6-dev libstdc++6-4.1-dev
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
caroline@Caz:~$ 


and my sources list


# deb cdrom:[Xubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe main restricted multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

## Medibuntu - Ubuntu 7.04 “Feisty”
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)


# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed universe main multiverse restricted

---

### Post by muteXe on 2008-03-31
Maybe a fresh install?  Back up you home folder, somewhere then do a fresh install of gutsy.
I tried to upgrade to gutsy a few months back via the update manager and that completely screwed up my entire ubuntu.  I had to do a fresh install of feisty (i wasn't prepared to go anywhere near gutsy after that happened).

mute

---

### Post by cazmatazzz on 2008-03-31
i wanted to do a fresh install but my external harddrive crashed a while back, so i cannot create a proper backup (which i am willing to take for granted with an upgrade.... i know thats kind of bad.)

---

### Post by vargasman on 2008-03-31
You could try to run it via the command line with:
```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by cazmatazzz on 2008-03-31
doesnt work either: this is what happens


caroline@Caz:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_AU
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_AU
Get:1 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper Release.gpg [189B]                   
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Translation-en_AU      
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_AU      
Get:4 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_AU      
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_AU                    
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_AU    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_AU
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_AU         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_AU
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_AU        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_AU
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_AU
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_AU    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper Release
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/universe Sources
Fetched 8B in 3s (2B/s)
Reading package lists... Done
caroline@Caz:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  dpkg-dev fakeroot g++ g++-4.1 libatm1 libc6-dev libstdc++6-4.1-dev
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
caroline@Caz:~$

---

### Post by luceerose on 2008-03-31
You need to edit your sources.list file & replace all instances of 'dapper' & 'feisty' with 'gutsy'

---

### Post by cazmatazzz on 2008-03-31
i think i have done that now, only i did not know what to do with the ones that say the full name (like in the first line)



# deb cdrom:[Xubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main restricted multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe

## Medibuntu - Ubuntu 7.04 “Feisty”
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)


# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted

---

### Post by cazmatazzz on 2008-03-31
now if i run the update manager it tells me i can only run a partial upgrade? shoudl i try to run the upgrade through the cd iso or should i run the partial upgrade through the update manager?
i am also creating back ups right now so perhaps its better to do a clean install but i think i might run into more problems then...

---

### Post by kpkeerthi on 2008-03-31
```

# deb cdrom:[Xubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
[COLOR="Red"]comment this line out[/COLOR] --> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
[COLOR="Red"]change to gutsy[/COLOR] --> change to gutsy --> deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
[COLOR="Red"]change to gutsy[/COLOR] --> deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted
[COLOR="Red"]change to gutsy[/COLOR] --> deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted

```

---

### Post by kpkeerthi on 2008-03-31
Just follow [this]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method_for_Adding_Repositories") instruction for adding gutsy repositories.

And then do
```
sudo aptitude update
```
```
sudo aptitude dist-upgrade
```

---

### Post by bumanie on 2008-03-31
Change Dapper Drake to Gutsy Gibbon in the first line and replace the dapper near the end of the same line with gutsy. There are still a couple of feisty entries that need to be changed to gutsy. Why not wait a few weeks and just do a fresh install of hardy? 
I don't know your drive sizes and layout, however, You could (reasonably safely) copy all your home data to the end of a drive and then choose manual at the partitioning stage to ensure that part of the drive is not touched. If you have two drives, you could put your home data there whilst you installed on the second drive - or buy another external drive.

---

### Post by Tomatz on 2008-03-31
Backup your files from the live cd then do a fresh install :)

---

### Post by luceerose on 2008-03-31
# deb cdrom:[Xubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) [COLOR="Red"]feisty[/COLOR] main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) [COLOR="Red"]feisty[/COLOR]-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) [COLOR="Red"]feisty[/COLOR]-updates main restricted

change those to gutsy

---

### Post by luceerose on 2008-03-31
The first two lines are just for using a cd-rom for upgrade.
You don't need those two lines at all, delete them.

---

### Post by cazmatazzz on 2008-03-31
ok i think its working now, its downloading a lot of packages which will take about 40 minutes. 

thanks a lot for all your help!

---

### Post by njparton on 2008-03-31
Isn't it "apt-get dist-upgrade -d" (with the additional -d on the end?).
 
I'll be upgrading to hardy soon so I just wanted to check :)

---

### Post by cazmatazzz on 2008-03-31
i didnt use the additional d at the end, i dont know if it will make a difference. everything works fine now, i have upgraded completely to gutsy (because i want to update to hardy as well when it arrives....)

---

