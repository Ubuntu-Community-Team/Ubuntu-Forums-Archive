---
title: "Wine help"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by CanadianGuitarist on 2007-12-14
I'm having a hard time installing wine. I dont know whats wrong. What do i need for it to work? can someone run me through the commands to get it?

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

##Universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## Multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Backports

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

## WINE REPOSITORY
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## MEDIBUNTU REPOSITORY
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

## VIRTUALBOX REPOSITORY
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free

---

### Post by Thanoulis on 2007-12-14
Have you tested to comment out all the non-official sources?
I have install wine with the original repositories (gutsy main/restricted/universe/multiverse) and worked like a charm!

---

### Post by aonegodman on 2007-12-14
Newby question here. Does Wine require the Windows OS to run, or is just required to run Windows based systems on Linux?

I guess I want to know can I use it on Ubuntu only system? Thanks all.

---

### Post by g2g591 on 2007-12-14
It doesn't require windows. and you should use the budget dedicated repo, as wine is developing fast. add universe to the budget dedicated repo, and you don't need the deb-src ones (just comment them out by placing a # infront of them)

---

### Post by sgtbob on 2007-12-15
I've installed Wine in Ubuntu 7.10 via synaptic and it is version 0.9.46. I have been unable to  acquire newer versions. No matter how I posit 'sudo apt-get install wine' it always installs this same verison.

Be that as it may - how do I operate a Windows program through WINE 0.9.46? I've tried reading a lot of documentation, but most of them do not discuss simple step 1, 2, 3, etc. For example, I DL the 'Wine users Guide' and in chapter 1, there is a '...**to test your installation...use wine winefile.**.'.  Great - I get a 'tree', but have absolutely no idea how to get to my drive C: to use Wine.It discusses 'adding items...', but never explains to the point I can understand it.  Anyone have some advice (be nice) for this noob or point me to a 'how to' instruction?

Bob:confused:](*,)

---

### Post by PmDematagoda on 2007-12-15
Using Wine is really simple once you get the hang of it which is itself easy to use as well.

To use Wine on an .exe file do:-

```
wine nameoffile.exe
```

Basically that is it when you consider the use of Wine, but if you want to configure Wine to fit your needs, then you can do:-

```
winecfg
```

Or you could use [Wine-Doors]("http://www.wine-doors.org/wordpress/?page_id=3").

If you want to get the latest Wine, then follow the instructions [here.]("http://www.winehq.org/site/download-deb")

But keep in mind, the stuff I gave above are the basic functions of Wine, you can do more than just that if you know where to look and what to do.

---

### Post by sgtbob on 2007-12-15
Thanks ever so much, the instructions you gave allowed me to download Wine's latest version and install it.  I kept trying to get version 0.9.51 and your guide allowed me to do that.

Bob

---

### Post by PmDematagoda on 2007-12-15
Glad I was able to help:).

Wish you a Happy Holiday Season:lolflag:.

---

### Post by sgtbob on 2007-12-15
I'm still stumped - when I try to use WINE, I always get this type error:

[B]bob@XPS:~$ wine XPFix.exe
err:reg:SCSI_getprocentry bus id line scan count error (fscanf returns 0, expected 4)
wine: could not load L"c:\\windows\\system32\\XPFix.exe": Module not found
bob@XPS:~$ wine PKUNZIP.exe
err:reg:SCSI_getprocentry bus id line scan count error (fscanf returns 0, expected 4)
wine: could not load L"c:\\windows\\system32\\PKUNZIP.exe": Module not found
bob@XPS:~$ [/B]

I did as you suggested, went to the site you indicated and performed the following functions:

[B]Adding the WineHQ APT Repository:

First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Gutsy (7.10):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list
[/B]...........

[B]Then, you can install Wine from WineHQ like it were any other package, such as by using the Synaptic Package Manager under System->Administration. Alternatively, you can install from the terminal by running 'sudo apt-get update' to update APT's package information and then 'sudo apt-get install wine'.
[/B] This feature allowed me to install the most curretn version of WINE - .0.9.51, but I'm still lost....


Perhaps WINE isn't designed to work the way I envisioned.  I thought I would be able to run my Windows programs through Linux.  I am able to open my 'disk' from windows and use files there; however, not some of the Windows porgrams I would like to run.  Is '.exe' the only one that will work?  What about the .doc and .xls files?

Bob

---

### Post by aonegodman on 2007-12-15
I got the following error in Terminal when exec the second for Ubuntu Gutsy (7.10):

 sudo wget [http://wine.budgetdedicated.com/apt/...t.d/gutsy.list](http://wine.budgetdedicated.com/apt/...t.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list
--15:02:42--  [http://wine.budgetdedicated.com/apt/...t.d/gutsy.list](http://wine.budgetdedicated.com/apt/...t.d/gutsy.list)
           => `/etc/apt/sources.list.d/winehq.list'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:02:42 ERROR 404: Not Found.

When I ran ***sudo apt-get install wine*** It got and installed _Wine 0.9.46_

Thanks for help and comments, this is all new and exciting stuff to this new Ubuntu user. :)

---

### Post by sgtbob on 2007-12-15
aone... - I opened one workplace on the internet site and another  workplace in terminal then copied  from the internet and pasted to the opened terminal in the following steps (I used those for 7.10).  I recommend you copy and paste from here:

(1) wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

(2) sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

(note: there is a space after 'sudo' and one after 'list' other wise there are no more spaces.

(3) sudo apt-get update 

(4) sudo apt-get install wine

When I finished, Wine was under 'Applications' as a separate program and it did install version .0.9.51.  That part worked - I just don't know how to make WINE work.... yet..:confused:

---

### Post by sgtbob on 2007-12-15
Here is what I get no matter which .exe file I insert:

[B]bob@XPS:~$ wine XPFix.exe

err:reg:SCSI_getprocentry bus id line scan count error (fscanf returns 0, expected 4)

wine: could not load L"c:\\windows\\system32\\XPFix.exe": Module not found

bob@XPS:~$ 
[/B]

Hopefully I have attached two screenshots:
[B]
screenshot.png [/B]is a result of entering **winecfg **in terminal.

**screenshot-1.png** is a result of entering **wine winefile**.

How does one use either of these screenshots?

---

### Post by arigram on 2007-12-15
You can always get a .deb package from here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
for easy one-click install.

---

