---
title: "Complete noob needs help with Grub and Video"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by ranker on 2007-03-01
Hi all,

I'm having some issues customizing my Edgy Eft installation and I'm looking for some help/pointers/hand holding.

1) I'd like to customize "Grub" so that  a) Only the latest update of Ubuntu is listed instead of like 4 different previous versions, b) Windows is the first option instead of the last option, c) the default OS loaded would be Vista instead of Ubuntu.  

I've managed to find the menu.lst in /boot/grub/menu.lst however it won't even let me edit the file.  For a first time linux user, even the options scare me so I'm hoping some of you could shed some light on which options I should change and how I should change them to get the desired results listed above.  I spent some time reading man pages but even then I'm a bit lost.

2) My wi-fi radar seems to just sit at "working" forever whenever I try to connect to a place.  Instead, I have to load up "System->Administration->Networking->Network Settings" in order to connect.  Kinda makes it pointless to have Wifi Radar if I have to use this everytime.  I'm wondering if this is a bug or if I had set something up wrong.  

Also, with either wifi radar or the built in network settings menu, I'm only able to connect to WEP encrypted routers.  Anything WPA, it appears as if it won't connect?

3) How do I see if my drivers for my ATI Radeon 9600 Mobility (128 mb) are updated and if they have the latest 3D drivers available?  I tried to install Easy Ubuntu and ended up having this garbled "xserver" mess that forced me to copy back some x11 config file.  


Thanks in advance for helping out an utterly clueless noob (who hopes to make Linux his new OS!)

Karl

---

### Post by ranker on 2007-03-01
Bump.  Still in need of help.  Thanks again!

---

### Post by rsambuca on 2007-03-01
There are a few ways to go about editing your menu.lst file. One method is to simply remove the entries from your menu.lst file (which is what grub uses for boot instructions). You can either 1. delete them, or 2. comment the entries out by putting a "#" in front of the lines you want to remove, or 3. you can change the line that says "howmany=all" to howmany=1, 

or if you are sure the upgrade is stable, you can remove the old kernels from your system using the Synaptic Package manager. If you search for linux kernel, you will see the versions you have installed, and you can remove the old ones.

If you are going to edit your menu.lst, you can use the gedit text editor by typing this command in a terminal:```
gksudo gedit /boot/grub/menu.lst
```

To change the default boot system to Vista (???) from ubuntu, change the number in the line that says "default 0" to the number that corresponds to Vista, keeping in mind that grub starts numbering at zero instead of one, and includes every line where "Title" appears.  (thus the line that says "other operating systems" is counted in the numbering.)

I also reduce the "timeout" line down to 2 seconds so you don't have to wait to boot into your primary OS, but you still have time to press an arrow key and stop the timer.  My Wife likes this so that for her it just goes into Windows quickly for her.  Someday she will learn to love ubuntu!

Sorry, can't help you with your wifi or ATI.

---

### Post by Dr. Nick on 2007-03-01
correction : the old kernels are called linux-image I believe. Removing the old ones fix grub automatically.

use **uname -a** to see the version you are using now

---

### Post by ranker on 2007-03-02
Thanks you two for the tips.  I think I got Grub working the way I like it now.  

However, I'm still at a loss on how to check to see if you have 3D enabled drivers as well as how I would obtain the latest 3D drivers for my ATI Radeon 9600 Mobility.  Part of my reason for choosing ubuntu was due to the awesome Compliz video. I'd love to get a chance to play around with an interface like that.  

Any one else have any ideas/suggestions regarding my ATI issue or wifi-radar problems?

---

### Post by ranker on 2007-03-02
I also have another issue.  I purchased a Logitech V270 Bluetooth mouse.  Ubuntu recognized it immediately.  However, my mouse wheel doesn't work.  I've searched for help through the forums, but none of their proposed workarounds help.

I've tried:

1) changing "ExplorerPS/2" to "IMPS/2"

2) changing the ZAxis button mapping from "4 5" to "6 7"

Further searching doesn't seem to turn up anything.

---

### Post by Dr. Nick on 2007-03-02
I have yet to get my ati card running in 3d, You can try a program called "easy ubuntu" to help you install them.


Not sure on the mouse issue

---

### Post by ranker on 2007-03-02
I tried using the Easy Ubuntu and followed its instructions (like choosing flxgr instead of ATI during the menu installation) but the resulting boot up of the OS was all jumbled. I had to replace it with a backup of xorg.conf.  

ATI cards don't have any linux 3D support?

---

