---
title: "what's with all the Software Properties?"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-08-08
In System --> Administration --> Software Properties, is there some kind of guide I can read for how to figure out what all that is? There are such slight differences between them and some even look the same to me. Also, how do you edit this list? Do you check the boxes next to the item, or click the Add button?

I read somewhere on here that to enable the universe and multiverse repositories I needed to first click on Ubuntu 6.06 LTS (binary) and then click Add, then click the check boxes next to Universe and Multiverse. But each entry in the list seems to have this choice, so why did I need to choose a particular one? Also, I went back to that one I chose, and Universe and Multiverse aren't checked anymore, yet they are still enabled. But at the same time, there are some entries in the list that contain 'universe' and 'multiverse' and they are not checked.

I hope that makes some sense. It's confusing to me because it all looks the same, and I don't see any order or reason for checking any particular box over another.

---

### Post by catlett on 2006-08-08
It's easier when you just l;ook at the file. That is ubuntu's attempt to make the repository file more "window users" friendly. It's gui but it is confusing,
That is the repository list. When you use apt-get or synaptic package manager, those are the servers that you access. The file is in /etc under /apt and it is labeled sources.list. This is the official way to add a repo [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) But if you want an easy way,  opon the file with this command.
```
sudo gedit /etc/apt/sources.list
```
Just delete what you have and enter this list. It is the dapper guides list.
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free
```Make sure to sae the file and then run sudo apt-get update

---

### Post by JohnJSal on 2006-08-08
Well, your cleaned up version makes it a lot easier to see the differences, but my file doesn't look like that. It still confuses me:


deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

# wxPython repository on Starship
deb [http://starship.python.net/crew/robind/wxPython/apt/](http://starship.python.net/crew/robind/wxPython/apt/) binary/
deb-src [http://starship.python.net/crew/robind/wxPython/apt/](http://starship.python.net/crew/robind/wxPython/apt/) source/

I don't seem to have the two main lines at the top like you do, nor is mine as nicely organized into sections as yours. Did you rewrite that yourself?

I guess one thing that confuses me is the presence or absence of the words universe and multiverse. I assume you can add those yourself, and maybe that's what you did. But I followed the instructions in the link you gave and used the GUI to enable universe and multiverse, yet not all of my links have those words, so I'm just trying to wrap my mind around all the different links and what they refer to, and which are enabled for universe/multiverse and which aren't, etc.

Edit: a slightly more thorough comparison seems to show that I have the same links as you, but mine are split up on different lines at times (some might have main restricted together, then another line with universe multiverse). However, I don't have the plf links.

---

### Post by catlett on 2006-08-08
My list comes form the Dapper Guide [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide) in their "add extra repositories" section [http://doc.gwos.org/index.php/DapperGuide#How_to_add_extra_repositories](http://doc.gwos.org/index.php/DapperGuide#How_to_add_extra_repositories)

The words universe and multiverse etc have to do with open software. I do not remeber it exactly but the regular repos are all open dource the others have some that are not and others have propriety.
Also some have packages that are illegal in the us to instal because of copy right law. Mainly the mp3 codecs and the dvd codecs.
Anyways the packages are all on the same server. If you hit the links in the posted lists, you can go to the server and see ho9w it is divided up.

The dapper guide is a great guide for appps but you will also need the win32codecs and mpg321 from the restricted formats wiki [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by JohnJSal on 2006-08-09
Great link. I'm going to be reading up on all that!

---

