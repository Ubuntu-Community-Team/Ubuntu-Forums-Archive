---
title: "Ubuntu, slow when updating"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-02-15
Don't know what happened, but still the [b]laptop turned off/logged off automatically[b] issue still remained...

Ubuntu Gutsy is slow, and unstable. Like for example, while installing a package, the mouse lags, but where's multi tasking there?

Upon starting Ubuntu, my system load is more than 4.0-4.80+ which is really weird, take not, processor 80-100%

And, for example I am watching a You Tube video, my systen load is more than 3.0+ with my processor, is 100% ...

I mean, for sure the system will become unstable... i am still monitoring, but probably it's working, my laptop does not turn off automatically anymore, because just set the limit of cpufreq to maximum of 1.40GHz out of 1.70GHz, the only problem is, I wanted it to be executed everytime I turn on my laptop.:confused:

Hopefully, I can gain the REAL speed of my laptop just like the fresh install of Ubuntu.

Also, I've tried using the old i810 driver for Intel graphics card along with the 915resolution fix, although I think, in my opinion, corrent me if im wrong, makes the system (animations-screen savers) more faster...

At least changing it to old drivers, makes the flickering (something like a clone of the effect, will stay on ur screen) effects of compiz, is or are probably gone. The issue wherein when the screensaver runs, a random black box or black flashing box of squares appears randomly.

Still I've experienced those, but not as much as using the intel experimental drivers. I've tried playing some 3d games of ubuntu from the add/remove programs, and it's so slow!!!

Oh my god I wish someone could really help me to make my laptop faster! I still have more than 7GB of space left... Please help.. my specifications are in my signature...

---

### Post by oedha on 2008-02-15
why do you use old i810 ? 
what intel are you using....?
mine is 915GM and i am using intel experiment + 915resolution....when i used i810...it turned just like you.
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Samhain13 on 2008-02-15
I think the YouTube / Flash video issue is a really big deal, I'm experiencing the same ~100% CPU usage the OP describes. And when one watches for a while, the temperature can easily rise 3-5 degrees Celcius-- and where I'm from, that's not a good thing since room temperature is already high to begin with.

As for the other things described by OP, I don't know. I haven't had those bad experiences despite having around the same specs: AMD Sempron 2400+ (1.66GHz), 1GB RAM and a 256MB Nvidia GeForce 5500. I previously tried experimenting with the available 3D games like Torcs and Vega Strike (with Advanced Desktop Effects enabled), and everything seemed to be working fine apart from the heat issue I described. But it's not as bad as merely watching Flash videos.

I am using the Realtime Kernel though, maybe that makes a difference?

---

### Post by mbsullivan on 2008-02-15
Hi guys,

The youtube video thing sounds like a bug... Without doing more research I can't really tell you a fix. Since it's 5AM right now, I'm not going to go searching, but you could try upgrading to the Hardy version of the Flash plugin (flashplugin-nonfree) and see if that solves your problem.

To do so, add:

> # hardy repositories
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy main restricted universe multiverse

to your /etc/apt/sources.list file, and add:

> Package: flashplugin-nonfree
Pin: release a=hardy
Pin-Priority: 1000

to your /etc/apt/preferences file.  The do a:

```
sudo aptitude update; sudo aptitude safe-upgrade
```

To upgrade your flash plugin. It doesn't look much newer than the Gutsy plugin, though.

> I am using the Realtime Kernel though, maybe that makes a difference?

Why are you using the realtime kernel?  Real time operating systems are made to put a hard constraint on the time that tasks are completed. As such, they are very important to embedded systems (like an IPod) or control systems (airplane controls). 

However, guaranteeing that tasks will be executed in a certain amount of time does not mean that processes will be executed faster than on a normal "best effort" operating system. In general, the opposite is true... A normal operating system will be faster and less experimental than a real-time one.

Mike

---

### Post by karlo on 2008-02-15
> **oedha said:**
> why do you use old i810 ? 
what intel are you using....?
mine is 915GM and i am using intel experiment + 915resolution....when i used i810...it turned just like you.
sudo dpkg-reconfigure -phigh xserver-xorg

Obviously according to my post it's **915**, if you read it carefully...

