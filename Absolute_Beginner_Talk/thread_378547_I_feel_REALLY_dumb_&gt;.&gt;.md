---
title: "I feel REALLY dumb &gt;.&gt;"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by starcraft.man on 2007-03-07
Hi. I'm fairly brand new to Ubuntu. Been a long time windows user (since DOS, goooooo command line). HA, that makes me feel old >.<. Anyway, in the past recent months I have been looking into Ubuntu due to my hostility towards Windows Vista (DRM restrictions, sloppy UI, Aero shunting via backwards compatibility errors and other such careless flaws in Vista).

Anyway, so I have currently installed Ubuntu into a dual boot in my main machine. I thought that would be really hard but it wasn't as bad as I thought when using my Acronis package to set up my drives. So, I had been trying Kubuntu before but found I was having numerous problems with the KDE desktop. So I switched to Ubuntu and installed it via the alternate install CD (had a bit of trouble with the main install CD with my dual boot). After getting it installed I of course used the update/upgrade/dist-upgrade to bring my OS up to date. I then decided to put in my Nvidia drivers, I have a 6800 GT and do plan to eventually get to XGL/Compiz (or some combination with AIGLX/beryl when I figure out the difference between all 4).

In my short lived previous Kubuntu install I had some trouble installing Nvidia drivers before as well, several failed attempts following the Ubuntu Guide method for manual installation. I eventually installed and used Automatix2 which seemed to fix my problem. Now that I am on Ubuntu, I have sadly found out that Automatix2 is down or gone? When I went to install I received a failed to connect to the repository command from the terminal, and the getautomix website returns me an error message. 

So, after coming to that sad realization I tried again to install nvidia drivers manually (from several different guides) and I keep getting the same problems. The kernel common and glx drivers download right, and they install right... but then I seem to do something wrong with the config cuz when I reboot I get this message saying "the Nvidia kernel could not be found and loaded" and I am forcibly shunted into the text mode. (I easily revert back to my clean install cuz I backed up my clean install via a back up software and reset every time I mess up).

**Question 1**
So, can someone please provide me a very basic (dumbed down) step by step complete guide so that I can't mess up the install and config, I would really like to get my nvidia drivers in. (I have tried automated method via easy ubuntu twice but it seemed to crash both times, as well as Ubuntuguide and a few other ways).

I really need these drivers in because I also have two monitors I'd like to configure.

**Question 2**
In addition, less importantly I was having some trouble (when I had Kubuntu configured properly with Nvidia drivers) getting my VP930b Viewsonic monitor configured with Kubuntu (I know Ubuntu similar so hope u can help) is there a compatibility issue? I know it wasn't in the drivers monitor list nor did it work with plug n play... any thoughts? Is there a manual configuration I have to do in xorg? (I have run the auto detect feature of Xorg and it fails to detect the monitor)

Hope somebody can help, I really would like to get going and learn more about Ubuntu and Linux as a whole. (Hope the read wasn't too long >.>)

BTW: I'm a Tea man, can I get leaves please? :D

---

### Post by Iceni on 2007-03-07
I have a 6800GS, pretty much the same card. I just downloaded the drivers from nvidia site and installed with the intaller. Worked like a charm. An alternative many seems to love is Envy, here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Note that envy gave me old drivers that did not perform well with beryl, while the newest ones from nvidia is flying.

---

### Post by j.miller565 on 2007-03-07
Try envy like Iceni said. it should solve your problems out pretty well at the moment.

---

### Post by starcraft.man on 2007-03-07
Well, I tried envy... but I only got as far as the deb package downloaded... I unchecked all the repositories manually in sources.list which I think is the only requisite and now when I double click the deb pack like it says I get "Error: Dependency is not satisfiable : module-assistant". Does that mean I'm doing something in particular wrong? Do I have to insert Envy manually in the sources list?

This is my sources list just in case I'm missing something >.>

```

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

---

### Post by MkfIbK7a on 2007-03-07
do 
> 
sudo apt-get install module-assistant 

in a terminal and then try again

---

### Post by starcraft.man on 2007-03-07
> **wert613 said:**
> do 


in a terminal and then try again

Ah ha, thanks.... gah, I just got back after being out and now I'm having one of those "DOH" moments... should have done "sudo aptitude search". Thanks Wert :)

Btw, is Automatix permanently down? I know I used it just a day or two ago...

---

### Post by starcraft.man on 2007-03-07
Hmmm, I got envy installed correctly and running properly but for some reason I seem to have gotten some errors during installation. I am not sure why... After install which closes properly (the error messages can be read in the terminal during the install), I clicked on the Nvidia settings manager under Envy in System settings and got the following Error.

```
Failed to Launch

Failed to execute child process "/usr/bin/nvidia-settings" (No such file or directory)
```

After that I ran Sudo Aptitude Search Nvidia and found this following stuff:

```
c   nvidia-glx                      - NVIDIA binary XFree86 4.x driver          
c   nvidia-glx-dev                  - NVIDIA binary XFree86 4.x / Xorg driver de
v   nvidia-kernel-1.0.7184          -                                           
v   nvidia-kernel-1.0.8774          -                                           
v   nvidia-kernel-1.0.8776          -                                           
v   nvidia-kernel-1.0.9746          -                                           
i   nvidia-kernel-2.6.17-10-generic - NVIDIA binary kernel module for Linux 2.6.
i   nvidia-kernel-common            - NVIDIA binary kernel module common files  
i   nvidia-kernel-source            - NVIDIA binary kernel module source        
p   nvidia-settings                 - Tool of configuring the NVIDIA graphics dr
p   nvidia-xconfig                  - The NVIDIA X Configuration Tool  
```

I know that "i" means installed and "p" means not installed (I think), what does c and v mean and if I am not mistake shouldn't I have nvidia-glx and nvidia-kernel-1.0.9746.

Can someone please tell me what is wrong? I did the automatic Nvidia install....

---

