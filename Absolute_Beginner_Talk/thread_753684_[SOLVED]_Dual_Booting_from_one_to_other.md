---
title: "[SOLVED] Dual Booting from one to other"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Bubba64 on 2008-04-13
I downloaded Hardy on my Desktop, and it has run like a champ. On my laptop though which is a a21m IBM think pad 700 MHz 256 ram I was having freeze ups of the Hardy program. So I downloaded the Gutsy ISO and while attempting to reinstall, not really knowing what I was doing, I now have a dualboot of both which  in the end is  great, if I can get the Hardy to run in the end without freezing. My question is as of now the only way I know how to go to Gutsy or Hardy is with a reboot, is there an easier way.

---

### Post by tamoneya on 2008-04-13
yes you are correct.  When you have a dual boot the only way to switch OS is by rebooting.  You can however access files in the other system by mounting the other OSes partition and reading the files.

---

### Post by Bubba64 on 2008-04-13
> **tamoneya said:**
> yes you are correct.  When you have a dual boot the only way to switch OS is by rebooting.  You can however access files in the other system by mounting the other OSes partition and reading the files.

Thanx for your quick reply I am not familiar with doing that, but that is OK I just boot into Hardy for the updates now. Although I wonder if in the end the Hardy might be better installed with a ISO after it has been out for awhile. I do see people posting with freeze ups with faster computers and more ram. I don't think my desktop has more than 256 ram but it runs at 1.7 GIG.

---

### Post by dondad on 2008-04-13
> **Bubba64 said:**
> Thanx for your quick reply I am not familiar with doing that, but that is OK I just boot into Hardy for the updates now. Although I wonder if in the end the Hardy might be better installed with a ISO after it has been out for awhile. I do see people posting with freeze ups with faster computers and more ram. I don't think my desktop has more than 256 ram but it runs at 1.7 GIG.

One thing that you have to be careful of: If you do a dual boot with two different ubuntu distributions (an I assume with others also), the las one that you install will have the grub menu that gets used when you boot up. What this means is that if the other distribution does a kernel update, it will update it's own menu.lst file, but that will not be the one that boots because it will use the unupdated file in the other distribution. Right now, I am dual booting Gutsy and Hardy. For various reasons, Gutsy was the last install, so every time Hardy updates the kernel, I have to manually update the grub menu in the Gutsy install. I didn't realize this for awhile, and finally the older kernel that I was unknowingly using and the newer Hardy restricted drivers got far enough out of sync that it would no longer boot. Editing the Gutsy grub menu to use the latest kernel fixed the problem.

---

### Post by Bubba64 on 2008-04-13
> **dondad said:**
> One thing that you have to be careful of: If you do a dual boot with two different ubuntu distributions (an I assume with others also), the las one that you install will have the grub menu that gets used when you boot up. What this means is that if the other distribution does a kernel update, it will update it's own menu.lst file, but that will not be the one that boots because it will use the unupdated file in the other distribution. Right now, I am dual booting Gutsy and Hardy. For various reasons, Gutsy was the last install, so every time Hardy updates the kernel, I have to manually update the grub menu in the Gutsy install. I didn't realize this for awhile, and finally the older kernel that I was unknowingly using and the newer Hardy restricted drivers got far enough out of sync that it would no longer boot. Editing the Gutsy grub menu to use the latest kernel fixed the problem.

So I am set up the same way Gutsy is the second install. What you suggest is beyond my understanding at this point, although I am generally a fast learner. So if you can give me a more detailed description or a link to instructions that would be great. I have a link to a forum post on dual booting and I didn't notice anything as you describe but it does make sense as far as the description of how the computer gets to the kernel screen. Anybody else wanting to comment feel free, it seems that I could use some help here. Also if it is possible to just remove Hardy at this point I would do that any simple instructions or links to that process would be great. I can always install Hardy again later on to see if the freeze problem has been minimized.

---

### Post by Bubba64 on 2008-04-13
I have wiped the hard dive clean and am reinstalling Gutsy. I screwed up the Hardy Kernel by removing what I thought was extra not needed stuff, oh well live and learn,

---

