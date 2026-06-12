---
title: "Ubuntu DESTROYED after updating!"
date: 2010-12-17
forum: Apple Hardware Users
---

### Post by mosmetic on 2010-12-17
Hey guys, (sry for english)

Im running Ubuntu 10.10 Maverick Meerkat on my MacBookPro 7,1 and after updating, i couldnt boot anymore.
(it were 196 updates, even though it sayed "download and install updates" during the installation O.o !!) 
I have to say, that i didnt update my macbook to the newest firmware from MacOs X because i was afraid very new firmware might be not supported by ubuntu. (should i do that, before updating ubuntu again?)

So now i reinstalled Ubuntu and it suggests me, to run the 196 updates. What am i supposed to do? (i alreay fixed reboot, and sound.

Then i have 4 other problems:
First, after closing the macbookpro ubuntu goes to standby mode. Then when i open it again, i can hear the noise from it, but the screen stays black. Blindly i can type "sudo reboot" in terminal to reboot. That all i can do. How can i fix that?

Then, my MacBookPro gets very hot, even while just browsing and not even using flashplayer. What can i do about that?

Also, the rebootfix doesnt work correctly for me. Since i fixed it like explained [here]("https://help.ubuntu.com/community/MacBookPro7-1/Maverick#Reboot").
At least it powers off when I'm rebooting. But that goes so fast, that it looks like pressing shutdown for 5 sec (i get a purple screen for 2 secs and then my screen gets white for about 1/100 sec and then the MacBook is turned off and restarts. (shutdown also doesnt work right. Same procedure as rebooting) 
It just cant be right! How can I see what happens during shutdown? or how can i fix my reboot to work properly? 


My other problem is, that i run rEFIT as my bootloader, but after selecting "linux" i also get the GRUB Bootloder, so i have to pick linux twice before booting. How can i disable the Grub bootloader, so i dont have to chose linux twice every boot.

Thanks in advance
Steve

---

### Post by yugnip on 2010-12-18
Hi mosmetic,

Personally, I would keep the Grub menu, and here is why: The reason you cannot boot is a kernel update, more than likely. If you keep the Grub menu, you will be able to choose the older kernel and boot from it, should any new kernels give you trouble.

With that in mind, go ahead and update. If after booting you see a newer kernel in the Grub menu, try it out. If you are unable to boot, restart and use the older kernel.

You can hide the Grub menu, and also edit it to take out older and newer kernels if you like. But until you become familiar enough with things, I would let it ride.

---

