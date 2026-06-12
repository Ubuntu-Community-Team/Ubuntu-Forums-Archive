---
title: "install WICD without internet"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by gruss on 2007-12-28
OK, I realize I'm a newb and all but where oh where can I find an installer for WICD?  I just wanted to download it with another pc and run the installer from my new xubuntu load.  Every search says "oh its easy open synaptic"  synaptic is great and all dont get me wrong but I"m thinking a tool to help with the internet should be available without having to connect to the internet from that particular pc ;)  I used it on another install with my WPA network at home and its worked flawlessly, but that was a notebook and no big deal to get near the router and plug in a cable.  A deb package would be awesome, right click and go.  I guess I could disable security for a few minutes but I thought this would be way easier.

---

### Post by ugm6hr on 2007-12-28
From here:
[https://sourceforge.net/project/showfiles.php?group_id=194573](https://sourceforge.net/project/showfiles.php?group_id=194573)

The .debs are in there (select Download).

More info: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by Q4U on 2007-12-28
Hi:

I am no expert on this particular software and I am not sure if I understood fully the prob, but still:
1. navigate to the repo with your internet-enabled pc starting from [http://apt.wicd.net](http://apt.wicd.net)
2. download the relevant package 
3. make sure the dependencies are met (i.e. check the dependencies file and check that they are already in your target pc)
4. you should now have one or more (if dependencies are not met) .deb files. Transfer it (them) to the target pc (for example with the help of a usb stick). Then type the following from the terminal: sudo dpkg -i /path_to_the_package/name_of_the_package_to_install.deb
5. Afterwards check [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) to do after-install finetuning (esp. if you have KDE)

Did it work?

---

### Post by gruss on 2007-12-28
Awesome UG, I looked all over for that, now I feel silly.  right now that pc's in win2003 mode running a restore on a lost partition so it'll be a few before I try.  Gonna throw in a new wireless card that according to the wiki should "just work" cause the other one would barely hold a connection..el cheapo usb thingy.  Anyway thanks again...man I wish this forum was around the last time I messed with Linux...I'll post results when I get them.


Edit
All working thanks guys and just so ya know the nice cheap DLink PCI Wireless card WDA-2320 works outta the box with 6.06 and seems to have decent reception as well

---

