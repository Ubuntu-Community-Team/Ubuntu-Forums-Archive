---
title: "updating repsitorys"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Tek-Noir on 2008-01-25
Hi everyone,

Im currently trying to update my canonical repositories but every time i tick to download i get Could not download all repository indexes error. Do i need to update the link and if so how and what should it be.

Cheers

---

### Post by wormser on 2008-01-25
Where are you doing this?  I was in update manager today and got a similar error.  They might have been doing some work on their sites.  It seems to be working fine right now.  Try it with the command line.

```
sudo apt-get update
```

---

### Post by Rocket2DMn on 2008-01-25
Post the outputs of these commands please:
```
sudo apt-get update
sudo apt-get install *nameofprogramtoinstall*
```

---

### Post by agim on 2008-01-25
Post the error message (copy and paste if you can). It will help us find out what errors are ocurring and what we can do about it.

---

### Post by Tek-Noir on 2008-01-25
Seems to have worked a bit but got this error

Some index files failed to download, they have been ignored, or old ones used instead.

Is that normal?

---

### Post by Tek-Noir on 2008-01-25
and when i go to add remove i get

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

and

[http://archive.canonical.com/ubuntu/dists/gutsy/Release:](http://archive.canonical.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  commercial/binary-amd64/Packages in Meta-index file (malformed Release file?)

---

### Post by Rocket2DMn on 2008-01-25
Can you please post the contents of your sources.list file?
```
cat /etc/apt/sources.list
``` and the exact output of
```
sudo apt-get update
```

Just copy and paste from the terminal

---

### Post by Tek-Noir on 2008-01-25
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Alpha amd64 (20070809)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'commercial' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy commercial
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy commercial

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse





Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Alpha amd64 (20070809) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Alpha amd64 (20070809) gutsy/restricted Translation-en_GB
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB     
Get: 2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/commercial Translation-en_GB            
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release.gpg [191B]                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Translation-en_GB                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Translation-en_GB            
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release.gpg [191B]           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Translation-en_GB      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Packages
Get: 5 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_GB
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_GB
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Fetched 5B in 1s (4B/s)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/Release](http://archive.canonical.com/ubuntu/dists/gutsy/Release)  Unable to find expected entry  commercial/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Rocket2DMn on 2008-01-25
You shouldn't be using repositories from other versions of Ubuntu.  If you are using Gutsy, disable the Feisty sources.  Also, it looks like the Commercial repo is not working - it is either down or not set correctly in sources.list.
You shouldn't need the commercial repo anyway, let's just disable it along with the medibuntu repo.
```
gksudo gedit /etc/apt/sources.list
```
> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Alpha amd64 (20070809)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'commercial' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# let's comment out the commerical repos
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy commercial
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy commercial

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

Then run
```
sudo apt-get update
```

It seems to me something is not right with medibuntu, because I get errors, too.

---

### Post by Tek-Noir on 2008-01-25
Seems to have sorted things, sorry im a bit new to all this lol

Thanks again for all the help :)

---

### Post by wittelw on 2008-02-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/156778](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/156778) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: [urlhttps://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/154094[/url] [br].[/br] ---------------------------- [br].[/br] [br].[/br]

				I ran into the same thing trying to upgrade to an Alpha of hardy heron using the following:

```
sudo update-manager -d
```

Upgrade would error out and restore to gutsy 7.10 with following error:

[http://archive.canonical.com/ubuntu/dists/gutsy/Release:](http://archive.canonical.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  commercial/binary-amd64/Packages in Meta-index file (malformed Release file?)

I solved it by commenting out two commercial lines in my /etc/apt/sources.list:

```
< deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy commercial
< deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy commercial
---
> # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy commercial
> # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy commercial
```

After doing this I am now trickling down 8.04 upgrade bits and expect to have it running in an hours or so (live CD looked fine on my system).

Thanks to all for the hints.

---

