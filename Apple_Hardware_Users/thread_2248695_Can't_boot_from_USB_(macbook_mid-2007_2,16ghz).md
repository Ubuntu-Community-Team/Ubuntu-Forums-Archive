---
title: "Can't boot from USB (macbook mid-2007 2,16ghz)"
date: 2014-10-16
forum: Apple Hardware Users
---

### Post by cmddata on 2014-10-16
Hey guys,

I'm having a long and hard journey to get ubuntu on my macbook mid - 2007; 2,16 ghz, 2gb ram, macos lion.

ihave tried the latest Ubuntu and 13 for mac iso from the official site and verified the data with bittorrent.

i have followed the mac os  terminal tutorial to make my usb device bootable.

i have installed (after everything failed) " refit" , linux usb loader, ubootin-mac.

All my alternative routes bring me to either no tux , or a tux that gives me the following error : 
Error not found returned from legacy folder.
Error not found from localdevicepath (x15)
Error loading while reopening our installation volume.

The firmware refused to boot from the selected volume..

I have read every forum post on this and tried a numerous amount of tutorials.

Please i'm begging you wont someone give me UBUNTU!

(just did another attempt, and again nothing. you know the funny thing is that no matter what i put on this usb or any other usb holding the alt/option key NEVER shows usb boot, i always need refit and then it gives me wonderful splendid errors)

(also i noticed that when i do the conver iso to img (dmg) method i dont get to see tux , and it just says legacy, but when i do the mac linux usb app way i do get tux but same story.)

---

### Post by Bucky Ball on 2014-10-16
Please stick with 12.04 LTS or 14.04 LTS as they are the only supported versions at the moment. Sorry I can't help as no Mac expert, but I did suceed in bumping your thread. ;)

---

### Post by QIII on 2014-10-16
And I'm going to bump it again to say this:

Installing on Apple products is often its own special sort of trip to Hades.  Don't take this as an indication that Ubuntu itself is typically as difficult as this.

---

### Post by Kale_Freemon on 2014-10-17
Do you happen to have a Windows machine available? You may be able to make a bootable USB with that and Unetbootin (there is a Windows version). If not, then you might be able to try installing Ubuntu in a virtual machine with VirtualBox and then adding your USB device to it via the devices menu and then using Startup Disk Creator inside the Ubuntu VM to make a bootable USB disk. That may work.

You may also want to try the normal, non-Mac, ISO. This is what I used on my 2008 Macbook and it worked fine.

---

### Post by cmddata on 2014-10-17
Thank you all for your replies.

I had indeed tried your approach, in fact i had tried 15 different .iso's ranging from amd64 ,mac, windows to i386 to virtualbox , parallels and vbware fusion.
Sad to say the least this was all in vain.

Well then later that evening i felt kinda funky , and thought " why not make a win8.1 bootable usb with bootcamp since its fully supported LOL" . 
And guess what NO BINGO AGAIN. The usb flash drive wont show up with ALT/OPTION and i get the same beautiful and loving errors with refit boot.

So then i did some searching on forums and tutorials to see if i missed anything, which led me to the following conclusion; this usb flash drive is not suitable for mac booting, it is for windows, but not for mac.

So i to help future troubleshooters out there i will post the name; Verbatim; store and go media. 

As soon as i try a different usb storage device, i will update this thread.

Best regards,

cmddata

PS : Just installed ubuntu on my 2 other windows systems easy as PI, i hope nobody is standing underneath my window because this macbook is going to take flying lessons

---

### Post by coffeecat on 2014-10-17
You posted in the Mac OSX sub-forum which is for:

> Support for Apple's OSX operating system.

I've moved this thread to **Apple Hardware Users** which is for:

> Support for users who are using Apple Intel or PPC based systems with Ubuntu.

---

### Post by este.el.paz on 2014-10-17
To the OP, is your macbook a 32 bit or 64 bit unit?  Might make a difference, or not.  Other question, if you are having a problem booting USB, why not try burning to DVD and boot the "live" desktop using "c" key . . . and try out your choice; would agree with BB that 12.04 or 14.04 are your best choices.  Seems like I've seen threads here about that say that if USB isn't booting to use DVD.

First try to boot the live desktop iso . . . burned to DVD.

e.e.p.

---

