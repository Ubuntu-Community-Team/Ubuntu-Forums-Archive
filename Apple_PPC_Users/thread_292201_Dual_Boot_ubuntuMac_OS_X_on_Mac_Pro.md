---
title: "Dual Boot ubuntu/Mac OS X on Mac Pro"
date: 2006-11-03
forum: Apple PPC Users
---

### Post by shaninho on 2006-11-03
Hello, I have been following instructions from another thread on this site as well as bin-false.org/?p=17 and I am encountering a problem that I would very much appreciate help on. 

I was able to get to the reboot phase, after 

-using Boot Camp to create a 22 GB partition, 
-installing rEFIt, 
-rebooting with an ubuntu 6.10 iso burned to a CD, 
-starting the installer with the irqpoll and acpi=force options
-using a different version of the linux-restricted-modules (linux-restricted-modules-686 and linux-restricted-modules-generic on separate occasions with no discernible difference)
-using /dev/sda4 to account for the fact that my swap partition is /dev/sda3 and my boot vol is /dev/sda4
(-tried lilo -b /dev/sda4 but that really seemed to hose things up)
-entered the rEFIt partition editor and sync'ed the MBR & GPT tables successfully.

However prior to this final step, rEFIt was recognizing the linux drive (complete with happy penguin), but it would try to boot and then just go to a black screen with a blinking cursor. Also one behavior I noticed was that after choosing the linux drive, the boot would not happen successfully under other conditions that would freeze at the penguin logo in the center of the gray background.

Finally, after the MBR/GPT sync, rEFIt reported a "sterile Windows" icon and an unknown OS, and then choosing it would result in "Missing Operating System." 

It's worth noting that I can get into ubuntu by booting from the LiveCD and then choosing the boot from hard drive option. But then the performance is ultra-sluggish in terms of both mouse input and keyboard input. 

Any suggestions would be greatly appreciated. Thanks in adv. 

](*,) Thought this was appropriate!

---

