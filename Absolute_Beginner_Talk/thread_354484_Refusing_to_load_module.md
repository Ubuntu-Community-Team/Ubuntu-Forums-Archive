---
title: "Refusing to load module"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by shadowboxer_k on 2007-02-06
hey guys,

before i start, i'd like to let you know that i am not very good with computers at all.

okay, so yesterday i wanted to install ubuntu 6.10 on my old and tortured IBM ThinkPad ( 800Mgz/ 256MB/ 20Gb/) and finally get rid of windows. i booted the computer from my ubuntu cd, and then i got a menu with several options. i chose "start or install". and then, my problems began.
after the pretty black loading screen, i got a black dos like black screen saying something like "error loading module". after that, it disappears and it looks like it is finally starting to load ubuntu, but it is extremely slow and it stops at the beige screen and that's it. ubuntu never loads. 

a couple of days ago i wanted to check out kubuntu and a similar thing happened. it was extremely slow but it finally loaded. now ubuntu doesn't load, and kubuntu doesn't either. i just don't know what to do. 
 
do you please have some advice on what the reason might be? or how to install ubuntu some other way? is it possible to do it from an external cd drive? 

please help!

thanks so much!

---

### Post by Scarlett on 2007-02-06
You can boot from an external drive.  Download the live CD from a bittorrent as an iso and burn it to a CD.  Use the lowest setting your system is capable of.  Usually 4x is recommended but I've gotten away with 8x.  Before you begin, it's a good idea to back up any files you can't live without... just in case.

Restart your computer and as it's booting up it should tell you which key(s) to hit to get into BIOS.  (On mine it's either <tab> <del> or F4, yours may be different.)  That should bring you to a blue DOS-like screen that you can navigate with the arrow keys.  Under "advanced BIOS options" choose "boot priority" and switch the first entry to USB-CDROM.  Save your settings and exit BIOS.  

Your system should now look at your external drive first and load up the install CD you've just created.  This will walk you through the partitioning and user creation.  After you're done installing there's a lot of updates and you'll probably be prompted to reboot.  As long as you're doing this, go ahead and get into the BIOS again and change the boot priority back to whichever hard drive you just installed Grub on.   Good luck!

---

### Post by shadowboxer_k on 2007-02-06
scarlett, 

thank you for the reply! 

in the meantime, i did some research and found that that actually you can't install ubuntu 6.10 on an IBM ThinkPad21 with the regular install cd. you have to use the alternate install cd. so, i will try that tonight after i'm done with work :)  wish me luck!

and thank you again. i still can't believe how kind people in this forum are.

---

