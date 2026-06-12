---
title: "How to install Lucid on MacBook Pro 5.3"
date: 2010-04-30
forum: Apple Hardware Users
---

### Post by arviso on 2010-04-30
I have created a partition through Boot Camp, downloaded the 64 bit Intel installer for PC and Mac, verified the checksum, burned a CD from its image (on the second try), but when I try to boot up from that CD, rEFIt refuses because of a "legacy" problem. I assumed it would be a live CD, from which I could do the installation; am I wrong, is there another way to install from it? My MacBook Pro 5,3 is the one exception to having its own installation page.


Please point me in the right direction to installing.

---

### Post by jacques4x4 on 2010-04-30
arviso, I haven't had any joy with a MacBook Pro 5,5 either..although 9.04 installs without any issues..  Are you using the latest rEFIt ?  I had troubles until I moved to version 0.14.  You might want to give that a try.  

My issue seems to be getting grub to install properly.  

Good luck..

---

### Post by CJN on 2010-05-01
> **arviso said:**
> I have created a partition through Boot Camp, downloaded the 64 bit Intel installer for PC and Mac, verified the checksum, burned a CD from its image (on the second try), but when I try to boot up from that CD, rEFIt refuses because of a "legacy" problem. I assumed it would be a live CD, from which I could do the installation; am I wrong, is there another way to install from it? My MacBook Pro 5,3 is the one exception to having its own installation page.


Please point me in the right direction to installing.

Simple, don't use refit, it's useless just hold alt at boot, uninstall that and you should be golden.

---

### Post by arviso on 2010-05-01
> **CJN said:**
> Simple, don't use refit, it's useless just hold alt at boot, uninstall that and you should be golden.

[QUOTE}
jacques4x4  	
Re: How to install Lucid on MacBook Pro 5.3
arviso, I haven't had any joy with a MacBook Pro 5,5 either..although 9.04 installs without any issues.. Are you using the latest rEFIt ? I had troubles until I moved to version 0.14. You might want to give that a try.

My issue seems to be getting grub to install properly.

Good luck..[/QUOTE]


I finally got the live-install disk to boot by selecting it in System Preferences->Startup Disk, then used it to install. All good, except I can't boot MacOS 10.6.3 from GRUB. I had to force-quit and reboot holding option/alt-key down and selecting MacOS. rEFIt doesn't seem to work as it did on my previous MacBook Pro, and I suspect GRUB superceded it. I don't know what version I was using. 


Is it worth re-installing rEFIt in its latest version? I would like the choice of boot-up disk, and it would be helpful when traveling to automatically boot up into Ubuntu, thereby protecting my old files in the MacOS partition. But I can use the option/alt-key instead, if necessary. It refers to the Ubuntu partition as "Windows."

---

### Post by kosumi68 on 2010-05-01
It is possible to boot directly from EFI using grub, as developed in this monster-thread: [http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

With grub-efi I can bless the ubuntu partition to be the default OS to boot, and also boot MacOS from grub (thus no need for refit).

---

### Post by arviso on 2010-05-01
> **kosumi68 said:**
> It is possible to boot directly from EFI using grub, as developed in this monster-thread: [http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704) 


From my brief examination of the monster-thread, I did not find my MacBookPro5,3 among the tested examples. I will try to keep rechecking on progress in this department, but I don't want to intervene in a working system with my very limited knowledge and skills, particularly since I will be taking my MacBookPro traveling this summer.



> **kosumi68 said:**
> With grub-efi I can bless the ubuntu partition to be the default OS to boot, and also boot MacOS from grub (thus no need for refit).



Thanks for the suggestions. Now I know what to expect.

---

### Post by arviso on 2010-09-24
> **jacques4x4 said:**
> arviso, I haven't had any joy with a MacBook Pro 5,5 either..although 9.04 installs without any issues..  Are you using the latest rEFIt ?  I had troubles until I moved to version 0.14.  You might want to give that a try.  

My issue seems to be getting grub to install properly.  

Good luck..
Thanks, Jacques, for the suggestion. My rEFIt, though upgraded relatively recently, is 0.11, so I will upgrade to 0.14. But I still need to know how to handle the "Install" step in the live CD Ubuntu 10.4.1 CD install procedure to insert the correct figure in the correct place to create an Ubuntu partition of about 75GB.

---

