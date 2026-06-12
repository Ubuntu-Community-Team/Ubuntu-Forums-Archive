---
title: "Add all the repositories in the world - All Free Software not just ubuntu"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by dolecannery on 2007-12-03
I would like to add all the repositories in the world to my synaptic package manager.  How do I do this?  Why is this not the default.  I do not just want the Ubuntu official and other repository.  I want everything as in Free and Open.  For example after quite a bit of searching I found the media repository for google earth and directions on how to add it  to synaptic.  I do not want to search the web for repository after repository and just luck into one or another, I would like to add the world list of them right of the starting line.  When I look for things like google earth I just want to go to synaptic, search and apply.  If this is a risk to ubuntu installation it is immaterial, without the choice to add the widest selection of software, Ubuntu's value is extremely diminished.

---

### Post by LowSky on 2007-12-03
How is ubuntu's value really diminished -- it's free...lol

It's like getting a free sandwich for lunch and complaining it has mustard on it.

you got to remember that some "free" software isn't really open source, and that some one owns the rights of its use. this is why ubuntu can not  play mp3's and DVD's with a standard installation.

besides Microsoft and Apple dont have anything like synaptic or play mp3 or dvd out of the box, and you pay real money for those products

---

### Post by mellowd on 2007-12-03
It's not added by default because it would need to be tested first. You have the option of adding a repository but its not there by default because then new people will go install a whole bunch of untested crap, and complain it isn't stable enough.

You have the free choice to add whatever you want though

---

### Post by markyb86 on 2007-12-03
You dont want ALL the repos in the world because alot of LINUX software isnt for ubuntu...

---

### Post by dolecannery on 2007-12-03
after study and trying for hours and hours nothing is installed, improved or changed for the better.  Working hard to accomplish nothing for non linux users is considered an opportunity cost not to mention frustrating.  Thanks for taking the time to read, please do not waste your time replying (unless you have something useful to say).

---

### Post by dolecannery on 2007-12-03
Thank you for replying.  How do I add them? Where are the details of these repositories, and instructions for adding them listed?

---

### Post by dolecannery on 2007-12-03
What are the universe off all linux programs that will work in ubuntu (not approved by ubuntu but linux to run in linux), why are not all linux repostories for ubuntu, which non ubuntu ones are usable in ubuntu, and what other distributions are the other programs good for, how would one know?  I want to be able to add as much as possible not whatever someone else can think of for me.

---

### Post by Tomosaur on 2007-12-03
You will have to go around every debian-based distribution, find the web links to their repositories, then add them through the Synaptic package manager or by modifying your /etc/apt/sources.list file, using this command:

```

sudo nano /etc/apt/sources.list

```

Adding every single repository in the world is a very, very bad idea, however. Most of the repositories will contain identical software anyway, and it will simply cause you huge confusion and frustration. That, and it will take ages to update the list of available packages, could cause conflicts when updating or adding new software, and will mean that your system will try to update using software from multiple repositories.

Generally speaking, it's just a bad idea, but I'm quite interested to know what will happen. It's going to take a long time for you to find the repositories and add them, though.



OR, do you mean, you just want to ENABLE the repositories which are already included but disabled by default? If this is what you want to do, it's very easy to do in the Synaptic package manager.

---

### Post by LowSky on 2007-12-03
LOOK WHAT I FOUND BY USING GOOGLE SEARCH! 

