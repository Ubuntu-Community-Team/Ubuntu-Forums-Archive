---
title: "Dual Boot question"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by XxSnipedYouxX on 2007-06-10
If I want to dual boot xp and ubuntu when I go to partition my hard disk will it delete my files?

---

### Post by bren on 2007-06-10
supposing you are installing the 7.04 LIVE CD you can boot ubuntu from the liveCD to see if you like it.  

if you like it click INSTALL on the desktop - only then will some files be put on your hard disk

during install you will be given option to 

a) wipe whole HD (incl xp) and install only ubuntu
b) reduce size for XP and put ubuntu in space made
c) manual settings by you

I suggest you choose option b)

---

### Post by johnny4north on 2007-06-10
no, it wont delete your files.  clean-up drive and defrag drive.  back-up your OS.  check out this link - [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)  i would use a live cd of ubuntu 7.04 for  week to see if it will work alright.  welcome to ubuntu..:)

---

### Post by freebird54 on 2007-06-10
Your files are generally safe.  However, you should never go major things to your hard drive without a backup of the data - just in case! (power failure or surge - unexpected errors on the drive etc etc)

Also - it is possible to accidentally TELL the installer to clean off the drive - and I don't think you want to do that.  If you are running Windows currently, it is best to go and turn off your page file, then run defrag a couple or three times before you start the process of resizing your current install.

If you have some favourite way of working with partitions already, you can do THAT before installing as well (say you had partition magic for one) - but it is unnecessary.

So - do a backup - and answer questions carefully and you should have no troubles.

Hope this helps!

(PS: - you can stay hooked up the internet WHILE installing if you are doing so from a Live CD - which means if you have questions half way through you can get immmediate (nearly) answers for them here...)

---

### Post by freebeer on 2007-06-10
It won't delete your files unless you make a major mistake.  Do backup your important files first as a precaution.

Here's a how-to for ya! [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I've set up four dual-boot computers with Ubuntu for far, and I never lost any data.  But I did backup files first.

---

### Post by Motoxrdude on 2007-06-10
Nope, it will not. Just resize your windows partition and create a new ext3 and swap partition. I dont mean to advertise but i made a "How to" on another forum. Here's the link if you are interested.
[http://xtechforum.com/index.php?page=14]("http://xtechforum.com/index.php?page=14")

---

### Post by XxSnipedYouxX on 2007-06-10
Thank you everyone! I wanted to make sure because from most of what I've read it does, delete your files; well I guess those people weren't dualbooting.

---

### Post by NotRoot:-) on 2007-06-10
> **XxSnipedYouxX said:**
> If I want to dual boot xp and ubuntu when I go to partition my hard disk will it delete my files?
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)    
Always back your data up before installing new software.  
Use the manual partitioning method if you want to keep existing data.  You'll probably have to shrink the windows partition down, to make a new linux partition to install Ubuntu.
This assumes that you have an existing windows partition that is not completely full.

---

