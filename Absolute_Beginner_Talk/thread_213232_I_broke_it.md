---
title: "I broke it"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by dusty1usa on 2006-07-11
I swear, I can break anything. Got Ubuntu installed on it's own hard drive mounted as a slave on IDE1, put the Ubuntu boot mgr on the second partition on the XP master drive (didn't want to put it on the same partition as the XP MBR) all ok. Got XP on it's own hard drive mounted as master on IDE1. (this drive has 3 paritions, C: for the OS, D: for programs and E: for file storage)
Got a free boot manager loaded (OSL2000) (well sorta free, you have a nag screen to click past if you don't pay em $25)
Anywho, it all works pretty slick. Start the computer, OSL 2000 screen comes up and you can choose what partition to boot into. 
Can choose to boot either XP or Ubuntu. No problems at all. 
Except......Ubuntu doesn't have a screen resolution that fits my monitor (Acer 19" widescreen with a 1400 x 900 res)
Well....1280 x 1024 don't look too bad so I'm checking out the screen savers included in Ubuntu. Going along clicking on the different ones and BAM! All of a sudden this one screensaver causes Ubuntu to crash bigtime. The mouse goes nuts and is uncontrollable. the little screensaver window gets all weird. And the thing is locked up tight as a drum. Only recourse is to hold the power button in til it cuts off. 
So how in the heck can I disable the screen saver if everytime I open the screensaver window now it breaks Ubuntu? 
I just know somebody here has a simple fix. From what I can see, you guys have it all covered pretty well. 
Thanks for reading this long post and any suggestions will be appreciated. I can always just wipe this drive and re-install Ubuntu. Prolly be the easiest solution but I thought I'd check in whith the experts first. 

dusty

---

### Post by DSn0wMan on 2006-07-11
Three words

sudo dpkg-reconfigure xserver-xorg

This command will help you choose video drivers, screen resolutions, and just about anything else involved with xserver.

---

### Post by dusty1usa on 2006-07-11
Hey thanks DSn0wMan, that works. All is kewl now. This looks a lot better and the screen saver likes it a lot better. 

dusty

---