some unofficial ( possibly unstable) repos
[http://blog.kovyrin.net/2006/03/27/unofficial-debian-reposotories-overview/](http://blog.kovyrin.net/2006/03/27/unofficial-debian-reposotories-overview/)

how to add them

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

YOURE WELCOME

---

### Post by dolecannery on 2007-12-03
As an example of what I mean, I found that Google Earth was on a media repository that was not provided by Ubuntu (either enabled or disabled by default).  I consider Google Earth a  basic tool.  I would like to have many of these types of programs available to me without jumping through hurdles to find and install them.  It seems that if I searched for Synaptic for these basic sort of utilities, could find them and then apply them it would make Ubuntu far more useful to me.

---

### Post by mellowd on 2007-12-03
> **dolecannery said:**
> As an example of what I mean, I found that Google Earth was on a media repository that was not provided by Ubuntu (either enabled or disabled by default).  I consider Google Earth a  basic tool.  I would like to have many of these types of programs available to me without jumping through hurdles to find and install them.  It seems that if I searched for Synaptic for these basic sort of utilities, could find them and then apply them it would make Ubuntu far more useful to me.

I don't find it essential, everyone will have a different Idea. In windows if you want something you need to find it. What's so difficult about finding and installing it?

---

### Post by dolecannery on 2007-12-03
Thank you LowSky for the useful information.

---

### Post by ruibernardo on 2007-12-03
Usually, to add a repository, you must had the GPG key of the repository to apt: Example for medibuntu: 

```
**wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - **&& sudo apt-get update
```To add the sources.list of medibuntu:```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```Without the GPG key, APT will give you an error and will not trust in the repository that is on the sources.list.

---

### Post by dolecannery on 2007-12-03
Once outside of Synaptic, adding software requires a thorugh knowledge of line commands, parameters, permissions, directory manipulation, decompresion techniques - what kind of file uses what kind of decompress and which parameters, etc, etc..  If one does not know how to do that, which anyone who has not used Linux extensively does not then in nearly every instance installing non synaptic software takes days if not weeks rather than moments.  My sense is that everyone else who is trying to get away  from windows by using Ubuntu has the same issue unless they are content to use the computer as a word processor, spreadsheet, email, web browser only.  Those things work great, then I am dead in the water doing anything that is interesting or important to me.

---

### Post by daimaru on 2007-12-03
> **dolecannery said:**
> I just want to go to synaptic, search and apply....without the choice to add the widest selection of software, Ubuntu's value is extremely diminished.
I can't recall ever going to "add & remove software" in windows and selecting google earth and thereby installing it. :) so why is ubuntu diminished if you have to do the same thing (most of the time easier) as you would have to do under windows. i mean you had to go to earth.google.com and download google earth for windows didn't you? there was no Global Bill Gates Microsoft Supporting Free Software Synaptic Package Manager that provided you every software you wanted now  was there?

EDIT: all you would have to do is type googleearth into firefox addressbar, click on downloads click  on agree to download and save the "GoogleEarthLinux.bin" to your hard drive. double click it and thats it... so if you can't do that how did you ever manage to execute a .exe file under windows?

---

### Post by Sarteck on 2007-12-03
It might be the Windows User in me, but I see what dolecannery is saying, and I somewhat agree.  I tend to take the middle ground, though--I think it would be foolish to have so many repos enabled by default (or even just commented out in the list).  But I think it would be cool if there was some standardized utility that automagically added a repo and installed your program for you (with your explicit permission, of course).  Kind of like your basic Windows INSTALL.EXE, except that would update when you updated the rest of your programs...

I don't know, am I making any sense?

---

### Post by ruibernardo on 2007-12-03
> **dolecannery said:**
> Once outside of Synaptic, adding software requires a thorugh knowledge of line commands, parameters, permissions, directory manipulation, decompresion techniques - what kind of file uses what kind of decompress and which parameters, etc, etc..  If one does not know how to do that, which anyone who has not used Linux extensively does not then in nearly every instance installing non synaptic software takes days if not weeks rather than moments.  My sense is that everyone else who is trying to get away  from windows by using Ubuntu has the same issue unless they are content to use the computer as a word processor, spreadsheet, email, web browser only.  Those things work great, then I am dead in the water doing anything that is interesting or important to me.

I think I understand what you mean. It is a bit strange to the Windows users. It is really a question of getting used too.

APT/dpkg system, if you are using repositories to install software, is not that complicated. You have files (packages), dependencies (apt resolves them) and repositories (you have to add the GPG key and update apt so it knows which ones are enabled). So, after adding a repository, it's just an issue of using apt-get/Synaptic/whatever.

The package manager system can install, remove, purge (remove configuration files), reinstall, etc. It is much more simpler, complete and secure (depending on the repos you are using) than using a magazine CD or an exe installer from some internet website in windows.

About installing binaries (.bin and .sh files) usually you just make them executable and run them.

A little more complicated is compiling from source. The basic steps are:
```
./configure
make 
sudo make install
```In the process you get some errors if you don't have the required sources the programs asks, but googling the make errors will give you answers even if you don't have a list of the compilation requirements.


I prefer any one of this cases than installing an .exe file from an obscure website the internet in windows. Linux and opensource are much more secure and more clear.

---

