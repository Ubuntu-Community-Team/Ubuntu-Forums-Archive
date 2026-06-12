---
title: "Are the kernel header files contained in build-essentials package?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-06-09
Im just going to re-iterate the subject of this post -- do you know if the kernel version header files are contained in the build-essential package??  If not, where can I find them?

---

### Post by Bachstelze on 2007-06-09
No, they're not. To install the headers for your current running kernel :

```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by kevdog on 2007-06-10
This is what I hate about ubuntu ---  more specific about the people who put the live CD together.

What if you dont have an internet connection.  Im trying to compile ndiswrapper from source to get the internet working.

Rant -- I mean seriously what were the package creators of Ubuntu thinking!!! As if getting wifi was hard enough already, ndiswrapper package is not included in the LiveCD -- but the build essential package is.  That means I have to compile it from scratch.  I download on a different computer the ndiswrapper package, move it from the other computer on USB stick, unzip it, but WAIT -- I need the header files for the kernel to compile from source!!!!  These must be on the Live CD -- but WAIT -- they aren't either.  Was anyone thinking when they did this??? Seriously!  No wonder the networking forum are full of people complaining they cant get wireless working.  I can understand the drivers not being included, but what about all these other packages.  Wait a minute -- I need the cabextract package to unzip the driver.exe file -- but WAIT -- this isnt included on the LiveCD either.

---

### Post by ThinkBuntu on 2007-06-10
OK, enough venting. If you need ndiswrapper installed, or don't have the opportunity to configure your system with an internet connection, use Mint. It comes with Ndiswrapper installed, as well as mintWifi (or is it mintWireless?) which is an ndiswrapper frontend. Very nice.

---

### Post by kevdog on 2007-06-10
I will take a look at it -- I dont read every post in the forums, but this is the first time Ive seen this mint package mentioned.

Here's the problem -- Ive installed ndiswrapper from svn - and its great.  The instructions from the sourceforge website are great. 

Based on my success, I felt like I would give back to the community, because it did take me a while to get a successful installation.

Im finding the posts in the networking forum are really about 80% of the same complaint -- total noob, cant get wireless working, etc.  Most need the ndiswrapper package solution, because all do not have broadcom chipsets, and bcm43xx does not work on all revisions of the chipset.

Anyway, trying to give instructions to total beginners how to actually download what packages, compile, install them, etc. is very difficult -- Ive only learned through them about what can be done and what cant, and what is on the LiveCD, and what isnt, and what needs to be downloaded in addition to ndiswrapper tarball, etc.  After Ive answered about 10 posts, Im getting frustrated not with them, but with the Ubuntu folks themselves.  Dont the package installers read the forums and say -- hey wait a minute I think we could make this easier for everyone!??

Thanks for your help.

---

### Post by ThinkBuntu on 2007-06-10
> **kevdog said:**
> I will take a look at it -- I dont read every post in the forums, but this is the first time Ive seen this mint package mentioned.

Here's the problem -- Ive installed ndiswrapper from svn - and its great.  The instructions from the sourceforge website are great. 

Based on my success, I felt like I would give back to the community, because it did take me a while to get a successful installation.

Im finding the posts in the networking forum are really about 80% of the same complaint -- total noob, cant get wireless working, etc.  Most need the ndiswrapper package solution, because all do not have broadcom chipsets, and bcm43xx does not work on all revisions of the chipset.

Anyway, trying to give instructions to total beginners how to actually download what packages, compile, install them, etc. is very difficult -- Ive only learned through them about what can be done and what cant, and what is on the LiveCD, and what isnt, and what needs to be downloaded in addition to ndiswrapper tarball, etc.  After Ive answered about 10 posts, Im getting frustrated not with them, but with the Ubuntu folks themselves.  Dont the package installers read the forums and say -- hey wait a minute I think we could make this easier for everyone!??

Thanks for your help.
It's not a package, it's an alternative OS based on Ubuntu with the multimedia codecs, etc. installed by default. Great for those who don't want to or can't connect online. [Here's their homepage]("http://www.linuxmint.com")

---

### Post by Bachstelze on 2007-06-10
> **kevdog said:**
> This is what I hate about ubuntu ---  more specific about the people who put the live CD together.

What if you dont have an internet connection.  Im trying to compile ndiswrapper from source to get the internet working.

Rant -- I mean seriously what were the package creators of Ubuntu thinking!!! As if getting wifi was hard enough already, ndiswrapper package is not included in the LiveCD -- but the build essential package is.  That means I have to compile it from scratch.  I download on a different computer the ndiswrapper package, move it from the other computer on USB stick, unzip it, but WAIT -- I need the header files for the kernel to compile from source!!!!  These must be on the Live CD -- but WAIT -- they aren't either.  Was anyone thinking when they did this??? Seriously!  No wonder the networking forum are full of people complaining they cant get wireless working.  I can understand the drivers not being included, but what about all these other packages.  Wait a minute -- I need the cabextract package to unzip the driver.exe file -- but WAIT -- this isnt included on the LiveCD either.

Too bad, dude, the headers *are* on the CD ! Next time you want to spread FUD, be sure you don't spread lies as well..

---