By default I am using the Intel Experiment driver, no need to use 915resolution when you are using the Intel Experiment driver. [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

**Now** I am using the old one i810 with 915resolution because by default, when you use the old driver, you can only have 800x600 resolution.

Don't worry, I know how to reconfigure it, I had my own thread for it [http://ubuntuforums.org/showthread.php?t=695080](http://ubuntuforums.org/showthread.php?t=695080)

---

### Post by karlo on 2008-02-15
> **Samhain13 said:**
> I think the YouTube / Flash video issue is a really big deal, I'm experiencing the same ~100% CPU usage the OP describes. And when one watches for a while, the temperature can easily rise 3-5 degrees Celcius-- and where I'm from, that's not a good thing since room temperature is already high to begin with.

As for the other things described by OP, I don't know. I haven't had those bad experiences despite having around the same specs: AMD Sempron 2400+ (1.66GHz), 1GB RAM and a 256MB Nvidia GeForce 5500. I previously tried experimenting with the available 3D games like Torcs and Vega Strike (with Advanced Desktop Effects enabled), and everything seemed to be working fine apart from the heat issue I described. But it's not as bad as merely watching Flash videos.

I am using the Realtime Kernel though, maybe that makes a difference?

What does **OP** means? So you are not the only one who experience flash videos high memory usage? I mean, when you watch Ubuntu demos on youtube, you'll see they have more than 4 youtube sites playing at the same time while doing the cube effects etc... and they all played smoothly. The laptop mode tools etc... anything for laptop power etc .. **except the built in one[/B the [B]powernowd** thing... **ALL OF THEM** does not work because my laptop does not support temperature readings, I think it only supports the** cpu frequency throttling**.

I tried having a demo of **Scorched 3D** and it does not work, everything **was slow.** I was also hearing **strange clickng sounds**.

What's a Realtime Kernel?:confused:

---

### Post by Trail on 2008-02-15
OP = original poster

---

### Post by karlo on 2008-02-15
> **mbsullivan said:**
> Hi guys,

The youtube video thing sounds like a bug... Without doing more research I can't really tell you a fix. Since it's 5AM right now, I'm not going to go searching, but you could try upgrading to the Hardy version of the Flash plugin (flashplugin-nonfree) and see if that solves your problem.

To do so, add:



to your /etc/apt/sources.list file, and add:



to your /etc/apt/preferences file.  The do a:

```
sudo aptitude update; sudo aptitude safe-upgrade
```

To upgrade your flash plugin. It doesn't look much newer than the Gutsy plugin, though.



Why are you using the realtime kernel?  Real time operating systems are made to put a hard constraint on the time that tasks are completed. As such, they are very important to embedded systems (like an IPod) or control systems (airplane controls). 

However, guaranteeing that tasks will be executed in a certain amount of time does not mean that processes will be executed faster than on a normal "best effort" operating system. In general, the opposite is true... A normal operating system will be faster and less experimental than a real-time one.

Mike

First of all thank you for your suggestion. Thank god someone replied, I've been posting more than 2 threads and none replied, specially with the cpufreq-set issue. Do you know how to set  it or run that program, when booting?

So that I can set my minumum processor speed to 600MHz, maximum to 1.40GHz(originally 1.70GHz), also make it ondemand.

If you also know the difference between userspacem ondemand, powersave, conservative ... an explaination would be great.

Please help me solve this issue, I think it has connectivity with the above theories of mine.

About the updates, I tried it, and I saw the following (check my attachment) ... I also was trying to check only **Flash**, but a message box always prompts me to do a **Partial Upgrade**.

Also on the terminal after adding the sources of **Hardy**, I have to download 600MB? Just for flash? Or the whole operating system?:confused::confused:

---

### Post by Samhain13 on 2008-02-15
> **mbsullivan said:**
> Why are you using the realtime kernel?  Real time operating systems are made to put a hard constraint on the time that tasks are completed. As such, they are very important to embedded systems (like an IPod) or control systems (airplane controls). 

I play around with Rosegarden. When using the Generic, it complains about "resolution" being low. And the sound cracks/pops during authoring and playback.

---

### Post by mbsullivan on 2008-02-15
> If you also know the difference between userspacem ondemand, powersave, conservative ... an explaination would be great.

Okay... a brief explanation is that the userspace and ondemand CPU frequency governors modulate your CPU speed (as I'm sure you know) based on the current amount of program activity. The userspace governor runs completely in userspace (i.e. with no kernel interaction). On the other hand, the ondemand governor is newer and has kernel support (since linux-2.6.9, if it's enabled in your build). 

The "powersave" governor keeps your CPU at the slowest speed step at all times, and the "conservative" governor keeps your CPU at the fastest speed step at all times.

So... what this issue boils down to is... use ondemand! It switches speed much quicker than the userspace daemon, which results in fewer performance losses, but resides in the lowest speed step the vast majority of the time, which saves lots of power.

> Do you know how to set it or run that program, when booting?

So that I can set my minumum processor speed to 600MHz, maximum to 1.40GHz(originally 1.70GHz), also make it ondemand.

Some distilled directions follow (mostly from [here]("http://ubuntuforums.org/showthread.php?t=248867"))... put these into the command line after booting to recovery mode.

(1) remove userspace daemons, if present

```
sudo apt-get remove powernowd cpudyn
```

(2) load speedstep module for Pentium M

```
sudo modprobe speedstep-centrino
```

... if this doesn't work for some reason, do:

```
sudo modprobe acpi-cpufreq
```

(3) load CPU governor

```
sudo modprobe cpufreq_ondemand
```

(4) enable ondemand CPU governor

```
sudo -s
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

Okay... now the ondemand governor should be enabled. If this works, let's make the changes permanent.

(5) load cpufreq_ondemand at startup... add "cpufreq_ondemand" to the end of /etc/modules. You can also remove any previous cpu governors, if present.

(6) set CPU governor to ondemand...

```
sudo apt-get install sysfsutils
``` 

Then add the line below to the end of /etc/sysfs.conf:

```
devices/system/cpu/cpu0/cpufreq/scaling_governor=ondemand
```

As for "setting the minimum to 600MHz, maximum to 1.40GHz", I don't believe it's possible to set the steps by which your processor changes speed (I may be wrong)... But, it's possible to see the speed intervals by doing a:

```
 cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

Hope this helps!
Mike

---

### Post by mbsullivan on 2008-02-15
Hi!

First time... I missed this part:

> Also on the terminal after adding the sources of Hardy, I have to download 600MB? Just for flash? Or the whole operating system?

Yikes... it shouldn't do that!  What exactly are the contents of your /etc/apt/sources.list and /etc/preferences ?

You should have BOTH Gutsy and Hardy repositories in your sources.list... and your preferences should look something similar to:

```
Package: *
Pin: release a=gutsy
Pin-Priority: 500

Package: flashplugin-nonfree
Pin: release a=hardy
Pin-Priority: 1000

```

Then, do a sudo aptitude update; sudo aptitude safe-upgrade. If it refuses to upgrade flashplugin-nonfree, saying:

> The following packages have been kept back:
  flashplugin-nonfree 


Then try doing a:

```
sudo aptitude dist-upgrade
```

This will NOT upgrade to Hardy (misleading), but rather will upgrade the libraries associated with flashplugin-nonfree, as well (which is the reason that it would have been held back in the first place). Regardless, it shouldn't be more than a couple of kilobytes extra... NOT 600 MB!

Mike

---

### Post by karlo on 2008-02-16
> **mbsullivan said:**
> Hi!

First time... I missed this part:



Yikes... it shouldn't do that!  What exactly are the contents of your /etc/apt/sources.list and /etc/preferences ?

You should have BOTH Gutsy and Hardy repositories in your sources.list... and your preferences should look something similar to:

```
Package: *
Pin: release a=gutsy
Pin-Priority: 500

Package: flashplugin-nonfree
Pin: release a=hardy
Pin-Priority: 1000

```

Then, do a sudo aptitude update; sudo aptitude safe-upgrade. If it refuses to upgrade flashplugin-nonfree, saying:



Then try doing a:

```
sudo aptitude dist-upgrade
```

This will NOT upgrade to Hardy (misleading), but rather will upgrade the libraries associated with flashplugin-nonfree, as well (which is the reason that it would have been held back in the first place). Regardless, it shouldn't be more than a couple of kilobytes extra... NOT 600 MB!

Mike

Sorry for a **very late** reply...

**sources.list**

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ph.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.


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

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://www.getautomatix.com/apt gutsy main
deb http://download.tuxfamily.org/syzygy42 gutsy exaile

#AUTOMATIX REPOS START
deb http://security.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse #Added by software-properties
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse #Added by software-properties
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy-proposed main restricted universe multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy-proposed main restricted universe multiverse #Added by software-properties
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse #Added by software-properties
#AUTOMATIX REPOS END

deb http://ppa.launchpad.net/stemp/ubuntu gutsy main
deb-src http://ppa.launchpad.net/stemp/ubuntu gutsy main

deb http://ppa.launchpad.net/tualatrix/ubuntu gutsy main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu gutsy main
deb http://repository.akirad.net akirad-gutsy main
deb-src http://repository.akirad.net akirad-gutsy main
```

There.. oh yeah, **gedit** takes time to show... is there anything like a notepad but much more faster than **gedit**?:)

---

### Post by Samhain13 on 2008-02-17
Karlo, something just occured to me.

Can you go to System > Preferences > Sessions and see if "Tracker" is checked? If so, uncheck it then log-out and log-in again. See if there's any improvement on the speed with which Gedit or other applications load.

---

### Post by karlo on 2008-02-18
> **Samhain13 said:**
> I think the YouTube / Flash video issue is a really big deal, I'm experiencing the same ~100% CPU usage the OP describes. And when one watches for a while, the temperature can easily rise 3-5 degrees Celcius-- and where I'm from, that's not a good thing since room temperature is already high to begin with.

As for the other things described by OP, I don't know. I haven't had those bad experiences despite having around the same specs: AMD Sempron 2400+ (1.66GHz), 1GB RAM and a 256MB Nvidia GeForce 5500. I previously tried experimenting with the available 3D games like Torcs and Vega Strike (with Advanced Desktop Effects enabled), and everything seemed to be working fine apart from the heat issue I described. But it's not as bad as merely watching Flash videos.

I am using the Realtime Kernel though, maybe that makes a difference?

**SORRY FOR THE LATE REPLY**... don't know if I replied to this message, anyway, the Hardware Sensors Applet or anything that reads temperatures and turns on the fan, my laptop does not support it.

---

### Post by karlo on 2008-02-18
> **mbsullivan said:**
> Hi guys,

The youtube video thing sounds like a bug... Without doing more research I can't really tell you a fix. Since it's 5AM right now, I'm not going to go searching, but you could try upgrading to the Hardy version of the Flash plugin (flashplugin-nonfree) and see if that solves your problem.

To do so, add:



to your /etc/apt/sources.list file, and add:



to your /etc/apt/preferences file.  The do a:

```
sudo aptitude update; sudo aptitude safe-upgrade
```

To upgrade your flash plugin. It doesn't look much newer than the Gutsy plugin, though.



Why are you using the realtime kernel?  Real time operating systems are made to put a hard constraint on the time that tasks are completed. As such, they are very important to embedded systems (like an IPod) or control systems (airplane controls). 

However, guaranteeing that tasks will be executed in a certain amount of time does not mean that processes will be executed faster than on a normal "best effort" operating system. In general, the opposite is true... A normal operating system will be faster and less experimental than a real-time one.

Mike

**I FOLLOWED IT AGAIN (ABOVE)...**

```
Ign http://download.tuxfamily.org gutsy/exaile Translation-en_PH               
Ign http://ppa.launchpad.net gutsy/main Translation-en_PH                      
Ign http://ph.archive.ubuntu.com gutsy/multiverse Translation-en_PH            
Get:6 http://repository.akirad.net akirad-gutsy Release.gpg [189B]             
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_PH     
Get:7 http://www.getautomatix.com gutsy Release.gpg [189B]                     
Get:8 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Hit http://wine.budgetdedicated.com gutsy/main Sources                         
Get:9 http://download.tuxfamily.org gutsy Release [10.9kB]                     
Get:10 http://security.ubuntu.com hardy Release.gpg [191B]                     
Ign http://www.getautomatix.com gutsy/main Translation-en_PH                   
Get:11 http://archive.ubuntu.com hardy Release.gpg [191B]                      
Hit http://wine.budgetdedicated.com gutsy/main Packages                        
Ign http://repository.akirad.net akirad-gutsy/main Translation-en_PH           
Hit http://security.ubuntu.com gutsy-security Release                          
Hit http://www.getautomatix.com gutsy Release                                  
Ign http://archive.ubuntu.com hardy/main Translation-en_PH                     
Hit http://repository.akirad.net akirad-gutsy Release                          
Hit http://www.getautomatix.com gutsy/main Packages                            
Get:12 http://download.tuxfamily.org gutsy/exaile Packages [1227B]             
Get:13 http://security.ubuntu.com hardy Release [65.9kB]                       
Ign http://archive.ubuntu.com hardy/restricted Translation-en_PH               
Ign http://archive.ubuntu.com hardy/universe Translation-en_PH                 
Hit http://archive.canonical.com gutsy/partner Packages                        
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_PH               
Ign http://ppa.launchpad.net gutsy Release.gpg                                 
Hit http://archive.ubuntu.com gutsy Release                                    
Get:14 http://ph.archive.ubuntu.com gutsy-updates Release.gpg [191B]           
Ign http://ppa.launchpad.net gutsy/main Translation-en_PH                      
Ign http://ph.archive.ubuntu.com gutsy-updates/main Translation-en_PH          
Hit http://ppa.launchpad.net gutsy Release                                     
Ign http://ph.archive.ubuntu.com gutsy-updates/restricted Translation-en_PH    
Hit http://ppa.launchpad.net gutsy Release                                     
Ign http://ph.archive.ubuntu.com gutsy-updates/universe Translation-en_PH      
Ign http://ppa.launchpad.net gutsy/main Packages                               
Hit http://repository.akirad.net akirad-gutsy/main Packages                    
Ign http://ph.archive.ubuntu.com gutsy-updates/multiverse Translation-en_PH    
Get:15 http://archive.ubuntu.com hardy Release [65.9kB]                        
Ign http://ppa.launchpad.net gutsy/main Sources                                
Ign http://ppa.launchpad.net gutsy/main Packages                               
Hit http://archive.canonical.com gutsy/partner Sources                         
Ign http://ppa.launchpad.net gutsy/main Sources                                
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Hit http://repository.akirad.net akirad-gutsy/main Sources                     
Hit http://ppa.launchpad.net gutsy/main Packages                               
Get:16 http://ph.archive.ubuntu.com gutsy-proposed Release.gpg [191B]          
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://ppa.launchpad.net gutsy/main Sources                                
Ign http://ph.archive.ubuntu.com gutsy-proposed/main Translation-en_PH         
Hit http://security.ubuntu.com gutsy-security/universe Packages                
Hit http://ppa.launchpad.net gutsy/main Packages                               
Ign http://ph.archive.ubuntu.com gutsy-proposed/restricted Translation-en_PH   
Hit http://security.ubuntu.com gutsy-security/multiverse Packages              
Hit http://ppa.launchpad.net gutsy/main Sources                                
Ign http://ph.archive.ubuntu.com gutsy-proposed/universe Translation-en_PH     
Hit http://security.ubuntu.com gutsy-security/main Sources                     
Ign http://ph.archive.ubuntu.com gutsy-proposed/multiverse Translation-en_PH   
Hit http://security.ubuntu.com gutsy-security/restricted Sources               
Get:17 http://ph.archive.ubuntu.com gutsy-backports Release.gpg [191B]         
Hit http://security.ubuntu.com gutsy-security/universe Sources                 
Ign http://ph.archive.ubuntu.com gutsy-backports/main Translation-en_PH        
Hit http://security.ubuntu.com gutsy-security/multiverse Sources               
Ign http://ph.archive.ubuntu.com gutsy-backports/restricted Translation-en_PH  
Ign http://ph.archive.ubuntu.com gutsy-backports/universe Translation-en_PH    
Ign http://ph.archive.ubuntu.com gutsy-backports/multiverse Translation-en_PH  
Hit http://archive.ubuntu.com gutsy/main Sources                               
Hit http://ph.archive.ubuntu.com gutsy Release                                 
Hit http://archive.ubuntu.com gutsy/restricted Sources                         
Get:18 http://security.ubuntu.com hardy/main Sources [315kB]                   
Hit http://ph.archive.ubuntu.com gutsy-updates Release                         
Hit http://ph.archive.ubuntu.com gutsy-proposed Release                        
Get:19 http://archive.ubuntu.com hardy/main Packages [1155kB]                  
Get:20 http://ph.archive.ubuntu.com gutsy-backports Release [44.0kB]           
Hit http://ph.archive.ubuntu.com gutsy/main Packages                           
Hit http://ph.archive.ubuntu.com gutsy/universe Packages                       
Hit http://ph.archive.ubuntu.com gutsy/restricted Packages                     
Hit http://ph.archive.ubuntu.com gutsy/multiverse Packages                     
Hit http://ph.archive.ubuntu.com gutsy/main Sources                            
Hit http://ph.archive.ubuntu.com gutsy/universe Sources                        
Hit http://ph.archive.ubuntu.com gutsy/restricted Sources                      
Hit http://ph.archive.ubuntu.com gutsy/multiverse Sources                      
Hit http://ph.archive.ubuntu.com gutsy-updates/main Packages                   
Hit http://ph.archive.ubuntu.com gutsy-updates/restricted Packages             
Hit http://ph.archive.ubuntu.com gutsy-updates/universe Packages               
Hit http://ph.archive.ubuntu.com gutsy-updates/multiverse Packages             
Hit http://ph.archive.ubuntu.com gutsy-updates/main Sources                    
Hit http://ph.archive.ubuntu.com gutsy-updates/restricted Sources              
Hit http://ph.archive.ubuntu.com gutsy-updates/universe Sources                
Hit http://ph.archive.ubuntu.com gutsy-updates/multiverse Sources              
Hit http://ph.archive.ubuntu.com gutsy-proposed/main Packages                  
Hit http://ph.archive.ubuntu.com gutsy-proposed/restricted Packages            
Hit http://ph.archive.ubuntu.com gutsy-proposed/universe Packages              
Hit http://ph.archive.ubuntu.com gutsy-proposed/multiverse Packages            
Hit http://ph.archive.ubuntu.com gutsy-proposed/main Sources                   
Hit http://ph.archive.ubuntu.com gutsy-proposed/restricted Sources             
Hit http://ph.archive.ubuntu.com gutsy-proposed/universe Sources               
Hit http://ph.archive.ubuntu.com gutsy-proposed/multiverse Sources             
Get:21 http://security.ubuntu.com hardy/restricted Sources [1604B]             
Get:22 http://security.ubuntu.com hardy/universe Sources [1342kB]              
Get:23 http://ph.archive.ubuntu.com gutsy-backports/main Packages [27.1kB]     
Get:24 http://ph.archive.ubuntu.com gutsy-backports/restricted Packages [14B]  
Get:25 http://ph.archive.ubuntu.com gutsy-backports/universe Packages [81.2kB] 
Get:26 http://ph.archive.ubuntu.com gutsy-backports/multiverse Packages [6660B]
Get:27 http://ph.archive.ubuntu.com gutsy-backports/main Sources [7799B]       
Get:28 http://ph.archive.ubuntu.com gutsy-backports/restricted Sources [14B]   
Get:29 http://ph.archive.ubuntu.com gutsy-backports/universe Sources [17.8kB]  
Get:30 http://ph.archive.ubuntu.com gutsy-backports/multiverse Sources [2264B] 
Get:31 http://archive.ubuntu.com hardy/restricted Packages [6727B]             
Get:32 http://archive.ubuntu.com hardy/universe Packages [4312kB]              
Get:33 http://security.ubuntu.com hardy/multiverse Sources [59.0kB]            
Get:34 http://archive.ubuntu.com hardy/multiverse Packages [168kB]             
Fetched 7690kB in 4m43s (27.1kB/s)                                             
Reading package lists... Done
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_PH
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_PH
Ign http://ppa.launchpad.net gutsy Release.gpg                                  
Ign http://ppa.launchpad.net gutsy/main Translation-en_PH                       
Ign http://ppa.launchpad.net gutsy Release.gpg                                  
Ign http://ppa.launchpad.net gutsy/main Translation-en_PH                       
Get:1 http://archive.canonical.com gutsy Release.gpg [191B]                     
Get:2 http://download.tuxfamily.org gutsy Release.gpg [189B]                    
Get:3 http://wine.budgetdedicated.com gutsy Release.gpg [191B]                  
Get:4 http://repository.akirad.net akirad-gutsy Release.gpg [189B]              
Get:5 http://archive.ubuntu.com gutsy Release.gpg [191B]                        
Get:6 http://security.ubuntu.com gutsy-security Release.gpg [191B]              
Get:7 http://www.getautomatix.com gutsy Release.gpg [189B]                      
Ign http://archive.canonical.com gutsy/partner Translation-en_PH                
Get:8 http://ph.archive.ubuntu.com gutsy Release.gpg [191B]                     
Ign http://repository.akirad.net akirad-gutsy/main Translation-en_PH            
Ign http://www.getautomatix.com gutsy/main Translation-en_PH                    
Hit http://ppa.launchpad.net gutsy Release                                      
Ign http://download.tuxfamily.org gutsy/exaile Translation-en_PH                
Ign http://wine.budgetdedicated.com gutsy/main Translation-en_PH                
Hit http://repository.akirad.net akirad-gutsy Release                           
Hit http://www.getautomatix.com gutsy Release                                   
Hit http://archive.canonical.com gutsy Release                                  
Get:9 http://archive.ubuntu.com hardy Release.gpg [191B]                        
Ign http://security.ubuntu.com gutsy-security/main Translation-en_PH            
Ign http://ph.archive.ubuntu.com gutsy/main Translation-en_PH                   
Ign http://archive.ubuntu.com hardy/main Translation-en_PH                      
Ign http://archive.ubuntu.com hardy/restricted Translation-en_PH                
Ign http://archive.ubuntu.com hardy/universe Translation-en_PH                  
Hit http://ppa.launchpad.net gutsy Release                                      
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_PH                
Ign http://ppa.launchpad.net gutsy/main Packages                                
Ign http://ppa.launchpad.net gutsy/main Sources                                 
Ign http://ppa.launchpad.net gutsy/main Packages                                
Hit http://wine.budgetdedicated.com gutsy Release                               
Ign http://ppa.launchpad.net gutsy/main Sources                                 
Get:10 http://download.tuxfamily.org gutsy Release [10.9kB]                     
Hit http://www.getautomatix.com gutsy/main Packages                             
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_PH      
Hit http://repository.akirad.net akirad-gutsy/main Packages                     
Ign http://ph.archive.ubuntu.com gutsy/universe Translation-en_PH               
Hit http://archive.canonical.com gutsy/partner Packages                         
Hit http://archive.ubuntu.com gutsy Release                                     
Hit http://repository.akirad.net akirad-gutsy/main Sources                      
Hit http://ppa.launchpad.net gutsy/main Packages                                
Ign http://wine.budgetdedicated.com gutsy/main Packages                         
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_PH        
Ign http://ph.archive.ubuntu.com gutsy/restricted Translation-en_PH             
Hit http://archive.canonical.com gutsy/partner Sources                          
Hit http://archive.ubuntu.com hardy Release                                     
Get:11 http://download.tuxfamily.org gutsy/exaile Packages [1227B]              
Hit http://wine.budgetdedicated.com gutsy/main Sources                          
Hit http://ppa.launchpad.net gutsy/main Sources                                 
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_PH      
Ign http://ph.archive.ubuntu.com gutsy/multiverse Translation-en_PH             
Hit http://archive.ubuntu.com gutsy/main Sources                                
Hit http://ppa.launchpad.net gutsy/main Packages                                
Hit http://wine.budgetdedicated.com gutsy/main Packages                         
Get:12 http://security.ubuntu.com hardy Release.gpg [191B]                      
Get:13 http://ph.archive.ubuntu.com gutsy-updates Release.gpg [191B]            
Hit http://ppa.launchpad.net gutsy/main Sources                                 
Hit http://security.ubuntu.com gutsy-security Release                           
Hit http://archive.ubuntu.com gutsy/restricted Sources                          
Get:14 http://security.ubuntu.com hardy Release [65.9kB]                        
Ign http://ph.archive.ubuntu.com gutsy-updates/main Translation-en_PH           
Hit http://archive.ubuntu.com hardy/main Packages                               
Ign http://ph.archive.ubuntu.com gutsy-updates/restricted Translation-en_PH     
Hit http://archive.ubuntu.com hardy/restricted Packages                         
Ign http://ph.archive.ubuntu.com gutsy-updates/universe Translation-en_PH       
Hit http://security.ubuntu.com gutsy-security/main Packages                     
Hit http://archive.ubuntu.com hardy/universe Packages                           
Ign http://ph.archive.ubuntu.com gutsy-updates/multiverse Translation-en_PH     
Hit http://security.ubuntu.com gutsy-security/restricted Packages               
Hit http://archive.ubuntu.com hardy/multiverse Packages                         
Get:15 http://ph.archive.ubuntu.com gutsy-proposed Release.gpg [191B]           
Hit http://security.ubuntu.com gutsy-security/universe Packages                 
Ign http://ph.archive.ubuntu.com gutsy-proposed/main Translation-en_PH    
Hit http://security.ubuntu.com gutsy-security/multiverse Packages         
Ign http://ph.archive.ubuntu.com gutsy-proposed/restricted Translation-en_PH
Hit http://security.ubuntu.com gutsy-security/main Sources                
Ign http://ph.archive.ubuntu.com gutsy-proposed/universe Translation-en_PH
Hit http://security.ubuntu.com gutsy-security/restricted Sources                
Ign http://ph.archive.ubuntu.com gutsy-proposed/multiverse Translation-en_PH    
Hit http://security.ubuntu.com gutsy-security/universe Sources            
Get:16 http://ph.archive.ubuntu.com gutsy-backports Release.gpg [191B]    
Hit http://security.ubuntu.com gutsy-security/multiverse Sources          
Ign http://ph.archive.ubuntu.com gutsy-backports/main Translation-en_PH   
Hit http://security.ubuntu.com hardy/main Sources                         
Ign http://ph.archive.ubuntu.com gutsy-backports/restricted Translation-en_PH
Get:17 http://security.ubuntu.com hardy/restricted Sources [1604B]        
Ign http://ph.archive.ubuntu.com gutsy-backports/universe Translation-en_PH     
Hit http://security.ubuntu.com hardy/universe Sources                     
Ign http://ph.archive.ubuntu.com gutsy-backports/multiverse Translation-en_PH
Get:18 http://security.ubuntu.com hardy/multiverse Sources [59.0kB]       
Hit http://ph.archive.ubuntu.com gutsy Release                                  
Hit http://ph.archive.ubuntu.com gutsy-updates Release                          
Hit http://ph.archive.ubuntu.com gutsy-proposed Release                         
Hit http://ph.archive.ubuntu.com gutsy-backports Release                        
Hit http://ph.archive.ubuntu.com gutsy/main Packages                            
Hit http://ph.archive.ubuntu.com gutsy/universe Packages                        
Hit http://ph.archive.ubuntu.com gutsy/restricted Packages                      
Hit http://ph.archive.ubuntu.com gutsy/multiverse Packages                      
Hit http://ph.archive.ubuntu.com gutsy/main Sources                             
Hit http://ph.archive.ubuntu.com gutsy/universe Sources                         
Hit http://ph.archive.ubuntu.com gutsy/restricted Sources                       
Hit http://ph.archive.ubuntu.com gutsy/multiverse Sources                       
Hit http://ph.archive.ubuntu.com gutsy-updates/main Packages                    
Hit http://ph.archive.ubuntu.com gutsy-updates/restricted Packages              
Hit http://ph.archive.ubuntu.com gutsy-updates/universe Packages                
Hit http://ph.archive.ubuntu.com gutsy-updates/multiverse Packages              
Hit http://ph.archive.ubuntu.com gutsy-updates/main Sources
Hit http://ph.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://ph.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://ph.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://ph.archive.ubuntu.com gutsy-proposed/main Packages
Hit http://ph.archive.ubuntu.com gutsy-proposed/restricted Packages
Hit http://ph.archive.ubuntu.com gutsy-proposed/universe Packages
Hit http://ph.archive.ubuntu.com gutsy-proposed/multiverse Packages
Hit http://ph.archive.ubuntu.com gutsy-proposed/main Sources
Hit http://ph.archive.ubuntu.com gutsy-proposed/restricted Sources
Hit http://ph.archive.ubuntu.com gutsy-proposed/universe Sources
Hit http://ph.archive.ubuntu.com gutsy-proposed/multiverse Sources
Hit http://ph.archive.ubuntu.com gutsy-backports/main Packages
Get:19 http://ph.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Hit http://ph.archive.ubuntu.com gutsy-backports/universe Packages        
Hit http://ph.archive.ubuntu.com gutsy-backports/multiverse Packages
Get:20 http://ph.archive.ubuntu.com gutsy-backports/main Sources [7799B]
Hit http://ph.archive.ubuntu.com gutsy-backports/restricted Sources
Hit http://ph.archive.ubuntu.com gutsy-backports/universe Sources
Get:21 http://ph.archive.ubuntu.com gutsy-backports/multiverse Sources [2264B]
Fetched 149kB in 49s (3014B/s) 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  g++-4.1 libphysfs-1.0-0 libsdl-gfx1.2-4 libsmpeg0 libstdc++6-4.1-dev 
The following packages have been automatically kept back:
  audacious-plugins boo d4x-common filezilla-common gdk-imlib11 gnome-bin 
  gnome-libs-data kdebase-bin kdelibs-data kdelibs4c2a libaprutil1 
  libatk1-ruby1.8 libaudid3tag1 libaudio-flac-header-perl libawn0 
  libboost-regex1.34.1 libcairo2-dev libcdio-cdda0 libcurl3 
  libemeraldengine0 libfaad2-0 libgdk-pixbuf2-ruby1.8 libglademm-2.4-1c2a 
  libgladeui-1-7 libglib2-ruby1.8 libgnome32 libgnomesupport0 libgnomeui32 
  libgnorba27 libgnorbagtk0 libgnutlsxx13 libgtk1.2 libgtk2-ruby1.8 
  libimlib2 libk3b2 libmono-cairo2.0-cil libmono-system-web1.0-cil libofa0 
  liborbit0 libpango1-ruby1.8 libpango1.0-dev libpq5 libquicktime1 libsvn1 
  libtaglib2.0-cil libtunepimp5 libungif4g libunicode-string-perl 
  libwxgtk2.6-0 libwxgtk2.8-0 libx11-dev libxine1-console libxine1-ffmpeg 
  libxine1-gnome libxine1-misc-plugins libxine1-x libxml-libxml-common-perl 
  libzvt2 mencoder mplayer python-compizconfig python-soya python-wxgtk2.6 
  python-wxversion rpm transmission-common vcdimager vlc-nox 
  xchat-gnome-common xsu xulrunner-1.9 
The following packages have been kept back:
  apt apt-utils aptitude at-spi audacious avant-window-navigator banshee 
  bluefish bluez-gnome bluez-utils bogofilter-bdb brltty brltty-x11 
  bug-buddy capplets-data compiz compiz-core compiz-fusion-plugins-extra 
  compiz-fusion-plugins-main compiz-gnome compiz-plugins 
  compizconfig-settings-manager cupsys cupsys-bsd cupsys-client 
  cupsys-driver-gutenprint d4x debhelper deskbar-applet dpkg dpkg-dev ekiga 
  emerald eog epiphany-browser-data epiphany-gecko evince evolution 
  evolution-common evolution-data-server evolution-data-server-common 
  evolution-exchange evolution-plugins evolution-webcal exaile f-spot faad 
  fast-user-switch-applet file-roller filezilla firefox firefox-3.0 
  firefox-gnome-support flashplugin-nonfree galeon gconf-editor gconf2 
  gconf2-common gdm gedit gedit-common gimp gimp-data gimp-python gksu 
  gnome-app-install gnome-applets gnome-applets-data gnome-cards-data 
  gnome-control-center gnome-games gnome-games-data gnome-keyring gnome-mag 
  gnome-media gnome-mount gnome-nettool gnome-orca gnome-panel 
  gnome-panel-data gnome-power-manager gnome-screensaver gnome-session 
  gnome-system-monitor gnome-system-tools gnome-terminal 
  gnome-terminal-data gnome-utils gnome-volume-manager gnupg gparted 
  gphpedit grub gstreamer0.10-plugins-bad 
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-good 
  gstreamer0.10-plugins-ugly gstreamer0.10-schroedinger gstreamer0.10-x 
  gthumb gtk2-engines gtk2-engines-pixbuf gtkhtml3.14 gtkpod-aac gucharmap 
  gwget hal hal-cups-utils hal-info hpijs hplip hplip-data iproute k3d kino 
  language-support-en lastfm lftp libatspi1.0-0 libbonoboui2-0 
  libbonoboui2-common libcairo2 libcamel1.2-10 libcupsimage2 libcupsys2 
  libcurl3-gnutls libebook1.2-9 libecal1.2-7 libedata-book1.2-2 
  libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2 
  libegroupwise1.2-13 libexchange-storage1.2-3 libgail-common 
  libgail-gnome-module libgail18 libgconf2-4 libgdl-1-0 libgdl-1-common 
  libgdl-gnome-1-0 libgimp2.0 libgksu2-0 libgnome-keyring0 libgnome-speech7 
  libgnome-window-settings1 libgnome2-canvas-perl libgnomecanvas2-0 
  libgnomecups1.0-1 libgnomekbd-common libgnomeprint2.2-0 
  libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common 
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common 
  libgnomevfs2-extra libgnutls-dev libgnutls13 libgpod-common libgs8 
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtk2.0-common libgtk2.0-dev 
  libgtkhtml2-0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 
  libgtksourceview2.0-common libgtkspell0 libgucharmap6 libgutenprintui2-1 
  libhsqldb-java libipod-cil libipodui-cil liblocale-gettext-perl 
  libmetacity0 libmono-corlib1.0-cil libmono-corlib2.0-cil 
  libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil 
  libmono-sqlite2.0-cil libmono-system-data2.0-cil 
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil 
  libmono2.0-cil libnss3-0d libopal-2.2 libpam-modules libpanel-applet2-0 
  libpango1.0-0 libperl5.8 libpoppler-glib2 libpurple0 librarian0 
  librsvg2-2 librsvg2-common libsasl2-2 libsasl2-modules libsdl1.2debian 
  libsdl1.2debian-alsa libsmbclient libsoup2.2-8 libtracker-gtk0 
  libtunepimp5-mp3 libvcdinfo0 libvte-common libvte9 libwnck-common 
  libwnck22 libx11-6 libxine1 libxine1-plugins libxul-common libxul0d 
  linux-generic linux-headers-generic linux-image-generic 
  linux-restricted-modules linux-restricted-modules-generic metacity 
  metacity-common mono-common mono-gac mono-jit mono-runtime nautilus 
  nautilus-cd-burner nautilus-data nautilus-sendto netcat 
  network-manager-gnome notification-daemon ntfsprogs openmovieeditor 
  openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-help-en-us openoffice.org-impress 
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math 
  openoffice.org-style-human openoffice.org-writer perl perl-base 
  perl-modules pidgin pidgin-data pitivi procmeter3 python-apt python-cups 
  python-glade2 python-gnome2 python-gnome2-desktop python-gnome2-extras 
  python-gnomecanvas python-gobject python-gtk2 python-gtkhtml2 
  python-notify python-uno python-vte python2.5 python2.5-minimal rhythmbox 
  rutilt samba-common scim scim-gtk2-immodule scim-modules-socket 
  scim-modules-table scim-tables-additional sensors-applet smbclient 
  sound-juicer sox splix ssh-askpass-gnome subversion synaptic 
  system-tools-backends tomboy totem totem-mozilla totem-xine tracker 
  tracker-search-tool transmission-gtk ttf-gentium ubuntu-artwork 
  ubuntu-standard update-manager update-manager-core update-notifier vino 
  vlc wine wvdial xbase-clients xchat-gnome xmms xorg xsane xsane-common 
  xserver-xorg xserver-xorg-core xserver-xorg-input-all 
  xserver-xorg-input-elographics xserver-xorg-input-evdev 
  xserver-xorg-input-kbd xserver-xorg-input-mouse 
  xserver-xorg-input-synaptics xserver-xorg-input-wacom 
  xserver-xorg-video-all xserver-xorg-video-amd xserver-xorg-video-apm 
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips 
  xserver-xorg-video-cirrus xserver-xorg-video-cyrix 
  xserver-xorg-video-dummy xserver-xorg-video-fbdev 
  xserver-xorg-video-glint xserver-xorg-video-i128 xserver-xorg-video-i740 
  xserver-xorg-video-imstt xserver-xorg-video-intel xserver-xorg-video-mga 
  xserver-xorg-video-neomagic xserver-xorg-video-newport 
  xserver-xorg-video-nsc xserver-xorg-video-nv xserver-xorg-video-rendition 
  xserver-xorg-video-s3 xserver-xorg-video-s3virge 
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion 
  xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx 
  xserver-xorg-video-tga xserver-xorg-video-trident 
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa 
  xserver-xorg-video-vga xserver-xorg-video-via xserver-xorg-video-vmware 
  xserver-xorg-video-voodoo xutils yelp zenity 
The following packages will be upgraded:
  915resolution adduser agave alacarte alien alsa-base alsa-oss alsa-utils 
  app-install-data app-install-data-commercial apparmor apparmor-utils 
  apport apport-gtk apturl arj aspell avahi-autoipd avahi-daemon 
  awn-manager base-files base-passwd bash bc bind9-host binutils 
  binutils-static bittornado bittornado-gui bittorrent bkhive blt 
  bluez-cups bogofilter bogofilter-common bsdmainutils bsdutils bsh 
  busybox-initramfs bzip2 cdparanoia cdrdao cli-common command-not-found 
  command-not-found-data console-setup console-terminus console-tools 
  consolekit coreutils cpio cpp cpp-4.1 cpp-4.2 cups-pdf cupsys-common dash 
  dbus dc dcraw debconf debconf-i18n debianutils defoma desktop-file-utils 
  devede dhcdbd dhcp3-client dhcp3-common dictionaries-common discover1 
  discover1-data disksearch dnsutils doc-base docbook-xml dosfstools 
  dvd+rw-tools e2fslibs e2fsprogs eject epiphany-browser esound-common 
  espeak espeak-data ethtool faac fakeroot feisty-gdm-themes ffmpeg file 
  findutils firefox-themes-ubuntu fontconfig fontconfig-config foo2zjs 
  foomatic-db foomatic-filters freeglut3 fuse-utils g++ g++-4.2 
  galeon-common gamin gcalctool gcc gcc-3.3-base gcc-4.1 gcc-4.1-base 
  gcc-4.2 gcc-4.2-base gcj-4.2-base gdb gdebi gdebi-core gdk-imlib1 
  genisoimage gettext gettext-base ghostscript ghostscript-x gij gij-4.2 
  glade-3 gnome-about gnome-accessibility-themes gnome-btdownload 
  gnome-desktop-data gnome-doc-utils gnome-icon-theme gnome-media-common 
  gnome-menus gnome-themes gnome-user-guide gom gpgv grep groff-base 
  gsfonts gsfonts-x11 gstreamer-tools gstreamer0.10-alsa gstreamer0.10-esd 
  gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 
  gstreamer0.10-fluendo-mpegdemux gstreamer0.10-gnomevfs 
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps 
  gstreamer0.10-plugins-farsight gstreamer0.10-sdl gstreamer0.10-tools 
  gtk-recordmydesktop gtorrent-viewer guidance-backends gutsy-wallpapers 
  gzip hdparm hostname hubackup human-icon-theme hwdb-client-common 
  hwdb-client-gnome imlib-base info initramfs-tools initscripts iptables 
  iputils-arping iputils-ping iputils-tracepath iso-codes java-common 
  klibc-utils klogd kubuntu-restricted-extras language-pack-en 
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base 
  language-selector language-selector-common laptop-mode-tools less libaa1 
  libacl1 libao2 libapr1 libarchive-tar-perl libart-2.0-2 libart2 
  libart2.0-cil libarts1c2a libartsc0 libasound2 libaspell15 libatk1.0-0 
  libatk1.0-dev libattr1 libaudclient1 libaudio-wav-perl libaudio2 
  libaudiofile0 libavahi-client3 libavahi-common-data libavahi-common3 
  libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1 libavahi-qt3-1 
  libavcodec1d libavformat1d libavutil1d libbind9-30 libblkid1 
  libbluetooth2 libbonobo2-0 libbonobo2-common libboost-date-time1.34.1 
  libboost-filesystem1.34.1 libboost-thread1.34.1 libbtctl4 libbz2-1.0 
  libc6 libc6-dev libc6-i686 libcaca0 libcairo-perl libcairomm-1.0-1 
  libcal3d12 libcdparanoia0 libcomerr2 libcompizconfig0 
  libcompress-raw-zlib-perl libcompress-zlib-perl libconsole libcucul0 
  libdatrie0 libdb4.2 libdb4.3 libdb4.4 libdb4.5 libdbus-1-3 libdc1394-13 
  libdecoration0 libdeskbar-tracker libdevmapper1.02.1 libdiscover1 
  libdjvulibre15 libdns32 libdvdread3 libedit2 libeel2-data libenchant1c2a 
  libesd-alsa0 libespeak1 libexif12 libexpat1 libexpat1-dev libfaac0 
  libfile-basedir-perl libfile-desktopentry-perl libflac++6 libflac8 
  libfltk1.1 libfontconfig1 libfontconfig1-dev libfreebob0 libfribidi0 
  libfuse2 libgamin0 libgc1c2 libgcc1 libgcj-bc libgcj-common libgcj8-1 
  libgconf2.0-cil libgconfmm-2.6-1c2 libgcrypt11 libgcrypt11-dev libgda2-3 
  libgda2-common libgksu1.2-1 libgl1-mesa-dri libgl1-mesa-glx 
  libglade2.0-cil libglew1.4 libglib-perl libglib2.0-0 libglib2.0-cil 
  libglib2.0-dev libglibmm-2.4-1c2a libglu1-mesa libgmime-2.0-2 
  libgmime2.2-cil libgnome-desktop-2 libgnome-mag2 libgnome-media0 
  libgnome-menu2 libgnome-vfs2.0-cil libgnome2-0 libgnome2-common 
  libgnome2-vfs-perl libgnome2.0-cil libgnomecanvas2-common 
  libgnomevfs2-bin libgomp1 libgpg-error-dev libgpg-error0 libgphoto2-2 
  libgphoto2-port0 libgpmg1 libgsf-1-114 libgsf-1-common libgsm1 
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk1.2-common 
  libgtk2-perl libgtk2-ruby libgtkhtml2.0-cil libgtop2-7 libgtop2-common 
  libgutenprint2 libhal-storage1 libhal1 libhunspell-1.1-0 libice-dev 
  libice6 libidl0 libidn11 libieee1284-3 libio-compress-base-perl 
  libio-compress-zlib-perl libisc32 libisccc30 libisccfg30 libiw29 libjack0 
  libjaxp1.3-java libjline-java libkeyutils1 libklibc libkpathsea4 libkrb53 
  liblcms1 libldap2 liblircclient0 libltdl3 liblua50 liblualib50 liblwres30 
  libmagic1 libmms0 libmodplug0c2 libmono-cairo1.0-cil 
  libmono-data-tds1.0-cil libmono-security1.0-cil libmono-sharpzip0.84-cil 
  libmono-system-data1.0-cil libmono0 libmono1.0-cil libmowgli1 libmozjs0d 
  libmp3-info-perl libmp4v2-0 libnautilus-burn4 libnautilus-extension1 
  libncurses5 libncursesw5 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil 
  libneon26 libneon27-gnutls libnet-dbus-perl libnewt0.52 libnl1-pre6 
  libnm-glib0 libnm-util0 libnspr4-0d libnss-mdns libntfs-3g16 
  libode0debian1 libogg0 libopenal0a liborbit2 libpam-gnome-keyring 
  libpam-runtime libpam0g libpango1.0-common libpaper-utils libpaper1 
  libpcap0.8 libpcre3 libpcrecpp0 libpisock9 libpisync0 libpng12-0 
  libpng12-dev libpoppler2 libpostproc1d libpulse0 libqt3-mt 
  libqt3-mt-sqlite libqt4-core libqt4-gui libraw1394-8 librecode0 
  librpc-xml-perl librsvg2.0-cil libruby1.8 libsamplerate0 libsane 
  libscim8c2a libscrollkeeper0 libsdl-image1.2 libsdl-mixer1.2 
  libsdl-net1.2 libselinux1 libsensors3 libsepol1 libshout3 libslang2 
  libslp1 libsnmp-base libsqlite3-0 libss2 libssl0.9.8 libstdc++5 
  libstdc++6 libstdc++6-4.2-dev libsuperlu3 libsvg1 libswscale1d libt1-5 
  libtag1c2a libtagc0 libtasn1-3 libtasn1-3-dev libtheora0 
  libtrackerclient0 libusb-0.1-4 libusplash0 libuuid1 libvisual-0.4-0 
  libvlc0 libvolume-id0 libvorbis0a libvorbisenc2 libvorbisfile3 libwpd8c2a 
  libwpg-0.1-1 libwps-0.1-1 libwww-perl libwxbase2.6-0 libwxbase2.8-0 
  libx11-data libxalan2-java libxaw7 libxcb-shape0 libxcb-shm0 libxcb-xv0 
  libxcb1 libxcomposite-dev libxcomposite1 libxcursor-dev libxcursor1 
  libxerces2-java libxfont1 libxi-dev libxi6 libxklavier11 libxml-dev 
  libxml-libxml-perl libxml-sax-perl libxml-simple-perl libxml-twig-perl 
  libxml1 libxml2 libxml2-dev libxml2-utils libxmu6 libxmuu1 libxosd2 
  libxpm4 libxrandr-dev libxrandr2 libxrender-dev libxrender1 libxslt1.1 
  libxtst6 libxxf86dga1 lincity-ng-data linux-libc-dev 
  linux-restricted-modules-common linux-sound-base login lsb-base 
  lsb-release lshw lsof ltrace makedev man-db manpages mcpp mesa-utils 
  mktemp module-assistant module-init-tools mount 
  mozilla-firefox-locale-en-gb mozilla-mplayer mpg321 msttcorefonts nano 
  ncurses-base ncurses-bin net-tools netbase network-manager nicotine 
  ntfs-3g ntp ntpdate nvidia-kernel-common openarena openarena-data 
  openoffice.org-java-common openoffice.org-l10n-common openprinting-ppds 
  openssh-client openssl ophcrack p7zip p7zip-full passwd pciutils 
  pcmciautils po-debconf poppler-utils popularity-contest powertop 
  pppoeconf procps psmisc python-2play python-apport python-bittorrent 
  python-central python-dbus python-gconf python-gdbm python-gmenu 
  python-gst0.10 python-imaging python-imaging-tk python-launchpad-bugs 
  python-libxml2 python-numeric python-problem-report python-pyorbit 
  python-pysqlite2 python-software-properties python-support python-tk 
  python-xml python-zopeinterface rar rdesktop readahead recordmydesktop 
  rss-glx rsync ruby ruby1.8 samdump2 scorched3d-data screen scrollkeeper 
  sed serpentine shared-mime-info slocate software-properties-gtk sqlite3 
  ssl-cert startup-tasks stellarium-data strace sudo sun-java5-bin 
  sun-java5-jre sun-java6-bin sun-java6-jre sun-java6-plugin 
  supertux-data-stable supertux-stable sysklogd system-services sysv-rc 
  sysvutils tango-icon-theme tar tasksel tasksel-data tcl8.4 tcpdump tk8.4 
  toshset tsclient ttf-arabeyes ttf-dejavu ttf-dejavu-core ttf-dejavu-extra 
  ttf-essays1743 ttf-fifthhorseman-dkg-handwriting ttf-georgewilliams 
  ttf-inconsolata ttf-isabella ttf-mgopen ttf-opensymbol ttf-staypuft 
  ttf-summersby ttf-thai-tlwg ttf-tuffy ttf-ubuntu-title tzdata ubufox 
  ubuntu-docs ubuntu-keyring ubuntu-minimal ubuntu-restricted-extras ucf 
  udev unace unattended-upgrades unrar update-inetd update-notifier-common 
  upstart upstart-compat-sysv upstart-logd usbutils usplash util-linux 
  util-linux-locales vbetool vim-common vim-tiny volumeid vorbis-tools 
  wamerican wbritish whiptail whois wireless-tools wodim x-ttcidfont-conf 
  x11-common x11proto-composite-dev x11proto-core-dev x11proto-render-dev 
  xauth xdg-user-dirs xdg-user-dirs-gtk xdg-utils xfonts-100dpi 
  xfonts-75dpi xfonts-base xfonts-encodings xfonts-intl-european 
  xfonts-utils xinit xkb-data xpdf-common xpdf-reader xpmutils 
  xscreensaver-data xscreensaver-gl xserver-xorg-video-i810 xsltproc 
  xtrans-dev xubuntu-restricted-extras xulrunner-gnome-support zim zlib1g 
  zlib1g-dev 
688 packages upgraded, 0 newly installed, 5 to remove and 440 not upgraded.
Need to get 719MB of archives. After unpacking 7205kB will be used.
Do you want to continue? [Y/n/?] 
```

**I also tried installing flashplugin-nonfree, this is what disturbs me.. large download...**

```
karlo@karlo-laptop:~$ sudo aptitude install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libc6-dev libc6-i686 libgnutls-dev 
The following packages are unused and will be REMOVED:
  libphysfs-1.0-0 libsdl-gfx1.2-4 libsdl-net1.2 lincity-ng-data 
  scorched3d-data stellarium-data 
The following packages have been automatically kept back:
  audacious-plugins awn-manager binutils-static bittornado bkhive blt boo 
  cpp-4.2 d4x-common filezilla-common g++-4.1 g++-4.2 galeon-common 
  gcc-3.3-base gcc-4.2 gdk-imlib1 gdk-imlib11 gettext gnome-bin 
  gnome-libs-data imlib-base java-common kdebase-bin kdelibs-data 
  kdelibs4c2a libapr1 libaprutil1 libart2 libarts1c2a libartsc0 
  libatk1-ruby1.8 libatk1.0-dev libaudclient1 libaudid3tag1 
  libaudio-flac-header-perl libaudio-wav-perl libaudio2 libavahi-qt3-1 
  libavcodec1d libavformat1d libavutil1d libawn0 libboost-date-time1.34.1 
  libboost-filesystem1.34.1 libboost-regex1.34.1 libboost-thread1.34.1 
  libbtctl4 libcairo2-dev libcal3d12 libcdio-cdda0 
  libcompress-raw-zlib-perl libcompress-zlib-perl libcurl3 libdc1394-13 
  libemeraldengine0 libexpat1-dev libfaac0 libfaad2-0 libfile-basedir-perl 
  libfile-desktopentry-perl libflac++6 libfltk1.1 libfontconfig1-dev 
  libfreebob0 libgconfmm-2.6-1c2 libgcrypt11-dev libgda2-3 libgda2-common 
  libgdk-pixbuf2-ruby1.8 libglademm-2.4-1c2a libgladeui-1-7 
  libglib2-ruby1.8 libgnome32 libgnomesupport0 libgnomeui32 libgnorba27 
  libgnorbagtk0 libgnutlsxx13 libgomp1 libgpg-error-dev libgsm1 libgtk1.2 
  libgtk1.2-common libgtk2-ruby libgtk2-ruby1.8 libice-dev libimlib2 
  libio-compress-base-perl libio-compress-zlib-perl libjack0 libk3b2 
  liblua50 liblualib50 libmms0 libmodplug0c2 libmono-cairo2.0-cil 
  libmono-data-tds1.0-cil libmono-security1.0-cil libmono-sharpzip0.84-cil 
  libmono-system-data1.0-cil libmono-system-web1.0-cil libmono1.0-cil 
  libmowgli1 libmp3-info-perl libmp4v2-0 libneon27-gnutls libode0debian1 
  libofa0 liborbit0 libpango1-ruby1.8 libpango1.0-dev libpng12-dev 
  libpostproc1d libpq5 libqt3-mt libqt3-mt-sqlite libqt4-core libqt4-gui 
  libquicktime1 libruby1.8 libsamplerate0 libsdl-image1.2 libsdl-mixer1.2 
  libstdc++6-4.1-dev libsuperlu3 libsvn1 libswscale1d libt1-5 libtagc0 
  libtaglib2.0-cil libtasn1-3-dev libtunepimp5 libungif4g 
  libunicode-string-perl libvlc0 libwxbase2.6-0 libwxbase2.8-0 
  libwxgtk2.6-0 libwxgtk2.8-0 libx11-dev libxcb-shape0 libxcb-shm0 
  libxcb-xv0 libxcb1 libxcomposite-dev libxcursor-dev libxi-dev 
  libxine1-console libxine1-ffmpeg libxine1-gnome libxine1-misc-plugins 
  libxine1-x libxml-libxml-common-perl libxml-libxml-perl libxml-sax-perl 
  libxml-simple-perl libxml1 libxosd2 libxrandr-dev libxrender-dev libzvt2 
  linux-libc-dev linux-restricted-modules-common mencoder mplayer 
  nvidia-kernel-common openarena-data po-debconf python-2play 
  python-compizconfig python-imaging python-imaging-tk python-pysqlite2 
  python-soya python-tk python-wxgtk2.6 python-wxversion 
  python-zopeinterface recordmydesktop rpm ruby ruby1.8 samdump2 
  sun-java5-bin sun-java6-bin sun-java6-jre supertux-data-stable 
  tango-icon-theme tcl8.4 tk8.4 transmission-common ttf-dejavu-extra 
  vcdimager vlc-nox x11proto-composite-dev x11proto-core-dev 
  x11proto-render-dev xchat-gnome-common xpdf-common xsu xtrans-dev 
  xulrunner-1.9 
The following NEW packages will be automatically installed:
  libflashsupport libopencdk10 
The following packages have been kept back:
  915resolution adduser agave alacarte alien alsa-base alsa-oss alsa-utils 
  app-install-data app-install-data-commercial apparmor apparmor-utils 
  apport apport-gtk apt apt-utils aptitude apturl arj aspell at-spi 
  audacious avahi-autoipd avahi-daemon avant-window-navigator banshee 
  base-files base-passwd bash bc bind9-host binutils bittornado-gui 
  bittorrent bluefish bluez-cups bluez-gnome bluez-utils bogofilter 
  bogofilter-bdb bogofilter-common brltty brltty-x11 bsdmainutils bsdutils 
  bsh bug-buddy busybox-initramfs bzip2 capplets-data cdparanoia cdrdao 
  cli-common command-not-found command-not-found-data compiz compiz-core 
  compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome 
  compiz-plugins compizconfig-settings-manager console-setup 
  console-terminus console-tools consolekit coreutils cpio cpp cpp-4.1 
  cups-pdf cupsys cupsys-bsd cupsys-client cupsys-common 
  cupsys-driver-gutenprint d4x dash dbus dc dcraw debconf debconf-i18n 
  debhelper debianutils defoma deskbar-applet desktop-file-utils devede 
  dhcdbd dhcp3-client dhcp3-common dictionaries-common discover1 
  discover1-data disksearch dnsutils doc-base docbook-xml dosfstools dpkg 
  dpkg-dev dvd+rw-tools e2fslibs e2fsprogs eject ekiga emerald eog 
  epiphany-browser epiphany-browser-data epiphany-gecko esound-common 
  espeak espeak-data ethtool evince evolution evolution-common 
  evolution-data-server evolution-data-server-common evolution-exchange 
  evolution-plugins evolution-webcal exaile f-spot faac faad fakeroot 
  fast-user-switch-applet feisty-gdm-themes ffmpeg file file-roller 
  filezilla findutils firefox firefox-3.0 firefox-gnome-support 
  firefox-themes-ubuntu fontconfig fontconfig-config foo2zjs foomatic-db 
  foomatic-filters freeglut3 fuse-utils g++ galeon gamin gcalctool gcc 
  gcc-4.1 gcc-4.1-base gcc-4.2-base gcj-4.2-base gconf-editor gconf2 
  gconf2-common gdb gdebi gdebi-core gdm gedit gedit-common genisoimage 
  gettext-base ghostscript ghostscript-x gij gij-4.2 gimp gimp-data 
  gimp-python gksu glade-3 gnome-about gnome-accessibility-themes 
  gnome-app-install gnome-applets gnome-applets-data gnome-btdownload 
  gnome-cards-data gnome-control-center gnome-desktop-data gnome-doc-utils 
  gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag 
  gnome-media gnome-media-common gnome-menus gnome-mount gnome-nettool 
  gnome-orca gnome-panel gnome-panel-data gnome-power-manager 
  gnome-screensaver gnome-session gnome-system-monitor gnome-system-tools 
  gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide 
  gnome-utils gnome-volume-manager gnupg gom gparted gpgv gphpedit grep 
  groff-base grub gsfonts gsfonts-x11 gstreamer-tools gstreamer0.10-alsa 
  gstreamer0.10-esd gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 
  gstreamer0.10-fluendo-mpegdemux gstreamer0.10-gnomevfs 
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse 
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps 
  gstreamer0.10-plugins-farsight gstreamer0.10-plugins-good 
  gstreamer0.10-plugins-ugly gstreamer0.10-schroedinger gstreamer0.10-sdl 
  gstreamer0.10-tools gstreamer0.10-x gthumb gtk-recordmydesktop 
  gtk2-engines gtk2-engines-pixbuf gtkhtml3.14 gtkpod-aac gtorrent-viewer 
  gucharmap guidance-backends gutsy-wallpapers gwget gzip hal 
  hal-cups-utils hal-info hdparm hostname hpijs hplip hplip-data hubackup 
  human-icon-theme hwdb-client-common hwdb-client-gnome info 
  initramfs-tools initscripts iproute iptables iputils-arping iputils-ping 
  iputils-tracepath iso-codes k3d kino klibc-utils klogd 
  kubuntu-restricted-extras language-pack-en language-pack-en-base 
  language-pack-gnome-en language-pack-gnome-en-base language-selector 
  language-selector-common language-support-en laptop-mode-tools lastfm 
  less lftp libaa1 libacl1 libao2 libarchive-tar-perl libart-2.0-2 
  libart2.0-cil libasound2 libaspell15 libatk1.0-0 libatspi1.0-0 libattr1 
  libaudiofile0 libavahi-client3 libavahi-common-data libavahi-common3 
  libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1 libbind9-30 
  libblkid1 libbluetooth2 libbonobo2-0 libbonobo2-common libbonoboui2-0 
  libbonoboui2-common libbz2-1.0 libcaca0 libcairo-perl libcairo2 
  libcairomm-1.0-1 libcamel1.2-10 libcdparanoia0 libcomerr2 
  libcompizconfig0 libconsole libcucul0 libcupsimage2 libcupsys2 
  libcurl3-gnutls libdatrie0 libdb4.2 libdb4.3 libdb4.4 libdb4.5 
  libdbus-1-3 libdecoration0 libdeskbar-tracker libdevmapper1.02.1 
  libdiscover1 libdjvulibre15 libdns32 libdvdread3 libebook1.2-9 
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 
  libedataserverui1.2-8 libedit2 libeel2-2 libeel2-data libegroupwise1.2-13 
  libenchant1c2a libesd-alsa0 libespeak1 libexchange-storage1.2-3 libexif12 
  libexpat1 libflac8 libfontconfig1 libfribidi0 libfuse2 libgail-common 
  libgail-gnome-module libgail18 libgamin0 libgc1c2 libgcc1 libgcj-bc 
  libgcj-common libgcj8-1 libgconf2-4 libgconf2.0-cil libgcrypt11 
  libgdl-1-0 libgdl-1-common libgdl-gnome-1-0 libgimp2.0 libgksu1.2-1 
  libgksu2-0 libgl1-mesa-dri libgl1-mesa-glx libglade2.0-cil libglew1.4 
  libglib-perl libglib2.0-0 libglib2.0-cil libglib2.0-dev 
  libglibmm-2.4-1c2a libglu1-mesa libgmime-2.0-2 libgmime2.2-cil 
  libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-media0 
  libgnome-menu2 libgnome-speech7 libgnome-vfs2.0-cil 
  libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl 
  libgnome2-common libgnome2-vfs-perl libgnome2.0-cil libgnomecanvas2-0 
  libgnomecanvas2-common libgnomecups1.0-1 libgnomekbd-common 
  libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 
  libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgpg-error0 
  libgphoto2-2 libgphoto2-port0 libgpmg1 libgpod-common libgs8 libgsf-1-114 
  libgsf-1-common libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 
  libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtk2.0-common 
  libgtk2.0-dev libgtkhtml2-0 libgtkhtml2.0-cil libgtkhtml3.14-19 
  libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common 
  libgtkspell0 libgtop2-7 libgtop2-common libgucharmap6 libgutenprint2 
  libgutenprintui2-1 libhal-storage1 libhal1 libhsqldb-java 
  libhunspell-1.1-0 libice6 libidl0 libidn11 libieee1284-3 libipod-cil 
  libipodui-cil libisc32 libisccc30 libisccfg30 libiw29 libjaxp1.3-java 
  libjline-java libkeyutils1 libklibc libkpathsea4 libkrb53 liblcms1 
  libldap2 liblircclient0 liblocale-gettext-perl libltdl3 liblwres30 
  libmagic1 libmetacity0 libmono-cairo1.0-cil libmono-corlib1.0-cil 
  libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil 
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil 
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil 
  libmono0 libmono2.0-cil libmozjs0d libnautilus-burn4 
  libnautilus-extension1 libncurses5 libncursesw5 libndesk-dbus-glib1.0-cil 
  libndesk-dbus1.0-cil libneon26 libnet-dbus-perl libnewt0.52 libnl1-pre6 
  libnm-glib0 libnm-util0 libnspr4-0d libnss-mdns libnss3-0d libntfs-3g16 
  libogg0 libopal-2.2 libopenal0a liborbit2 libpam-gnome-keyring 
  libpam-modules libpam-runtime libpam0g libpanel-applet2-0 libpango1.0-0 
  libpango1.0-common libpaper-utils libpaper1 libpcap0.8 libpcre3 
  libpcrecpp0 libperl5.8 libpisock9 libpisync0 libpng12-0 libpoppler-glib2 
  libpoppler2 libpurple0 librarian0 libraw1394-8 librecode0 librpc-xml-perl 
  librsvg2-2 librsvg2-common librsvg2.0-cil libsane libsasl2-2 
  libsasl2-modules libscim8c2a libscrollkeeper0 libsdl1.2debian 
  libsdl1.2debian-alsa libselinux1 libsensors3 libsepol1 libshout3 
  libslang2 libslp1 libsmbclient libsnmp-base libsoup2.2-8 libsqlite3-0 
  libss2 libssl0.9.8 libstdc++5 libstdc++6 libstdc++6-4.2-dev libsvg1 
  libtag1c2a libtasn1-3 libtheora0 libtracker-gtk0 libtrackerclient0 
  libtunepimp5-mp3 libusb-0.1-4 libusplash0 libuuid1 libvcdinfo0 
  libvisual-0.4-0 libvolume-id0 libvorbis0a libvorbisenc2 libvorbisfile3 
  libvte-common libvte9 libwnck-common libwnck22 libwpd8c2a libwpg-0.1-1 
  libwps-0.1-1 libwww-perl libx11-6 libx11-data libxalan2-java libxaw7 
  libxcomposite1 libxcursor1 libxerces2-java libxfont1 libxi6 libxine1 
  libxine1-plugins libxklavier11 libxml-dev libxml-twig-perl libxml2 
  libxml2-dev libxml2-utils libxmu6 libxmuu1 libxpm4 libxrandr2 libxrender1 
  libxslt1.1 libxtst6 libxul-common libxul0d libxxf86dga1 linux-generic 
  linux-headers-generic linux-image-generic linux-restricted-modules 
  linux-restricted-modules-generic linux-sound-base login lsb-base 
  lsb-release lshw lsof ltrace makedev man-db manpages mcpp mesa-utils 
  metacity metacity-common mktemp module-assistant module-init-tools 
  mono-common mono-gac mono-jit mono-runtime mount 
  mozilla-firefox-locale-en-gb mozilla-mplayer mpg321 msttcorefonts nano 
  nautilus nautilus-cd-burner nautilus-data nautilus-sendto ncurses-base 
  ncurses-bin net-tools netbase netcat network-manager 
  network-manager-gnome nicotine notification-daemon ntfs-3g ntfsprogs ntp 
  ntpdate openarena openmovieeditor openoffice.org openoffice.org-base 
  openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress 
  openoffice.org-java-common openoffice.org-l10n-common 
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math 
  openoffice.org-style-human openoffice.org-writer openprinting-ppds 
  openssh-client openssl ophcrack p7zip p7zip-full passwd pciutils 
  pcmciautils perl perl-base perl-modules pidgin pidgin-data pitivi 
  poppler-utils popularity-contest powertop pppoeconf procmeter3 procps 
  psmisc python-apport python-apt python-bittorrent python-central 
  python-cups python-dbus python-gconf python-gdbm python-glade2 
  python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras 
  python-gnomecanvas python-gobject python-gst0.10 python-gtk2 
  python-gtkhtml2 python-launchpad-bugs python-libxml2 python-notify 
  python-numeric python-problem-report python-pyorbit 
  python-software-properties python-support python-uno python-vte 
  python-xml python2.5 python2.5-minimal rar rdesktop readahead rhythmbox 
  rss-glx rsync rutilt samba-common scim scim-gtk2-immodule 
  scim-modules-socket scim-modules-table scim-tables-additional screen 
  scrollkeeper sed sensors-applet serpentine shared-mime-info slocate 
  smbclient software-properties-gtk sound-juicer sox splix sqlite3 
  ssh-askpass-gnome ssl-cert startup-tasks strace subversion sudo 
  sun-java5-jre sun-java6-plugin supertux-stable synaptic sysklogd 
  system-services system-tools-backends sysv-rc sysvutils tar tasksel 
  tasksel-data tcpdump tomboy toshset totem totem-mozilla totem-xine 
  tracker tracker-search-tool transmission-gtk tsclient ttf-arabeyes 
  ttf-dejavu ttf-dejavu-core ttf-essays1743 
  ttf-fifthhorseman-dkg-handwriting ttf-gentium ttf-georgewilliams 
  ttf-inconsolata ttf-isabella ttf-mgopen ttf-opensymbol ttf-staypuft 
  ttf-summersby ttf-thai-tlwg ttf-tuffy ttf-ubuntu-title tzdata ubufox 
  ubuntu-artwork ubuntu-docs ubuntu-keyring ubuntu-minimal 
  ubuntu-restricted-extras ubuntu-standard ucf udev unace 
  unattended-upgrades unrar update-inetd update-manager update-manager-core 
  update-notifier update-notifier-common upstart upstart-compat-sysv 
  upstart-logd usbutils usplash util-linux util-linux-locales vbetool 
  vim-common vim-tiny vino vlc volumeid vorbis-tools wamerican wbritish 
  whiptail whois wine wireless-tools wodim wvdial x-ttcidfont-conf 
  x11-common xauth xbase-clients xchat-gnome xdg-user-dirs 
  xdg-user-dirs-gtk xdg-utils xfonts-100dpi xfonts-75dpi xfonts-base 
  xfonts-encodings xfonts-intl-european xfonts-utils xinit xkb-data xmms 
  xorg xpdf-reader xpmutils xsane xsane-common xscreensaver-data 
  xscreensaver-gl xserver-xorg xserver-xorg-core xserver-xorg-input-all 
  xserver-xorg-input-elographics xserver-xorg-input-evdev 
  xserver-xorg-input-kbd xserver-xorg-input-mouse 
  xserver-xorg-input-synaptics xserver-xorg-input-wacom 
  xserver-xorg-video-all xserver-xorg-video-amd xserver-xorg-video-apm 
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips 
  xserver-xorg-video-cirrus xserver-xorg-video-cyrix 
  xserver-xorg-video-dummy xserver-xorg-video-fbdev 
  xserver-xorg-video-glint xserver-xorg-video-i128 xserver-xorg-video-i740 
  xserver-xorg-video-i810 xserver-xorg-video-imstt xserver-xorg-video-intel 
  xserver-xorg-video-mga xserver-xorg-video-neomagic 
  xserver-xorg-video-newport xserver-xorg-video-nsc xserver-xorg-video-nv 
  xserver-xorg-video-rendition xserver-xorg-video-s3 
  xserver-xorg-video-s3virge xserver-xorg-video-savage 
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis 
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga 
  xserver-xorg-video-trident xserver-xorg-video-tseng 
  xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vga 
  xserver-xorg-video-via xserver-xorg-video-vmware 
  xserver-xorg-video-voodoo xsltproc xubuntu-restricted-extras 
  xulrunner-gnome-support xutils yelp zenity zim zlib1g zlib1g-dev 
The following NEW packages will be installed:
  libflashsupport libopencdk10 
The following packages will be upgraded:
  flashplugin-nonfree libc6 libgnutls13 libpulse0 
4 packages upgraded, 2 newly installed, 6 to remove and 1122 not upgraded.
Need to get 4792kB of archives. After unpacking 206MB will be freed.
The following packages have unmet dependencies:
  libc6-i686: PreDepends: libc6 (= 2.6.1-1ubuntu10) but 2.7-5ubuntu2 is to be installed.
  libgnutls-dev: Depends: libgnutls13 (= 1.6.3-1build1) but 2.0.4-1ubuntu1 is to be installed.
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-5ubuntu2 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
libgnutls-dev

Upgrade the following packages:
libc6-dev [2.6.1-1ubuntu10 (gutsy-updates, now) -> 2.7-5ubuntu2 (hardy)]
libc6-i686 [2.6.1-1ubuntu10 (gutsy-updates, now) -> 2.7-5ubuntu2 (hardy)]

Score is 199

Accept this solution? [Y/n/q/?] 
```

Now what to do?

---

### Post by karlo on 2008-02-19
> **mbsullivan said:**
> Okay... a brief explanation is that the userspace and ondemand CPU frequency governors modulate your CPU speed (as I'm sure you know) based on the current amount of program activity. The userspace governor runs completely in userspace (i.e. with no kernel interaction). On the other hand, the ondemand governor is newer and has kernel support (since linux-2.6.9, if it's enabled in your build). 

The "powersave" governor keeps your CPU at the slowest speed step at all times, and the "conservative" governor keeps your CPU at the fastest speed step at all times.

So... what this issue boils down to is... use ondemand! It switches speed much quicker than the userspace daemon, which results in fewer performance losses, but resides in the lowest speed step the vast majority of the time, which saves lots of power.



Some distilled directions follow (mostly from [here]("http://ubuntuforums.org/showthread.php?t=248867"))... put these into the command line after booting to recovery mode.

(1) remove userspace daemons, if present

```
sudo apt-get remove powernowd cpudyn
```

(2) load speedstep module for Pentium M

```
sudo modprobe speedstep-centrino
```

... if this doesn't work for some reason, do:

```
sudo modprobe acpi-cpufreq
```

(3) load CPU governor

```
sudo modprobe cpufreq_ondemand
```

(4) enable ondemand CPU governor

```
sudo -s
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

Okay... now the ondemand governor should be enabled. If this works, let's make the changes permanent.

(5) load cpufreq_ondemand at startup... add "cpufreq_ondemand" to the end of /etc/modules. You can also remove any previous cpu governors, if present.

(6) set CPU governor to ondemand...

```
sudo apt-get install sysfsutils
``` 

Then add the line below to the end of /etc/sysfs.conf:

```
devices/system/cpu/cpu0/cpufreq/scaling_governor=ondemand
```

As for "setting the minimum to 600MHz, maximum to 1.40GHz", I don't believe it's possible to set the steps by which your processor changes speed (I may be wrong)... But, it's possible to see the speed intervals by doing a:

```
 cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

Hope this helps!
Mike

SORRY FOR A VERY LATE REPLY.

Now, tried doing what you said, it helped me a lot, changing the maximum and minimum frequency, for example I wanted min: 600MHz, and max: 1.40GHz, they are all being applied at startup... Check out my attachment .. edited with GIMP, yup it's photoshop for linux ...

changed the maximum and minimum speed to the available frequencies, even tried making the speed like 40-70% of my original one, tried removing it, the userspace daemons, still slow and TURNS OFF AGAIN AUTOMATICALLY.

my theory, i removed the laptop tools, then i never experienced any turn off thing, actually it does not turn off, it only logs off automatically.

again never experienced anything, even when compiz fusion is on, then i tried using my battery, i realized it really helps because my battery drained, and I did not experienced any hibernatikon etc:lolflag:

now i installed laptop tools again and I remembered before I set it to be enabled even when I am on ac power so i checked it again and make sure it's not enabled when i am on ac power.

i was hoping everything would be ok and i would not logged off automatically but i was wrong.

It happened again with the message:

check the screenshots, if you don't understand something please tell it to me. it made me lazy to type all here, instead check out the notes...

help me please and also, do you think i must post this in launch pad?

oh yeah, i disabled compizfusion and i haven't experienced any log off issue now, (upgrading and downgrading my graphics card driver, intel experimental ro intel i810 vise versa), never experienced logging off thingy only ubuntu is really really slow...

---

### Post by karlo on 2008-02-19
> **Samhain13 said:**
> Karlo, something just occured to me.

Can you go to System > Preferences > Sessions and see if "Tracker" is checked? If so, uncheck it then log-out and log-in again. See if there's any improvement on the speed with which Gedit or other applications load.

well tracker is very useful right for searching files like google desktop?

---

### Post by karlo on 2008-02-21
While browsing the net, I noticed that my mouse lags and my system load is more than 6.66!!! while the processor load is 100% ...

It's because of the **Update Manager**, it hangs on the part when it reads the **dependences** (is it the right term) OR reading state **information!**

it's the first time that it happened to me..... it gave me a ***trauma*** on **updating** stuffs.

Same thing happened when ***installing*** updates..

**YouTube video:** [http://www.youtube.com/watch?v=KQtOI61zCBU](http://www.youtube.com/watch?v=KQtOI61zCBU)

---

