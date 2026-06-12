---
title: "I Get A Blank Screen After Switching to Nvidia Drivers"
date: 2013-06-21
forum: Apple Hardware Users
---

### Post by teamcoltra on 2013-06-21
For starters, this thread is opened after days of trying - if you solve this problem for me, I will buy you a beer (assuming you live in a country that I can paypal you beer money :D ):

I have a Macbook Air 3,1 - I followed these instructions to a T [https://help.ubuntu.com/community/MacBookAir3-2/Raring](https://help.ubuntu.com/community/MacBookAir3-2/Raring) (except that for whatever reason, my mac will not boot into the +mac distro, I have tried redownloading it, I have tried putting it on different drives, I used unetbootn and startup disk creator -- everything, it just wont work).

I get through the ubuntu loading splash, and then my screen goes blank, I would say "goes black" but it doesn't even have a backlight. It is like the computer is turned off except that you can hear a faint fan sound. 

Things I have already tried (and pretty much in every combination of them):\
* used the nvidia 310 driver from the driver selection screen
* used nvidia-current from a ppa (with the nvidia-xconfig script)
* used nvidia-experimental-310 from terminal (with the nvidia-xconfig script)
* used a custom xorg file from this bug report: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-310/+bug/1159269](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-310/+bug/1159269) (the second one)
* Tried finding religion, asking God for help - based on the suggestion of these nice suited guys at my door, didn't work.
* Installed grub-pc and removed grub-efi
* Used default partitions (for grub-pc) and used snapshot partitions
* Used boot-fix hoping that helped with grub-pc 
* Installed Salamander and LTS - neither worked
* Tried installing 32 bit OS but the machine wont boot into it

Debian 7 didn't seem to have as many problems when I used that but it still felt buggy and I am guessing it was because Gnome3 doesn't use the same hardware acceleration, if I was to do something graphical I am guessing the problem will still occur (but I don't know, I don't really want to use Debian). 

-- if I find a solution, I will certainly update the thread, but in the meantime if you want to help me work through this in real time and use IRC I am teamcoltra on FreeNode.

---

### Post by 2F4U on 2013-06-22
This thread deals extensively with the black/blank screen problem:

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

You may be able to find a workaround by going through the diagnosis steps.

---

