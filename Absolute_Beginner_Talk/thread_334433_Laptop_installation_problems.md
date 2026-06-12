---
title: "Laptop installation problems"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by cbartlo on 2007-01-08
Howdy folks,

I'm pretty new to the whole linux thing, and after successfully putting Ubuntu 6.10 on a desktop computer (with nary a hitch) I decided I wanted to try an install on an older laptop I had sitting around.

The laptop in question is a Gateway Solo 9300 (which basically is a p3 with 256mb ram, 12gb HDD and an AGP graphics card...there is also a wireless PCMIA card I'd like to use since there is no ethernet port, but not essential).  The ultimate goal is to get something up and running for the kids to do school and simple games on. 

I tried using the same install disk that I used on my desktop system, but the install program freezes before I get to the Ubuntu desktop where the install icon is.  I realize I'm trying to install to an older system (though I did get XP to run on it), does this mean I should be using a different version of ubuntu?

Thanks for any help!

---

### Post by scrooge_74 on 2007-01-08
Try using Xubuntu or the Alternate CD which installs from the console.

Older laptops work better with more light weight window managers, you should check ICEwm is pretty cool and is very light weight

Here is a nice thread on it by aysiu

[http://www.ubuntuforums.org/showthread.php?t=263710](http://www.ubuntuforums.org/showthread.php?t=263710)

---

### Post by c-ron on 2007-01-08
Hit the Esc key at the livecd boot menu to exit to the 'boot:' prompt.
Try running with some things disabled. You could try booting with "live noapic nolapic" to see if you can get to the desktop to install.

See this post:
[http://www.ubuntuforums.org/archive/index.php/t-148761.html](http://www.ubuntuforums.org/archive/index.php/t-148761.html)

---

### Post by djheadley on 2007-01-08
I had the same trouble with my Gateway Solo 2500.  I ended up going back to 6.06 (which is on my desktop) and although it seemed to take a long time, it works.  I haven't tried the other options as I wanted to at least keep with Gnome.  I don't have an answer but I'm glad I'm not alone.

---

### Post by cbartlo on 2007-01-09
Thanks for the info folks.  The "noapic" trick got it further along in the boot process but it still ended up freezing.  However I tried older versions of Ubuntu and I could get 5.10 installed and running.  

I can't connect to the internet yet so I guess my next question which is the more challenging problem to solve:

A) Getting my Belkin 54g wireless card working so I can download the software I'd like to install (Ubuntu didn't pick it up on the install)

B) Downloading the software on a different computer and installing it via CD (I'm not sure if this is even possible, I've just used the add/remove programs to get things on my desktop)


Thanks again for all the help!

---

### Post by scrooge_74 on 2007-01-09
for quesiton A, check this links:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

Second question it is possible to download the packages and then install them to your PC, but that is going to be a lot of work.

You should really try looking into the alternate CDs or Xubuntu, you wont be dissapointed.  I run gnome but I also have ICEwm install so I can do things a little different

---

