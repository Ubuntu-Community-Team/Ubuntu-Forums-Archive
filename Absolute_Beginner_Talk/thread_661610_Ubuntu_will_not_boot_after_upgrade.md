---
title: "Ubuntu will not boot after upgrade"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by circusmonkey on 2008-01-08
I  updated my install of ubuntu as directed by the updater. Now my machine will will not boot at all ! I was  on   2.6.20-16  generic 64bit.  

I have tried booting up in recovery mode , it runs through as it loads various things up , then it just comes to what looks like a terminal and puts me the user @root 
I thought it might be the x server and I have run sudo apt-get install ubuntu-desktop 
It said the latest version was already installed , so I tried  start x , nothing happened.I also read about a broken release I tried sudo apt-get install x server-xorg-core=1:1.0.2-0unbuntu10  then sudo start X , that did nothing.

What can I do to fix this ?  .I am not a computer programmer , just a newbie home user .So basic instructions are needed ! 

R

---

### Post by kellemes on 2008-01-08
Don't try to start X-windows in recoverymode..

What's happening when you boot Ubuntu in normal-mode?

---

### Post by circusmonkey on 2008-01-08
nothing ...... I dont get a splash screen. of note I did install my original nvidia drivers  with envy

---

### Post by circusmonkey on 2008-01-08
No ideas ? .

---

### Post by matrimubu on 2008-01-09
same thing happened to me. I have ubuntu 32 bit gutsy installed. I did the update as suggested by the system updater. My partition appears to have been corrupted. fsck can not read the partition from recovery mode. It gets listed from fdisk -l but that is all. I booted into a live CD and gparted sees it but doesn't understand it. I thought it was my /boot partition that was hosed, but now I think it was the extended partition. These partitions were created by the installer. I allowed it to create all the partitions. It looks like it is LVM in an extended partition. Whatever was in that update caused it to crap out. 

I think I am just reinstalling. Trying to fix this is taking too much time.

Good luck ...

---

### Post by houstonbofh on 2008-01-09
If you can boot into recovery mode, they system is still there, but X is messed up.  From the recovery system type "dpkg-reconfigure xserver-xorg" to reconfigure X.  Then reboot. If that fails, report back for the next step.

---

### Post by circusmonkey on 2008-01-09
Well after speaking to the experts at work ....

I had to enter the recovery install and then use the command sudo envy , which then uninstalled  and then reinstalled the graphics drivers. or I could of manually edited the xorg file . It seems when ever you upgrade it breaks something to do with the nvidia drivers. 
Quite why on earth this has not been addressed is beyond me. Its just another thing that puts people off using ubuntu over windows ..........

---

### Post by shareMenaPeace on 2008-01-09
Happend to me to early in 2007, but not with the last kernel header update - but this time i had ATI - not sur eif this has anything todo though ...

:popcorn:

---

### Post by rkd on 2008-01-09
> **circusmonkey said:**
> 
Quite why on earth this has not been addressed is beyond me. Its just another thing that puts people off using ubuntu over windows ..........
Please try to remember that the reason things are so fragile with the video is that Nvidia and ATI are very secretive about the information programmers need to make their video hardware work. I think it is amazing that the Linux programmers have been able to figure out enough to make the video work as well as it does. 

I know that, regardless of the reason, it is annoying. But please direct your ire at Nvidia, not at Ubuntu.

Oh, one other point. I noticed you mentioned using Envy. I have seen postings that caution about using Envy because, while it seems to get things going with minimal fuss, there seems to be some evidence, or at least suspicion, that it leaves unintentional land mines in the package database that go off during upgrades. You might have been another accidental victim of that. I hope I'm not spreading false information, but that's what I've read.

---

### Post by PmDematagoda on 2008-01-09
If the OP is still open to suggestions, here is something that could be attempted.

Boot Ubuntu in Recovery Mode, then execute:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
after that is done, execute:-
```
startx
```

---

### Post by philinux on 2008-01-09
I think he's solved it PmD.

---

### Post by PmDematagoda on 2008-01-09
> I think he's solved it PmD.

Oh yes,:oops:, thank you philinux:).

---

### Post by muteXe on 2008-01-09
This kinda thing happened to me when trying to upgrade to Gutsy.  In the end I had to format my linux partition and reinstall Feisty.  A shame really as i'd love to try Gutsy but don't want to risk it again :(

---

### Post by eolson on 2008-01-09
Here's what happens to mine.   It goes to the X longin screen you enter username and password normally it then goes and starts to load the desktop.  Gets part way through and blows up and goes back to the X log in again.

Sure with it happend sooner in the boot sequence.

Still messing with it.

---

### Post by bellciao on 2008-01-09
I have the official driver from Nvidia site, and today upgrading messed them up. Now I'm in minimal graphical mode. I tried to reinstall them but even if the installation went fine they still don't work.

---

### Post by muteXe on 2008-01-09
I only installed Envy as the resolution i wanted (1280x1024) wasn't on the ubuntu screen res menu.  Since then i've heard Envy can do nasty things when trying to upgrade. Not sure how else to enable the res i want (tried editing the x11.xorg file but that didn't work) so i'll have to stick with envy and not upgrade to Gutsy. :(

---

### Post by philinux on 2008-01-09
> **muteXe said:**
> I only installed Envy as the resolution i wanted (1280x1024) wasn't on the ubuntu screen res menu.  Since then i've heard Envy can do nasty things when trying to upgrade. Not sure how else to enable the res i want (tried editing the x11.xorg file but that didn't work) so i'll have to stick with envy and not upgrade to Gutsy. :(


I've read loads of posts on here from people running gutsy who've used envy with no bother.

If you make a backup copy of your working xorg.conf you can always restore it easily.

---

### Post by houstonbofh on 2008-01-09
Evny, and nvidia binaries are the most common reasons upgrades fail.  Seriously.  Envy is NOT upgrade friendly.  Also, it is not needed.  I am running nvidia-glx-new at 1280x1024 right now.  The repository drivers work, and upgrade clean.  However, if you have used a script to hack your system, you may be unable to "unhack" it clean.

---

