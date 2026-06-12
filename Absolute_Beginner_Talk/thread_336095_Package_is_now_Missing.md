---
title: "Package is now Missing"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by crondog on 2007-01-11
Hi all,

This is my first post and i would like to say this forum has been great in helping me with my obstacles with Ubuntu so far...

I have come across a slight problem which i cant seem to find a solution for, but have searched on here and google without luck. 

My problem is that i tried installing Kubuntu over Ubuntu 6.10. I have the Ubuntu DVD, so i assume i have "everything". I chose kubuntu-desktop from the Synaptic Package Manager and chose install. It said it was going to download some updates for openoffice from the ubuntu site, which i didnt want updated cos i down want to waste my bandwidth on that...

It installed it without problem until i rebooted my computer, then the screen that is suppose to come up asking you which desktop environment never did...

Now kubuntu-desktop isnt even in the Package Manager anymore. I have tried 

sudo apt-get install kubuntu-desktop

but i get the error

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kubuntu-desktop

So can anyone help me out?

---

### Post by Seine on 2007-01-11
I'm not sure if kubuntu-desktop is on the DVD, but I can confirm that I do have access to it in one of my repositories.

```
jem@fawkes:~$ sudo aptitude search kubuntu
Password:
p   kubuntu-artwork-kbfx            - kubuntu artwork for KBFX                  
p   kubuntu-artwork-usplash         - kubuntu artwork for usplash               
p   kubuntu-default-settings        - Default settings and artwork for the Kubun
p   kubuntu-desktop                 - Kubuntu desktop system                    
p   kubuntu-docs                    - kubuntu documentation                     
p   kubuntu-grub-splashimages       - grub splashimages for Kubuntu             
p   kubuntu-konqueror-shortcuts     - Konqueror shortcuts for the Ubuntu wiki an

```

Here's my sources list. Not sure which repo has what you're after. 

```
jem@fawkes:~$ cat /etc/apt/sources.list
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb http://au.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

deb http://au.archive.ubuntu.com/ubuntu/ edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://au.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://au.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.)
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
# deb http://theli.free.fr/packages/ edgy listen

deb http://wine.budgetdedicated.com/apt edgy main

deb http://media.blutkind.org/xgl/ edgy main-edgy

## www.go-compiz.org/index.php?title=Ubuntu_Installation_Guide
deb http://gandalfn.club.fr/ubuntu edgy stable dev

```

---

### Post by justinlb on 2007-01-11
I had this problem as well at one point, but after looking around I found that it was better to just do a clean install of Kubuntu, that would be a better option unless you want to be able to switch between Gnome and KDE for different sessions.

---

### Post by crondog on 2007-01-11
I thought that the dvd had "everything"...maybe not...

I would connect to the net and download it but i am retricted to 1GB downlaods a month on iBurst and dont want to waste my limit.

---

### Post by crondog on 2007-01-11
Is there a way to do that just from the dvd (if it has it on there)?

---

### Post by Bachstelze on 2007-01-11
Well, the Ubuntu DVD has everything for UBuntu, which in the developpers' mind does not include Kubuntu...

---

### Post by justinlb on 2007-01-11
I'm pretty sure that all the Kubuntu files are in the repos that come with the CD/DVD, if you want a purely KDE environment without downloading Kubuntu you can always use [https://shipit.kubuntu.org/](https://shipit.kubuntu.org/) to send you a Kubuntu CD

---

### Post by crondog on 2007-01-11
My mistake then...

---

### Post by justinlb on 2007-01-11
You can make sure you have Kubuntu in the repos by opening a terminal and typing "sudo aptitude search kubuntu"

---

### Post by crondog on 2007-01-11
> **justinlb said:**
> You can make sure you have Kubuntu in the repos by opening a terminal and typing "sudo aptitude search kubuntu"

Tried that. Came up with nothing.

---

### Post by crondog on 2007-01-11
> **HymnToLife said:**
> Well, the Ubuntu DVD has everything for UBuntu, which in the developpers' mind does not include Kubuntu...

I thought that the DVD had "everything" from the [http://packages.ubuntu.com](http://packages.ubuntu.com) site. If it does then what is this [http://packages.ubuntu.com/edgy/metapackages/kubuntu-desktop](http://packages.ubuntu.com/edgy/metapackages/kubuntu-desktop) ?

---

### Post by justinlb on 2007-01-11
Do you have all the universal repos enabled?

---

### Post by crondog on 2007-01-11
> **justinlb said:**
> Do you have all the universal repos enabled?

All i have enabled is the dvd. Only because i assumed all i needed was on the dvd. If its not on the dvd then im not going to worry about it anymore because i dont want to downlaod anything...

---

### Post by justinlb on 2007-01-11
I only have the Live CD, so I can't give you an answer on whether the Kubuntu packages are on the DVD, I would suggest that you use ShipIt to get a Kubuntu disc for a clean install if you  aren't able to download anything.

---

### Post by crondog on 2007-01-11
> **justinlb said:**
> I only have the Live CD, so I can't give you an answer on whether the Kubuntu packages are on the DVD, I would suggest that you use ShipIt to get a Kubuntu disc for a clean install if you  aren't able to download anything.

Its no big deal anyway...i just wanted to try it. Being new to linux and all, i thought i would muck around with things so i can get used to it. Maybe another time...

---

### Post by rai4shu2 on 2007-01-11
The DVD for Ubuntu only contains Ubuntu and the Gnome-ish main packages, plus some essential KDE libraries. It doesn't contain all the Kubuntu packages.

---

### Post by crondog on 2007-01-11
> **rai4shu2 said:**
> The DVD for Ubuntu only contains Ubuntu and the Gnome-ish main packages, plus some essential KDE libraries. It doesn't contain all the Kubuntu packages.

That settles that then

---

