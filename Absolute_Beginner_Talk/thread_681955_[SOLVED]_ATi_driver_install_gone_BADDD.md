---
title: "[SOLVED] ATi driver install gone BADDD"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Psychlone on 2008-01-29
Hello.  I just recently decided to give Linux (in the Ubuntu form) a try for the first time.
I've used Windows since 3.1 and am very familiar with everything from BASIC to DOS to Vista, and can tweak the crap out of pretty much any system running on MS's OS, but have absolutely *no* experience with Linux (in any flavor)

Anyway, after trying to install Ubuntu and being defeated literally 20 times, I finally figured out that the HDD I was trying to install to (not dual boot, rather install to a separate HDD within the case) - had to be the *only* HDD plugged in - I suspect that the GRUB was installing on one of my Windows partitions and not seeing it when I tried to boot to the HDD that I actually installed Ubuntu on.
So, after a long, hard battle to get it all installed (which went smoothly after removing all the other HDDs in the system) - I tried to utilize the restricted graphics driver for my ATi HD2900XT card, which after reboot, lead to nothing but a black screen.
So, plugged in my Vista HDD, surfed the crap outta the net, came up with this forum and tried a couple of the main fixes (sudo dpkg-reconfigure xserver-xorg) which after reboot, limited me to 800X600 at 73Hz and I couldn't change it for the life of me.

I'm very new to Linux distros and would love to learn.  All I'm trying to do as a starting point is have my ethernet adapters work (which isn't a problem), the current driver for my ATi HD2900XT and to enable Compiz Fuzion (just so I can begin to get used to how to install programs/apps, and get used to how Linux works in general - it'll be quite some time before I'm ready to switch altogether from MS, but that is the goal for the future)

In any case, can someone please help me to get my graphics card running properly?  I'll worry about my X-Fi Fatal1ty later (if that's even going to work...)

System spex:
AMD Opteron 165 CCBBE 0615DPMW @ 3.2GHz
ASUS A8R32-MVP Deluxe w/ BIOS 0701 (newest)
2 X 1GB Corsair XMS3202C2 v1.3 @ 583MHz
HiS HD2900XT @ 884c/1150m (=2300MHz m)
6 X 500GB WD SATA2 HDDs (1 with nothing *but* Ubuntu on it)
X-Fi Fatal1ty Extreme Gamer w/ Cambridge Soundworks S750 7.1 DTS/THX
Samsung SyncMaster 204B
Aspire X-Navigator case w/ 4 X 80mm + 1 X 120mm fans
Zumax 650W CF Certified PSU

Please help - I'm not about to give up, but I *am* loosing hair over this!! ;)

Psychlone

---

### Post by phidia on 2008-01-29
Although there are exceptions, generally nvidia has better support in linux. 
That being said [this how to]("http://ubuntuforums.org/showthread.php?t=515573") should help you. If you get specific problems you may get faster responses in the [multimedia & video section]("http://ubuntuforums.org/forumdisplay.php?f=138"). 
Hope that helps & welcome to Ubuntu!

---

### Post by Psychlone on 2008-01-29
Thanks for the quick reply.

I have actually followed that as well as [http://ubuntuforums.org/showthread.php?t=584143]("http://ubuntuforums.org/showthread.php?t=584143") and [http://ubuntuforums.org/showthread.php?t=583138]("http://ubuntuforums.org/showthread.php?t=583138") and [http://ubuntuforums.org/showthread.php?t=561274]("http://ubuntuforums.org/showthread.php?t=561274") but still came up with the same problem - so far, all I've been able to do is reinstall from scratch (which isn't a problem since I've got nothing to loose (yet) - but it does take forever at CD speeds!! ;)

I've obviously borked something along the way during the install of the ATi Linux 8.1 drivers...why's it gotta be so much different from installing a driver on MS systems?  All that aside, I'm still not going to give up.  I'm going to install Ubuntu from scratch (so I'm not 'fixing' something I have no idea how to fix in the first place) - and then I'll go over the link you've provided with a fine-tooth comb and maybe figure out exactly where I went wrong (hopefully!)

Thanks again.

Psychlone


*** EDIT:  I finally got the ATi 8.1 drivers working with the following:
```
sudo ln -sf bash /bin/sh
bash ./ati-driver-installer-8.40.4-x86.x86_64.run --buildpkg Ubuntu/feisty
sudo ln -sf dash /bin/sh
```
...and then a full restart.

Thanks for pointing me in the right direction!!

Psychlone

---

### Post by phidia on 2008-01-29
Congrats!! Often staying with it is the solution and looking at the problem from a different angle-which is what help or even questions from others provides.

Even though troubleshooting is a pain your solution can help others too-glad you got it working!

---

