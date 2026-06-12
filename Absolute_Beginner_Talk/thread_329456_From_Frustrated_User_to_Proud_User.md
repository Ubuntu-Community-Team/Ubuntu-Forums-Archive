---
title: "From Frustrated User to Proud User"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by S.D.K. on 2007-01-01
Hello again all.

I'm happy to report that Ubuntu Installation #5 (AMD 64 Version 6.06) is finally stable for me!:D 

I still have no real idea what cause installation #2-4 to fail, but I have taken a few steps that it narrow down.

First the error that made me want to kill small animals and break my computer in half:

17179586.460000 EXT3-fs error (device hdb1) ext_check_descriptions Invalid bitmap
for group 384 not in gray (block 2147483647)!

Mount /dev/hdb1 on root failed: Invalid argument

mount /root/dev No Such file
mount /sys No Such File
mount /proc No Such file

Target filesystem doesn't have /sbin/init

/bin/sh: can't access tty; job control turned off

--------------
Things I did

Checked for possible HDD failure.
Checked, everything okay for now.

Running Memtest86+
Ran for 12+ hours
16 tests, no failures
Removed One 333MHz DDR 256MB Ram stick as it read only 128 MB as a precaution  

Excessive Heat?
Ran BIOS and increased fan speeds and lowered tolerance from 10C to 5C

Installation (From Dec 27 - Jan 1)
Installations #1 & 2 LiveCD x86 6.06 
Installations #3 & 4 Alt InstallCD x86 6.06
Installation #5 Alt InstallCD AMD 64 6.06

Well, for the last 5 hours, everything seems alright. Installed many things via Automatix2 [Excluded nVIDIA driver again as precaution] even installed flash support using a guide.

Yes. Many thanks to the many people who helped. Maybe the next time someone has an error similiar to the ones I had, thay can recieve help before they have to reinstall Ubuntu as many times as I did.

Anyone still want to guess what broke Ubuntu?
Was it bad ram?
Overheating?
Using x86 instead of AMD 64?

---

### Post by riven0 on 2007-01-01
Ah, so you got it back up and working. Alright! :KS Now you just got to test it for a couple of days to make sure no quirks pop up. 

If this is the first time you've excluded the nVidia driver and it's not crashing, it probably had something to do with that. But it's pretty strange, because I've never heard of graphics driver giving such problems... especially nVidia. They have good Linux support. :confused: 

Or, consequently, it could have been related to the way easyUbuntu and Automatix installed the driver, if that makes any sense. I've heard that some people need to re-install Ubuntu after using Automatix... not sure about easyUbuntu, but it's also possible.

Anyway, keep us updated! :mrgreen:

---

### Post by smoker on 2007-01-01
glad you have it all sorted, hope it stays that way (keep the small animals safe!)/

best of luck

---

### Post by S.D.K. on 2007-01-02
It now it is day two of Installation #5 and no problems have popped up. I installed the nVIDIA driver and everything is still okay. Turned off the computer last night and it boots up with no problems.

I can cross out that as a cause of what prevent Ubuntu from booting. That narrows it down to using the x86 installation, bad Ram, or possible overheating.

That aside, can someone help me or point to a how to of installing WINE on AMD 64 Ubuntu 6.06?

I read the howto on the WINE website and I found it confusing and unhelpful. This howto guide here "http://doc.gwos.org/index.php/Wine_AMD64" was more helpful but I am unable to access 
[http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.21~winehq0~ubuntu~6.06.orig.tar.gz](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.21~winehq0~ubuntu~6.06.orig.tar.gz)

Any help is greatly appreciated.

---

### Post by MkfIbK7a on 2007-01-02
[www.getautomatix.com](www.getautomatix.com) 
install this program you can install wine from it

---

### Post by S.D.K. on 2007-01-02
I have installed Automatix2 for AMD64 Drapper, but there is no option on installing WINE.
Currently I get time out/404 errors trying to get here: [www.getautomatix.com](www.getautomatix.com)

---

### Post by MkfIbK7a on 2007-01-02
yes the website goes offline alot
go into synaptic pakage manager 
got to the settings menu
choose repositories
check all the boxes click finish 
press reload in the bar on top then shut synaptic and open automatix2 it should be there now

---

### Post by S.D.K. on 2007-01-02
I have done what you suggested wert613, but I do not see the WINE option on Automatix2 any where.

---

### Post by MkfIbK7a on 2007-01-02
ok then search in synaptic for "wine"

---

### Post by S.D.K. on 2007-01-02
wert613, I search for Wine on synaptics. When I run the search, I get two options, however, when I try to install them, I get these errors:

libwine:
 Depends: wine  but it is not installable

libwine-dev:
 Depends: wine-dev  but it is not installable

---

### Post by MkfIbK7a on 2007-01-02
in synaptic go to 
the settings menu choose repositories check all the check boxes press reload on the bar on top and do a search for wine again

---

### Post by S.D.K. on 2007-01-02
Nope. still get the the same thing.

---

### Post by MkfIbK7a on 2007-01-02
do
```
apt-get install wine
```
put the output here

---

### Post by S.D.K. on 2007-01-02
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

---

### Post by MkfIbK7a on 2007-01-02
hmm looks like its missing from your resource list not sure how to fix that...

---

### Post by S.D.K. on 2007-01-02
Oh well, thanks for the help wert613 .

---

### Post by riven0 on 2007-01-02
How about posting your sources.list. 
 > 
sudo gedit /etc/apt/sources.list

Maybe you have a server commented off.

---

### Post by MkfIbK7a on 2007-01-02
good idea i should have thought of that

---

### Post by S.D.K. on 2007-01-03
Here what I got:

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper misc

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

