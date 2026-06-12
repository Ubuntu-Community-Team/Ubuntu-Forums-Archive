---
title: "Dismounting an external HDD"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by trudetski on 2007-06-30
I have a  250GB Seagate FreeAgent external HDD. I have been able to connect it to Ubuntu 7.04 and was also able to set it to read/write despite it being formatted for NTSF, I have a dual boot with XP. I was generally happy with the results until I tried to restart Ubuntu. Upon doing so the computer lagged just after the screen went black and showed a blinking cursor in the top left corner. I could not edit text and I let it sit for 10 minutes or so and it did nothing. I then turned off the machine manually but when I rebooted I found it had the same issue when GRUB tried to start up. I turned it off again, restarted and to my surprise GRUB loaded up just fine and I went back into Ubuntu. Once there, however, I found that Ubuntu could not find my external HDD. I also tried XP and it cannot either. The only fix that I have been able to figure out is to unplug the drive while the computer is off and then plug it back in once the OS loads.

I have been messing around with it on the Ubuntu half and have discovered that if I right click the drive and select "eject" it will not let me and it gives me an alert message telling me so. What I assume is happening is when Ubuntu turns off it does not dismount/eject the drive and that is causing the problem. Is there any workaround or possible setting to fix this problem? Thanks.

---

### Post by Edible_Monkey on 2007-07-29
Hi trudetski

It sounds as though (when you reboot your machine with the External HDD connected) your machine is recognizing your External HDD as a boot device, and as a consequence, is trying to boot from it... (the black screen with flashing text cursor). You may want to check to see if your machine is set to boot from an external device first.

Secondly,, the eject problem. This exists with many External HDD's out there, your not alone. a good snippet of code for you jot down:

*sudo umount -lf [MOUNT POINT]*

a typical example would be: *sudo umount -lf /media/disc*

_Breakdown:_   the '-lf' is worth an explanation. the 'l' calls the 'lazy' parameter, this will detach the filesystem and clear up any references to it. The 'f' calls the 'force' parameter, this will force the filesystem to unmount in case of any unreachable devices.
  
*umount* will simply allow you to unmount your external hdd before you turn the machine off. (This code is used if right clicking and pressing 'eject' fails).

Hope this helps

---

