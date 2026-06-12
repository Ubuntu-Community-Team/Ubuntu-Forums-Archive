---
title: "installing gutsy and/or dualbooting?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by binskipy2u on 2007-10-27
anyone else dualboot? if so, where should i begin? what should i install first? should the share swapfiles?
anyone have a good how-to?
 anyone know if gutsy will work well(specially the full 3d effects) with my system specs?
any information would be most appreciated..thanks

amd xp2200
3 gigs pc2100 ram
80gig hd
128 ati radeon 9250 8xagp

btw i'm currently a pclinuxos2007 user, id like to dualboot with that..

---

### Post by mikewhatever on 2007-10-27
It isn't much of a how-to to dual boot to linux systems. Just set up a partition for Ubuntu and install, and yes, you can share the swap. To check if Gutsy works well on your hw, run it from cd first.

---

### Post by uclalinux on 2007-10-27
yes duel booting is easy, I have had 4 OSs on one HD at one time, (MAC, Solaris Gentoo, Windows)

if you are doing a fresh install i would install Windows first, then linux because it go very smooth, if you already have linux and want to add windows. then make sure there is a NTSF partition  on the the main hard drive(it a windows thing- it just makes everything easier). after windows is install you will most likely reload grub because windows will over write your MBR, and replace it with theres and theres would allow you to boot linux. 
so after windows is installed, boot to a live cd and fallow this 


[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)


here is the offical ubuntu page for the same problem, but i feel the other page is better(because it is shorter)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

