---
title: "[SOLVED] Everything Has Been Deleted - Help!"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by ShadowMKII on 2007-11-01
Well, trying to install Skype on Gutsy has been a nightmare for me. I went to all of these online tutorials - even the Ubuntu community ones - and I did not get a straight enough answer to help me install Skype. I have the Skype icon in my Internet main menu, but the program does not work, and that is after what happened. I was so worked up with trying to get Skype working that I had to add a third-party repository from one of those "easy Skype install" sites for Ubuntu Gutsy. Since the repository was not working for me like it was for the guy on the video on his website (with the easy instructions, to boot), I deleted all of the existing third-party software sources that I had except for his in hopes that it would work. Foolish, obviously, because it did not work. I restarted my computer thinking that all of the attempts and changes and library installations may have not let Ubuntu have the chance to refresh itself and remove the Skype icon from the Internet main menu. Unfortunately for me, I removed my desktop settings. Could some one please help me get out of this mess, and, perhaps, HELP ME INSTALL SKYPE like all of the other normal people were able to in their ridiculously straightforward tutorials and videos!!?!

Some screen shots for assistance:

This is what happened after my Glossy/Human settings were terminated: [[img=http://img522.imageshack.us/img522/5703/screenshotzm7.th.png]](http://img522.imageshack.us/my.php?image=screenshotzm7.png)

These are some tutorials I TRIED to follow, but did not work out well for me. Even with a month's experience, I remain an utter Ubntn00b: [[img=http://img152.imageshack.us/img152/7070/screenshot1tf2.th.png]](http://img152.imageshack.us/my.php?image=screenshot1tf2.png)
[[img=http://img152.imageshack.us/img152/2804/screenshot2wf1.th.png]](http://img152.imageshack.us/my.php?image=screenshot2wf1.png)

Could someone point me in the right direction or take me to a solved thread about Skype and Gutsy, please? I do not know what I have been doing wrong!

---

### Post by Maestro23 on 2007-11-01
Running 64-bit Gutsy.  Read your post and decided to try and install skype myself.

1. Added the Medibuntu repositories: [https://help.ubuntu.com/community/Medibuntu?highlight=%28Medibuntu%29](https://help.ubuntu.com/community/Medibuntu?highlight=%28Medibuntu%29)

2. Install Skype 1.4 (same as the .deb at the site):** sudo apt-get install skype**

3. Installed with no problems and there's a menu item under** Apps>>Internet**

*When you tried to install from the repos before, what kind of errors where you getting to send you half-way around the world for "easy" tutorials?

---

### Post by ShadowMKII on 2007-11-02
You really went out of your way to help me with all of this! Well, when I was trying to get everything working from all of these easier sites, I usually recieved a message roughly translating into "couldn't find package" or "such-and-such does not exist" or "so-and-so is not a valid directory/file name." I had Skype on the Applications->Internet submenu, but it still did not work when I was receiveing these errors. 

I just tried to install the repositories that you installed, but I got another error message. I am, obviously, not getting something that has been preventing me from doing a lot of things on terminal. I prefer terminal instead of Synaptic, but some things have to be done. Anyhow, I will give you some code so you can get an indication of what I am doing wrong.

Here you go:```
jordi@Shadow-Slate:~$ sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for jordi:
--21:19:44--  http://www.medibuntu.org/sources.list.d/gutsy.list
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving www.medibuntu.org... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 223 [text/plain]

100%[====================================>] 223           --.--K/s             

21:19:45 (16.67 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [223/223]

jordi@Shadow-Slate:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package skype
jordi@Shadow-Slate:~$ 

```

That seems to be my ticket. How did you go about doing it yourself? Also, I think I forgot to mention, was that I could not find Skype on the Add/Remove Programs option on the Applications menu. I wanted to try and get rid of all of the unnecessary files that I downloaded and start freshly, but I was unable to find it! Thank you for going through all of the trouble by the way.

Also, just for a "heads up," my desktop decided to restore itself. Do not ask how, as it just did it on its own after I booted up from reading that horrific error message!

---

### Post by Maestro23 on 2007-11-02
Hmm... Can you post your **/etc/apt/sources.list**

In terminal:

> cat /etc/apt/sources.list

---

### Post by ShadowMKII on 2007-11-02
```
jordi@Shadow-Slate:~$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse restricted universe main
deb-src http://archive.ubuntu.com/ubuntu/ gutsy multiverse restricted universe main #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse restricted universe main
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse restricted universe main #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse restricted universe main
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse restricted universe main #Added by software-properties

jordi@Shadow-Slate:~
```

---

### Post by Partyboi2 on 2007-11-02
What does 
```
apt-cache search skype
``` say?

---

### Post by Maestro23 on 2007-11-02
Looks like you don't have all your sources.  Did you upgrade to Gutsy?  

Here's mine.  you can copy/paste mine over yours and save it.  You can also generate a new default list with the following link: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Here's mine:

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

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

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse

*After you get your sources.list straight, do:

> sudo apt-get update

sudo apt-get upgrade

---

### Post by ShadowMKII on 2007-11-02
This says absolutely nothing! ```
apt-cache search skype
```

I was originally a Feisty user from the 26th of September, but I upgraded just over a week ago to Gutsy. I had problems upgrading because of some strange gtkpod repository or something. If you want to know exactly what it was, search for some of my threads that I have posted here. I would tell you, but I cannot remember right now!

As for copying and pasting, do you mean I should copy and paste it into terminal and it will run by itself?

---

### Post by Partyboi2 on 2007-11-02
In a terminal type:
```
 sudo gedit /etc/apt/sources.list
```then delete the contents of that file and copy and paste the new one then save.
then:
```
 sudo apt-get update
```then:
```
 sudo apt-get upgrade
```

---

### Post by Maestro23 on 2007-11-02
> **ShadowMKII said:**
> This says absolutely nothing! ```
apt-cache search skype
```

I was originally a Feisty user from the 26th of September, but I upgraded just over a week ago to Gutsy. I had problems upgrading because of some strange gtkpod repository or something. If you want to know exactly what it was, search for some of my threads that I have posted here. I would tell you, but I cannot remember right now!

As for copying and pasting, do you mean I should copy and paste it into terminal and it will run by itself?

No.  Make a backup of your sources.list file first. Someting like:

> sudo cp /etc/apt/sources.list /etc/sources.list11012007

Then open up the original with an editor (geidt, nano, etc...) and delete all the contents.  .Copy/Paste my list into the empty file and save.

Then run the apt-get commands I posted.

To edit the file with gedit:

> gksudo gedit /etc/apt/sources.list

Hope that makes sense to you. :)

---

### Post by ShadowMKII on 2007-11-04
```
jordi@Shadow-Slate:~$ sudo cp /etc/apt/sources.list /etc/sources.list04112007
[sudo] password for jordi:
jordi@Shadow-Slate:~$ gksudo /etc/apt/sources.list
jordi@Shadow-Slate:~$ 

```

Well, that is what I got from what you told me. I was not sure if I should go any further seeing as how there was no editing window that popped up or anything.

As for the other version, this is what I got:

```
jordi@Shadow-Slate:~$ sudo gedit /etc/apt/sources.list
jordi@Shadow-Slate:~$ sudo apt-get update
Get:1 http://packages.medibuntu.org gutsy Release.gpg [189B]                   
Ign http://packages.medibuntu.org gutsy/free Translation-en_CA                 
Get:2 http://us.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_CA
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_CA
Hit http://packages.medibuntu.org gutsy Release
Err http://packages.medibuntu.org gutsy Release
  
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_CA
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_CA
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_CA
Get:3 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_CA
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_CA
Get:4 http://packages.medibuntu.org gutsy Release [2723B]
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_CA
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_CA
Get:5 http://us.archive.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-security/main Translation-en_CA
Ign http://us.archive.ubuntu.com gutsy-security/restricted Translation-en_CA
Ign http://us.archive.ubuntu.com gutsy-security/universe Translation-en_CA
Ign http://us.archive.ubuntu.com gutsy-security/multiverse Translation-en_CA
Get:6 http://us.archive.ubuntu.com gutsy Release [65.9kB]
Get:7 http://us.archive.ubuntu.com gutsy-updates Release [51.2kB]
Get:8 http://us.archive.ubuntu.com gutsy-security Release [51.2kB]             
Get:9 http://us.archive.ubuntu.com gutsy/main Packages [1070kB]                
Ign http://packages.medibuntu.org gutsy Release                
Ign http://packages.medibuntu.org gutsy/free Packages   
Ign http://packages.medibuntu.org gutsy/non-free Packages
Hit http://packages.medibuntu.org gutsy/free Packages
Hit http://packages.medibuntu.org gutsy/non-free Packages
Get:10 http://us.archive.ubuntu.com gutsy/restricted Packages [6769B]
Get:11 http://us.archive.ubuntu.com gutsy/main Sources [306kB]                 
Get:12 http://us.archive.ubuntu.com gutsy/restricted Sources [2120B]           
Get:13 http://us.archive.ubuntu.com gutsy/universe Packages [4007kB]           
Get:14 http://us.archive.ubuntu.com gutsy/universe Sources [1226kB]            
Get:15 http://us.archive.ubuntu.com gutsy/multiverse Packages [152kB]          
Get:16 http://us.archive.ubuntu.com gutsy/multiverse Sources [56.8kB]          
Get:17 http://us.archive.ubuntu.com gutsy-updates/main Packages [13.2kB]       
Get:18 http://us.archive.ubuntu.com gutsy-updates/restricted Packages [14B]    
Get:19 http://us.archive.ubuntu.com gutsy-updates/main Sources [4127B]         
Get:20 http://us.archive.ubuntu.com gutsy-updates/restricted Sources [14B]     
Get:21 http://us.archive.ubuntu.com gutsy-updates/universe Packages [8800B]    
Get:22 http://us.archive.ubuntu.com gutsy-updates/universe Sources [2068B]     
Get:23 http://us.archive.ubuntu.com gutsy-updates/multiverse Packages [599B]   
Get:24 http://us.archive.ubuntu.com gutsy-updates/multiverse Sources [14B]     
Get:25 http://us.archive.ubuntu.com gutsy-security/main Packages [9254B]       
Get:26 http://us.archive.ubuntu.com gutsy-security/restricted Packages [14B]   
Get:27 http://us.archive.ubuntu.com gutsy-security/main Sources [2773B]        
Get:28 http://us.archive.ubuntu.com gutsy-security/restricted Sources [14B]    
Get:29 http://us.archive.ubuntu.com gutsy-security/universe Packages [7348B]   
Get:30 http://us.archive.ubuntu.com gutsy-security/universe Sources [1539B]    
Get:31 http://us.archive.ubuntu.com gutsy-security/multiverse Packages [599B]  
Get:32 http://us.archive.ubuntu.com gutsy-security/multiverse Sources [14B]    
Fetched 7049kB in 28s (251kB/s)                                                
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
jordi@Shadow-Slate:~$ 

```

When I ran sudo apt-get upgrade after that, I was told that nothing was upgraded or changed. I ran apt-get update again just in case (due to the terminal message above), but found that there were no changes, obviously. From here, where do I go now? (By the way, I backed up my files as well.)

---

### Post by ShadowMKII on 2007-11-04
Also, I just got this message, which is entirely related.

[[img=http://img225.imageshack.us/img225/2425/screenshotgh4.th.png]](http://img225.imageshack.us/my.php?image=screenshotgh4.png)

I hope this helps!

---

### Post by avik on 2007-11-04
Try this in the terminal:

```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

---

### Post by oldos2er on 2007-11-04
The command "gksudo  /etc/apt/sources.list" should be "gksudo gedit /etc/apt/sources.list"

---

### Post by ShadowMKII on 2007-11-04
Well, here is how far I have gotten. 

```
jordi@Shadow-Slate:~$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
[sudo] password for jordi:
OK
Get:1 http://packages.medibuntu.org gutsy Release.gpg [189B]
Ign http://packages.medibuntu.org gutsy/free Translation-en_CA                 
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_CA
Hit http://packages.medibuntu.org gutsy Release         
Get:2 http://us.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_CA
Ign http://packages.medibuntu.org gutsy/free Packages
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_CA
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_CA
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_CA
Get:3 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_CA
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_CA
Ign http://packages.medibuntu.org gutsy/non-free Packages
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_CA
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_CA
Get:4 http://us.archive.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-security/main Translation-en_CA
Ign http://us.archive.ubuntu.com gutsy-security/restricted Translation-en_CA
Ign http://us.archive.ubuntu.com gutsy-security/universe Translation-en_CA
Ign http://us.archive.ubuntu.com gutsy-security/multiverse Translation-en_CA
Hit http://us.archive.ubuntu.com gutsy Release 
Hit http://us.archive.ubuntu.com gutsy-updates Release
Hit http://packages.medibuntu.org gutsy/free Packages               
Hit http://us.archive.ubuntu.com gutsy-security Release             
Hit http://packages.medibuntu.org gutsy/non-free Packages
Hit http://us.archive.ubuntu.com gutsy/main Packages
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-security/main Packages
Hit http://us.archive.ubuntu.com gutsy-security/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-security/main Sources
Hit http://us.archive.ubuntu.com gutsy-security/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-security/universe Packages
Hit http://us.archive.ubuntu.com gutsy-security/universe Sources
Hit http://us.archive.ubuntu.com gutsy-security/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-security/multiverse Sources
Fetched 192B in 2s (77B/s)
Reading package lists... Done
jordi@Shadow-Slate:~$ sudo apt-get skype
E: Invalid operation skype
jordi@Shadow-Slate:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting skype-static instead of skype
The following extra packages will be installed:
  dbus-x11 skype-common skype-static
The following NEW packages will be installed:
  dbus-x11 skype-common skype-static
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 19.7MB of archives.
After unpacking, 22.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com gutsy/main dbus-x11 1.1.1-3ubuntu4 [34.8kB]
Get:2 http://packages.medibuntu.org gutsy/non-free skype-common 1.4.0.118dynamic+static-0medibuntu3 [1603kB]
Get:3 http://packages.medibuntu.org gutsy/non-free skype-static 1.4.0.118dynamic+static-0medibuntu3 [18.0MB]
Fetched 19.7MB in 11m41s (28.0kB/s)                                            
Selecting previously deselected package dbus-x11.
(Reading database ... 110370 files and directories currently installed.)
Unpacking dbus-x11 (from .../dbus-x11_1.1.1-3ubuntu4_amd64.deb) ...
Selecting previously deselected package skype-common.
dpkg: regarding .../skype-common_1.4.0.118dynamic+static-0medibuntu3_all.deb containing skype-common:
 skype-common conflicts with skype (<< 1.4.0.118dynamic+static-0medibuntu1)
  skype (version 1.4.0.118-1) is present and installed.
dpkg: error processing /var/cache/apt/archives/skype-common_1.4.0.118dynamic+static-0medibuntu3_all.deb (--unpack):
 conflicting packages - not installing skype-common
Selecting previously deselected package skype-static.
dpkg: considering removing skype in favour of skype-static ...
dpkg: yes, will remove skype in favour of skype-static.
Unpacking skype-static (from .../skype-static_1.4.0.118dynamic+static-0medibuntu3_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/skype-common_1.4.0.118dynamic+static-0medibuntu3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jordi@Shadow-Slate:~$ 

```

I encountered an error after I finished downloading and terminal began unpacking. Do you know what the problem is?

---

### Post by ShadowMKII on 2007-11-04
Never mind! I somehow got it working! ^-^ Thank you everyone for all of your help with this - you have made me one very happy Ubuntu user!

[SOLUTION] - After doing what I did, I was told to update from the little orange box that appears, by default, near the On/Off button on the upper right hand corner of the screen. I clicked it and there appeared to be an error. I was told how to solve it in terminal; I did so, and everything worked from there!

---

### Post by Maestro23 on 2007-11-04
> **ShadowMKII said:**
> Never mind! I somehow got it working! ^-^ Thank you everyone for all of your help with this - you have made me one very happy Ubuntu user!

Glad you finally got it man.  Don't forget to mark this SOLVED using the Thread Tools.

Congrats again man.:guitar:

---

