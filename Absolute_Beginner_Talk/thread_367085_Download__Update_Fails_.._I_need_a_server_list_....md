---
title: "Download / Update Fails .. I need a server list ..."
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by almasry on 2007-02-21
Hi guys
my new Ubuntu (v 6.10) don't download any file or update  completely .. it fails in downloading some files .. and so the setup or the update  stops or generates some errors ..

a friend of mine ,told me that I should add or update the servers list .. but he didn't give me anew list to download ..

if some one pointed me to a servers' list , i would be thankful ..

thanks in advance

---

### Post by linux_kid on 2007-02-21
In synaptic, go to settings->reposotories

Select the servers you wish.

---

### Post by aktiwers on 2007-02-21
Or use mine:
```
sudo gedit [SIZE=-1]/etc/apt/sources.list
```

And replace it all with this:

[/SIZE]> 
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy main restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy-updates main restricted #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
#AUTOMATIX REPOS END

# Treviño's Ubuntu edgy Beryl-SVN Repository (GPG key: 81836EBF - DD800CD9)
# Daily Updated Beryl (and related projects) Packages...
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

# Ubuntu edgy
deb [http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) edgy main restricted universe multiverse
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) edgy main restricted universe multiverse

# Ubuntu edgy updates
deb [http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) edgy-updates main restricted universe multiverse

# Ubuntu edgy backports
# deb [http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) edgy-backports main restricted universe multiverse

# Ubuntu edgy security fixes
deb [http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) edgy-security main restricted universe multiverse
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) edgy-security main restricted universe multiverse

deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

## E17 repository "edevelop.org"
deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17
deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17

deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) stable contrib

And then close and save.

At last do this in Terminal:
```
sudo apt-get update
```

---

### Post by OnyxOD on 2007-02-23
> **aktiwers said:**
> Or use mine:
```
sudo gedit [SIZE=-1]/etc/apt/sources.list
```

And replace it all with this:

[/SIZE]

And then close and save.

At last do this in Terminal:
```
sudo apt-get update
```

Hi, I added "deb [http://apt.tt-solutions.com/ubuntu/](http://apt.tt-solutions.com/ubuntu/) dapper main" to the repository list at /etc/apt/sources.list When I run apt-get update it says that there isnot a publick key is not available.   So I looked back at the wxwidgets site and it ask me to run this command in the terminal curl "http://www.tt-solutions.com/vz/key.asc | apt-key add -" it says Curl command not found.. So how do I add the right public key? any help is much appreciated Thanks!!! btw I love ubuntu, and searching the forums for most of my problems has helped out alot thanks to all the members that make help support possible!:guitar:

---

### Post by T3h_Dohtem on 2007-02-23
i believe in ubuntu: curl == wget

try:

wget [http://www.tt-solutions.com/vz/key.asc](http://www.tt-solutions.com/vz/key.asc) | apt-key add -


For the original poster, i dont know that i would go about adding repositories to fix all of your problems, especially not all of the outside repos that aktiwers posted. As a new user you're best off adding and removing repos in synaptic:

Sytem Menu>Administrative>Synaptic Package Manager

Then when you have synaptic open:

Settings Menu>Repositories

the main thing that will help you is just doing (in a terminal):

sudo apt-get update

Or in Synaptic click Reload, or Refresh (I don't remember which it is labeled)

If that doesn't work, i'd keep looking, and be more descriptive, "it generates some errors" doesnt tell us very much about the problem you're having.

---

### Post by OnyxOD on 2007-02-23
Hi thanks for the help, I ran that code and it went ok, but still the same problem after running sudo apt-get update as followed:

W: GPG error: [http://apt.tt-solutions.com](http://apt.tt-solutions.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 06EA41DE4F6C1E86

I am assuming it didn't work :confused: thanks.

---

### Post by almasry on 2007-02-24
ooooof .... my previous list was better than this expired one :

have  a look : 

> Ign [ftp://ubuntu.uni-klu.ac.at](ftp://ubuntu.uni-klu.ac.at) edgy-updates/restricted Packages                                                              
Get:88 [ftp://ubuntu.uni-klu.ac.at](ftp://ubuntu.uni-klu.ac.at) edgy-updates/universe Packages                                                             
Ign [ftp://ubuntu.uni-klu.ac.at](ftp://ubuntu.uni-klu.ac.at) edgy-updates/universe Packages                                                                
Get:89 [ftp://ubuntu.uni-klu.ac.at](ftp://ubuntu.uni-klu.ac.at) edgy-updates/multiverse Packages                                                           
Ign [ftp://ubuntu.uni-klu.ac.at](ftp://ubuntu.uni-klu.ac.at) edgy-updates/multiverse Packages                                                              
Get:90 [ftp://ubuntu.uni-klu.ac.at](ftp://ubuntu.uni-klu.ac.at) edgy-updates/main Sources                                                                  
Ign [ftp://ubuntu.uni-klu.ac.at](ftp://ubuntu.uni-klu.ac.at) edgy-updates/main Sources                                                                     
Get:91 [ftp://ubuntu.uni-klu.ac.at](ftp://ubuntu.uni-klu.ac.at) edgy-updates/restricted Sources                                                            
Ign [ftp://ubuntu.uni-klu.ac.at](ftp://ubuntu.uni-klu.ac.at) edgy-updates/restricted Sources                                                               
Get:92 [ftp://ubuntu.uni-klu.ac.at](ftp://ubuntu.uni-klu.ac.at) edgy-updates/universe Sources                                                              
Ign [ftp://ubuntu.uni-klu.ac.at](ftp://ubuntu.uni-klu.ac.at) edgy-updates/universe Sources                                                                 
Get:93 [ftp://ubuntu.uni-klu.ac.at](ftp://ubuntu.uni-klu.ac.at) edgy-updates/multiverse Sources                                                            
Ign [ftp://ubuntu.uni-klu.ac.at](ftp://ubuntu.uni-klu.ac.at) edgy-updates/multiverse Sources                                                               
Get:94 [ftp://ubuntu.uni-klu.ac.at](ftp://ubuntu.uni-klu.ac.at) edgy-security/main Packages                                                                
Ign [ftp://ubuntu.uni-klu.ac.at](ftp://ubuntu.uni-klu.ac.at) edgy-security/main Packages                                                                   
Get:95 [ftp://ubuntu.uni-klu.ac.at](ftp://ubuntu.uni-klu.ac.at) edgy-security/restricted Packages     




guys ..!!!  any expert user have a good list to share it , plz .. I am confused

---

### Post by aktiwers on 2007-02-25
Sorry, didnt know my filelist would cost you any problems. Works great here.
Why dont you just take the one on your LiveCD and copy paste it?

Then you are back on the default.

---

