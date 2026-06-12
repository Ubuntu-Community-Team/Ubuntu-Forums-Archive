---
title: "Will the programs for Ubuntu 7.04 work well on 6.06?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by NT4.0 on 2007-06-05
I have been using Ubuntu for a year but I am not yet fully familiar with the way packages are installed on the system. For example, I want to install Thunderbird 2.0 on my Ubuntu 6.06 system but in the repositories it is said that 1.5 is for 6.06 and 2.0 is only for the last beta (I forgot the codename). The same with Firefox. What is the best way to update my software -- use packages for newer Ubuntu versions or download sources and compile them? I am confused because on Windows it didn't matter which version of a program I used.

---

### Post by dpzektor on 2007-06-05
You know what's funny? I downloaded a program not too long ago that had Dapper, Edgy, and Feisty versions. I accidentally downloaded the Dapper version and installed it onto my Feisty machine. Well, it worked as normal. On that note, it doesn't hurt to try I suppose....but maybe we'll wait for an expert opinion :)

---

### Post by tdrusk on 2007-06-05
Any program should work with any Ubuntu as long as you have the right dependencies.

If you want to stay up to date on the programs you can download the newest Ubuntu release. They do this for stability reasons. They work out all the kinks with certain programs and give them to the user. It's then your option to upgrade programs that aren't in the Ubuntu repositories.

---

### Post by Crafty Kisses on 2007-06-05
> **NT4.0 said:**
> I have been using Ubuntu for a year but I am not yet fully familiar with the way packages are installed on the system. For example, I want to install Thunderbird 2.0 on my Ubuntu 6.06 system but in the repositories it is said that 1.5 is for 6.06 and 2.0 is only for the last beta (I forgot the codename). The same with Firefox. What is the best way to update my software -- use packages for newer Ubuntu versions or download sources and compile them? I am confused because on Windows it didn't matter which version of a program I used.

To my knowledge, Yes. They should work with any version of Ubuntu that's currently out right now.

---

### Post by NT4.0 on 2007-06-05
Thanks, guys, so I shouldn't worry. I'll try to install new Firefox & Thunderbird versions. As far as I know, I'll still have to do that by hand because Synaptic shows only the versions for 6.06.

---

### Post by NT4.0 on 2007-06-06
Unfortunately, the system does not let me install Firefox 2 or Thunderbird 2, the packages conflict with some libraries. I read more about this and found that installing Firefox 2 on Ubuntu 6.06 is not easy, the same with Thunderbird. As far as I found out, the program needs to be "backported" to an earlier release of the system to resolve the conflicts. I'll have to stick with 1.5 ones for a while...

---

### Post by tdrusk on 2007-06-06
Unless you have a reason to stay with Edgy, you can use [this process]("http://onlyubuntu.blogspot.com/2007/03/upgrade-ubuntu-610-edgy-eft-to-ubuntu.html").

---

### Post by vanadium on 2007-06-06
You need to see it this way: the packages that are officially prepared and supported for your distro are guaranteed to work. You can try installing other packages, but then, it is at your risk.

---

### Post by steve.horsley on 2007-06-06
You could always just install the real version direct from mozilla.com. They come in a tar.gz if I remember right, and you just extract these to folders in /opt (you need to do this as root - launch nautilus with **gksudo nautilus** and be careful!). Then you just make a symlink in /usr/local/bin to the new firefox with this command:
**sudo ln -s /opt/firefox/firefox /usr/local/bin/firefox**

---

### Post by jverkamp on 2007-06-06
I agree with fuzzyhair, if you have the bandwidth to spare, it's highly beneficial to upgrade to Feisty Fawn.  On the whole, things seems to be snappier and more stable in the new version (at least in my case).  I've been using Feisty since it was in alpha and I've always like what I've seen.

If you do choose to upgrade, make sure you use the graphical update method.  Updating *sources.list* and using *apt-get dist-upgrade* can break your system mid-upgrade.  It's possible to fix it, but it takes more time then it's worth, believe me.  ;)

---

### Post by NT4.0 on 2007-06-06
jverkamp, fuzzyhair: First of all, I have Ubuntu 6.06 (Dapper), not Edgy. Second, I am not planning to switch from this version as it works fine for me. Third, I have dial-up connection and I would not imagine upgrading the system via it. Fourth, if I need to upgrade, I will always download the CD image and install the system anew.

Actually, Mozilla Firefox/Thinderbird 1.5 are good but I am surprised that it's so troublesome to install newer versions on the same OS release. If I just compile the sources, will it inevitably lead to conflicts?

---

### Post by kittyhawk63 on 2007-06-06
> **NT4.0 said:**
> Thanks, guys, so I shouldn't worry. I'll try to install new Firefox & Thunderbird versions. As far as I know, I'll still have to do that by hand because Synaptic shows only the versions for 6.06.

Automatix2 now has version Thunderbird 2.0 for Feisty. I don't know if it shows it in Dapper, however,
kh

---

