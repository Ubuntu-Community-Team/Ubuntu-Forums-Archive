---
title: "vlc in xubuntu"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by nexttry on 2008-02-22
I want to install vlc in my xubuntu but i have no idea on how to install programs oir is it called apps?

I succesfully manage to install adobe flash and pdf reader, but have failed in every other installation.

so I would like someone to help me and guide my way trhough this installation, or point at articles or things to read.

I am also new to the terminology and of course everything else that has to do with linux

its 7,10 on an i386

please help
thank ypou

---

### Post by PmDematagoda on 2008-02-22
You should be able to install VLC(provided you have the required repositories) simply using:-
```
sudo apt-get install vlc
```

---

### Post by taurus on 2008-02-22
Make sure you have enable all the repos in /etc/apt/sources.list before you attend to install anything extra for your machine.

---

### Post by nexttry on 2008-02-22
result:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vlc

I dont understand, so I need alot of more things installed before installing?

---

### Post by PmDematagoda on 2008-02-22
Post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by nexttry on 2008-02-22
deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by nexttry on 2008-02-22
was that right?

---

### Post by OffAxis on 2008-02-22
> so I need alot of more things installed before installing? 
No, it just needs to look in the right place.
see those lines marked #deb ?
delete the pound sign (#) in front of the deb

so 
**#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe**

would become 
**deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe**

only delete the # in front of the word deb and deb-src (not the descriptions)

so 
```
sudo nano /etc/apt/sources.list
```

delete the pound signs, save (control-X then Y then Enter to save it as the same name) and

```
sudo apt-get update
sudo apt-get install vlc

```

---

### Post by fddlstx on 2008-02-22
And easy way to do this, if you're not very comfortable with terminal, is to go to:
Applications>System>Software Sources, and check all of the boxes in the 'third-party software' and 'ubuntu' tab. Then go to Applications>System>Synaptic package manager, do a search for vlc, and install it. If you simply mark the package named 'vlc' and nothing else, when you hit apply it will select all the other necessary packages for you.
Once the installation is done, you should see vlc in your Applications>Multimedia folder.

---

### Post by nexttry on 2008-02-22
okay i think its installing now, thanks all

but what did I do? i simply opened up the computer for the whole world or what?

does anyone know any good guide for installing programs using those tar.gz files or whats they are called?? ive tried to find but failed.

yes it worked again thanks

---

### Post by FuturePilot on 2008-02-22
Here's a good overview of installing stuff, even some basic instructions on installing from source.
[http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by nexttry on 2008-02-22
thanks

but after deleted all # signs isnt my computer more attractive for attacks, or maybe there arent any linux hackers? also

could i have deleted those pound signs from the text file?


i tried the same command for getting compiz but i save that for another thread

---

### Post by taurus on 2008-02-22
Enabling more repos by removing the # in front of all the deb & deb-src in /etc/apt/sources.list has nothing to do with whether your machine is open for attack or not.  And if you don't want to enable those repos, then you can't install anything with synaptic, Add/Remove, or apt-get/aptitude.  You just have to install more stuff by hand, hunting down the .deb and all the dependencies then.

---

### Post by nexttry on 2008-02-22
hey im anoob you know. I think its great installing like that.

anyway vlc works fine thanks again

---

