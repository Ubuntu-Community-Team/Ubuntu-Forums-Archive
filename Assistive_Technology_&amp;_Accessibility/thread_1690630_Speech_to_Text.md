---
title: "Speech to Text"
date: 2011-02-18
forum: Assistive Technology &amp; Accessibility
---

### Post by COMPUTIAC on 2011-02-18
Hello,   I am looking for a speech - to - text  program.  In my previous computer life I used Dragon, but of course it will not with Ubuntu.

  Is there any true programs of this nature available ?



   COMPUTIAC

---

### Post by COMPUTIAC on 2011-02-23
Hello, I have found and installed VEDICS. I won't say it was easy to install because it wasn't .

The problem I have now is when I try to start it the CPU will go to 100% and there is no way to stop it. Restarting the machine is the only way to put an end to it.

The read me in VEDICS calls for Java runtime. I can not find where to download this and install it.

Is there any fix for this ?

                   Thank's   COMPUTIAC

 [https://sourceforge.net/projects/vedics/](https://sourceforge.net/projects/vedics/)

---

### Post by lykeion on 2011-02-24
Looking at the install.sh script it wants sun-java6-jre package.
To install it you need to enable the partner repository. In a terminal you can do that like this:
```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
```

Regarding high CPU load there seem to others having this problem too: [http://vedics.sourceforge.net/?page_id=58](http://vedics.sourceforge.net/?page_id=58)
Maybe something the developers are working on, you might want to contact them about it.

---

### Post by COMPUTIAC on 2011-02-24
Hello , Thank's for the info. It did not work for some reason , this is what comes up after entering the code ;



  bob@bob-HP-dc5000-uT-DZ216AV:~$ sudo add-apt-repository "deb http://archive.canonical.com/$(lsb_release _sc) partner"
Usage: lsb_release [options]

lsb_release: error: No arguments are permitted

What am I doing wrong ?     

    COMPUTIAC

I found one mistake , made correction and this comes up now ;

bob@bob-HP-dc5000-uT-DZ216AV:~$ sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"
bob@bob-HP-dc5000-uT-DZ216AV:~$ 


It will not run anything .

---

### Post by lykeion on 2011-02-24
You missed the space between the url-part and the lsb_release-part. Try to copy and paste the command instead of entering it manually.
This command should not "run anything". It enables the partner repository. After you've done that you can run the install.sh script for VEDICS.

---

### Post by COMPUTIAC on 2011-02-24
Hello , I did the copy and paste . When I clicked on the install.sh  it opened another terminal and ran from there , no change so far , CPU 100% right now program will not run.

  COMPUTIAC

---

### Post by COMPUTIAC on 2011-02-24
Hello , somehow this created a bug in the update manager . I can not use it at this time , I guess this is why nothing happened when I entered the code .

Yes , I did report the bug .  See below :

COMPUTIAC


Distribution: Ubuntu 10.10 maverick
Application: Ubuntu Tweak 0.5.10
Desktop: gnome

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/mainwindow.py", line 502, in setup_notebook
    page = module()
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/modules/updatemanager.py", line 44, in __init__
    self.update_list()
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/modules/updatemanager.py", line 59, in update_list
    PACKAGE_WORKER.update_apt_cache(init=True)
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/common/package.py", line 216, in update_apt_cache
    self.cache = apt.Cache()
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 88, in __init__
    self.open(progress)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 130, in open
    self._list.read_main_list()
SystemError: E:Malformed line 65 in source list /etc/apt/sources.list (dist parse)

---

### Post by lykeion on 2011-02-24
Have you installed VEDICS or not? It's hard to follow your progress since you've posted so many threads about this.

What do you mean CPU 100% and program will not run? If the program doesn't run it doesn't affect CPU load.

If the CPU load is due to some Java process running in the background I think you do best to restart computer. I know that this is a "Windows-solution", but it may be easier then fiddling with processes from a terminal.

Then I think you should consider [Gnome Voice Control](http://live.gnome.org/GnomeVoiceControl) instead of VEDICS. It's easier to install, just use Ubuntu Software center to find and install it.

---

### Post by lykeion on 2011-02-24
> **COMPUTIAC said:**
> SystemError: E:Malformed line 65 in source list /etc/apt/sources.list (dist parse)

This is probably because you entered the wrong command first (no space between .com/ and maverick). Solve this by 
1. open sources.list in a text editor
```
gksu gedit /etc/apt/sources.list
```
2. Turn on showing line numbers
Edit > Preferences > Check "Display line numbers"
3. Go to line 65, and if it's something like: 
deb http://archive.canonical.com/maverick partner
You should delete this line
4. Save and exit gedit
5. Update repositories
```
sudo apt-get update
```

---

### Post by COMPUTIAC on 2011-02-24
Hello , Yes I have installed VEDICS .  When I click on the VEDICS icon the program will not start , and this is when the CPU hits 100%  not before.

Yes , I did the windows thing and did a restart , the only way to calm it down.

At this point I can not use package manager either .

COMPUTIAC

---

### Post by COMPUTIAC on 2011-02-24
Hello , this is what I get after entering the code and removing line 65 .

E: Malformed line 66 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.


COMPUTIAC

---

### Post by COMPUTIAC on 2011-02-24
Hello , I just received this about the bug report .

Public bug reported:


Distribution: Ubuntu 10.10 maverick
Application: Ubuntu Tweak 0.5.10
Desktop: gnome

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/mainwindow.py", line 502, in setup_notebook
    page = module()
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/modules/updatemanager.py", line 44, in __init__
    self.update_list()
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/modules/updatemanager.py", line 59, in update_list
    PACKAGE_WORKER.update_apt_cache(init=True)
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/common/package.py", line 216, in update_apt_cache
    self.cache = apt.Cache()
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 88, in __init__
    self.open(progress)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 130, in open
    self._list.read_main_list()
SystemError: E:Malformed line 65 in source list /etc/apt/sources.list (dist parse)

** Affects: ubuntu-tweak
     Importance: Undecided
         Status: New


So , for now I can't use the update or package managers .   Any ideas ?

COMPUTIAC

---

### Post by perspectoff on 2011-02-24
Yes, Digium / Vestec / LumenVox have speech recognition for Linux (which is widely deployed and available for commercial uses), but it is not free and open source. Modules are available for Asterisk PBX.

It is also quite expensive.

But don't say there isn't good speech recognition available for Linux.

---

### Post by lykeion on 2011-02-24
> **COMPUTIAC said:**
> Hello , this is what I get after entering the code and removing line 65 .
E: Malformed line 66 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
COMPUTIAC
Maybe remove line 66, or is it too obvious? Copy and paste your sources.list here

---

### Post by COMPUTIAC on 2011-02-24
Hello , here is the list . There seems to be a problem with line 66 . I sent another bug report for that one .

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://archive.connical.com/](http://archive.connical.com/) maverick partner
deb-src [http://archive.connical.com/](http://archive.connical.com/) maverick partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner

deb-src [http://archive.canonical.com/](http://archive.canonical.com/) partner         <-------------  this is line   #66
deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner

---

### Post by lykeion on 2011-02-24
Okay, you could delete this line and update repos to fix your problems.

Actually you could delete all the lines 59-70, since the partner repositories is already added above (line 45-46).

For a more compact sources.list you can replace the contents with this:
```
deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu maverick-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted universe multiverse

deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main
```

---

### Post by COMPUTIAC on 2011-02-24
Hello , I can now use package manager .  When I try to use up-date manager I get this message .

W:GPG error: [http://archive.connical.com](http://archive.connical.com) maverick Release: The following signatures were invalid: NODATA 1 NODATA 2, W:Failed to fetch [http://archive.connical.com/dists/maverick/partner/source/Sources.bz2](http://archive.connical.com/dists/maverick/partner/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)
, W:Failed to fetch [http://archive.connical.com/dists/maverick/partner/binary-i386/Packages.bz2](http://archive.connical.com/dists/maverick/partner/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)
, E:Some index files failed to download, they have been ignored, or old ones used instead.


 OK , so you are saying to delete everything in the source.list      and replace it with your list  ?

COMPUTIAC

---

### Post by lykeion on 2011-02-24
Yes do that. http://archive.connical.com is not a valid URL

---

### Post by COMPUTIAC on 2011-02-24
Hello , This is the latest source.list .  There seems to be a problem with the last 4 lines .

COMPUTIAC



bob@bob-HP-dc5000-uT-DZ216AV:~$ gksu gedit /edit/apt/sources.list
bob@bob-HP-dc5000-uT-DZ216AV:~$ gksu gedit /etc/apt/sources.list

bob@bob-HP-dc5000-uT-DZ216AV:~$ 
bob@bob-HP-dc5000-uT-DZ216AV:~$ sudo apt-get update
[sudo] password for bob: 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]
Ign [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main Translation-en           
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,338B]                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Get:3 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198B]                 
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en              
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Get:4 [http://archive.canonical.com](http://archive.canonical.com) maverick Release [5,925B]                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Get:5 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [471B]                    
Get:6 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources [3,808B]           
Get:7 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages [7,448B]     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Get:8 [http://archive.connical.com](http://archive.connical.com) maverick Release.gpg [70.6kB]
Get:9 [http://archive.connical.com/](http://archive.connical.com/) maverick/partner Translation-en [70.6kB]
99% [9 Translation-en bzip2 0B]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.connical.com/](http://archive.connical.com/) maverick/partner Translation-en
Get:10 [http://archive.connical.com/](http://archive.connical.com/) maverick/partner Translation-en_US [70.6kB]
69% [10 Translation-en_US bzip2 0B]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.connical.com/](http://archive.connical.com/) maverick/partner Translation-en_US
Get:11 [http://archive.connical.com](http://archive.connical.com) maverick Release [70.6kB]
Ign [http://archive.connical.com](http://archive.connical.com) maverick Release
Get:12 [http://archive.connical.com](http://archive.connical.com) maverick/partner Sources [70.6kB]
62% [12 Sources bzip2 0B]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.connical.com](http://archive.connical.com) maverick/partner Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:13 [http://archive.connical.com](http://archive.connical.com) maverick/partner i386 Packages [70.6kB]
68% [13 Packages bzip2 0B]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.connical.com](http://archive.connical.com) maverick/partner i386 Packages
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 443kB in 4s (93.3kB/s)
W: GPG error: [http://archive.connical.com](http://archive.connical.com) maverick Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch [http://archive.connical.com/dists/maverick/partner/source/Sources.bz2](http://archive.connical.com/dists/maverick/partner/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://archive.connical.com/dists/maverick/partner/binary-i386/Packages.bz2](http://archive.connical.com/dists/maverick/partner/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.
bob@bob-HP-dc5000-uT-DZ216AV:~$

---

### Post by COMPUTIAC on 2011-02-24
Hello , where and how do I enter the code for the source.list  ?

In a terminal or in the window with the source.list .

COMPUTIAC

---

### Post by lykeion on 2011-02-24
> Hello , where and how do I enter the code for the source.list ?
In a terminal or in the window with the source.list.
Err...what? 

1. Open sources.list with gedit
```
gksu gedit /etc/apt/sources.list
```

2. Delete all contents (Select all (Ctrl + a) > Delete)

3. Copy this (select it > right-click > Copy):
```
deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu maverick-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted universe multiverse

deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main
```

4. Back to gedit > Paste (Ctrl + v) contents

5. Save and exit gedit

6. Update repositories

---

### Post by COMPUTIAC on 2011-02-24
Hello , Great !    Everything appears to be back to a functioning state with no more warnings. 

 I apologize for appearing so lame in-doing this , as most others I am a very accomplished whiz in M$ , so far this is Greek to me at this point . It is getting easier as I move along . 

How do you suggest I go about installing the gnome voice program ? Should I take out anything else besides the VEDICS .


I would also like to thank you for all your help and sticking with me in this mess . I realize I took up a lot of your time .


COMPUTIAC

---

### Post by lykeion on 2011-02-24
You sure did need some very hands-on helping, but that's okay. :)

Installing gnome voice control is not different from installing any other program in Ubuntu. You can use several methods:

Method #1 Using Ubuntu Software Center
[LIST=1]
[*]Applications > Ubuntu Software Center
[*]Enter "gnome voice control" (without quotes) in search field
[*]Select gnome-voice-control > click Install
[/LIST]
Method #2 Using Synaptics Package Manager
[LIST=1]
[*]System > Administration > Synaptics Package Manager
[*]Enter "gnome voice control" (without quotes) in quicksearch field
[*]Right-click gnome-voice-control > Mark for installation
[*]Click Apply button
[/LIST]
Method #3 Using apt-get from a terminal
[LIST=1]
[*]Applications > Accessories > Terminal
[*]Enter this command:
[/LIST]
```
sudo apt-get install gnome-voice-control
```

---

### Post by COMPUTIAC on 2011-02-24
Hello , I have it installed , finally !  It would not work at first , of course . I went in and found and removed all parts of VEDICS then it started working . 

I still have a problem with the CPU at times running 100%  when this program is open , and it will freeze the system , the only way to stop it is to do a manual shut down with the power switch .  I know , not a good idea  but no choice .

I would like to find a way to  "train" this to do more commands . Vedics had a way to submit recordings . I will have to nose around a bit to find something similar . 

At this point it will not do all commands , I will work on it though .

Well , again , Thank's for your time and patience with a knuckle head .  I don't know if you were laughing at me or swearing at me every-time I posted back .

If you have any thoughts , please post back .           Below is a picture of my machine !!  

           
                                                  
COMPUTIAC

---

### Post by lykeion on 2011-02-24
By looking at your avatar and the attached burning computer pic I figured it's best to show a lot of patience with you to save you from wrecking expensive hardware :)

Good luck with GVC but remember that speech recognition in Linux is a work in progress. Here are some links to related projects:
[https://help.ubuntu.com/community/Accessibility#Voice%20Recognition](https://help.ubuntu.com/community/Accessibility#Voice%20Recognition)
[http://en.wikipedia.org/wiki/Speech_recognition_in_Linux](http://en.wikipedia.org/wiki/Speech_recognition_in_Linux)

---

### Post by COMPUTIAC on 2011-02-24
Hello ,  I learned a long time ago the insurance co,  will believe something with flames  rather than hammer and pry-bar marks all over it !  

I realize this program is not Dragon Naturally Speaking , maybe with a lot of help it will be .

Any thoughts on the CPU thing ?


Thank's a lot again ,  COMPUTIAC

---

### Post by lykeion on 2011-02-24
So you got the 100% CPU problem with *both* VEDICS and GVC?

Just to make sure, could you start **top** to monitor your processes before launching GVC.
In a terminal enter: top
Shift + p -> sort on cpu%
q -> quit top

If it's the gnome-voice-control applet that's eating all your CPU (and you also had this problem with VEDICS), my guess would be some problems with your audio configuration. Search in this forum with keywords like: pulseaudio 100% cpu, or start a new thread.

If it's another process like Xorg or firefox that's causing the cpu load it's something other (graphic card, flash).

That's all for today for me, maybe I'll check this thread tomorrow.

---

### Post by COMPUTIAC on 2011-02-24
Hello , Yes I can start it . The highest ones are : plug-in container  7.5 +- %

                                                                       pulseaudio  5 - 7 +- %

                                                                       voice_ control  4 - 6 +- %

                                                                      Firefox bin  hits   26 %   but not steady
 The rest seem to be behaving themselves .

 Right now I can't get this machine to max out . Just my luck .

I will keep an eye on it .

COMPUTIAC

---

### Post by COMPUTIAC on 2011-02-25
Hello , I could not have VEDICS operating so it was of any use , I had it so it would do some commands , but was just too tricky .

  I then went in a different direction and looked into the workings of wine . I found an article which mentioned the use of Dragon Naturally Speaking , and was mountable using wine.

  I had a copy of Dragon NS 10 standard .    First I installed wine , then the Dragon .  

Some searching , with trial and error led me to using " _wine core exe_ " to run the " _setup.exe _" in Dragon . 

The installation from then on went very well . I will admit I can not use it 100% as yet , I see no problem in making it run at 100% very shortly . 

I will post my progress on how to make it work 100% .  If anyone can add something to this , please feel free .


COMPUTIAC

---

### Post by lykeion on 2011-02-26
A good resource for running windows programs with wine is [WineHQ AppDB]("http://appdb.winehq.org/") and when I search for DNS 10 Standard I can see it got gold rating, see  [HERE](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13563). 
Read the howto to configure font and pulseaudio settings. Good luck!

---

### Post by COMPUTIAC on 2011-02-26
Hello  lykeion ,  Thank's for the post . There is a ton of useful information to go over.

  Do you have any thoughts as to what I should take off of my machine as far as programs I do not need any longer , from trying to have Vedics and Gnome Voice Control .

COMPUTIAC

---

### Post by lykeion on 2011-02-26
If you installed gnome-voice-control with a package manager (Ubuntu Software Center, Synaptics, or apt-get) you could easily remove it the same way.
In Synaptics you can also remove local/obsolete packages and residual config of earlier installed packages.

Start Synaptics:
System > Administration > Synaptics Package Manager

Remove GVC: 
Enter "gnome-voice-control" in search field
Rightclick gnome-voice-control package > Mark for complete removal > Click Apply button > Clear search field (so all packages are shown again)

Remove local/obsolete packages:
Click Status button at bottom-left > Select "Installed (local or obsolete)" to left > Rightclick found packages > Mark for complete removal > Click Apply button

Remove residual config earlier installed packages:
Click Status button at bottom-left > Select "Not installed (residual config)" to left > Rightclick found packages > Mark for complete removal > Click Apply button

---

### Post by COMPUTIAC on 2011-02-26
Hello lykeion,

 Great directions , went perfect as you expected . Is there any of the many Java applications I could remove , or will they not do any harm in staying on-board ? With out conflicts .

  I am not positive if DNS uses any or not . It doe's use C++ which I think is totally different .

COMPUTIAC

---

### Post by COMPUTIAC on 2011-03-07
Hello azakmi2 , 

The problem I had after installing VEDICS was , I could not start it without the CPU maxing out at 100% . The only way to quit the program and bring the CPU rate to a compatible rate was to reboot the machine .

  The "windows thing"  means to restart , or reboot the computer . They both mean the same thing .

If you have any other questions , please post them .

  COMPUTIAC

---

### Post by Paddy Landau on 2011-03-16
This question comes up regularly on the forums, and is one that I am interested in (for speech recognition and dictation).

Unfortunately, it would appear that Linux does not have good speech recognition software yet. The most promising seems to be [Julius]("http://julius.sourceforge.jp/en_index.php?q=index-en.html"). Unfortunately, although Julius works, the developers have only a Japanese speech model and need help developing an English model. (They do have [an English model]("http://julius.sourceforge.jp/en_index.php?q=index-en.html#about_models") but it has problems including severely restricted licensing.)

I think that if you depend on speech recognition, you will have to remain with Windows or Mac for the time being.

---

### Post by rao.nischal on 2011-04-22
Hi Computiac,

I am one of the developers of vedics. Regarding the CPU going 100%, can you please let me know whether you have installed Sun JRE or OpenJDK?

If it is OpenJDK, there is an issue in it which causes the CPU to hit 100%.

I would really appreciate if you can reach out for "VEDICS" related help on [VEDICS forum]("https://sourceforge.net/projects/vedics/forums/forum/1127786") so that we can help you better.

Thanks & Regards,
Nischal E Rao

---

