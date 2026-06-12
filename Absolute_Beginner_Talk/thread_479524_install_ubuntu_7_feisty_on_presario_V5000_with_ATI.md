---
title: "install ubuntu 7 feisty on presario V5000 with ATI radeon 200m and broadcom wifi"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by edwin.e.johnson on 2007-06-20
I thought i would write this because i made the leap to Ubuntu from windows not to long ago and i had some trouble getting everything to work right out of the box.... i was lucky to have this forum to fix every problem i have had. the only problem was none were specific for my lappy...

so first off download ubuntu 7 feisty and burn to live cd

after my install of Ubuntu (dual boot) with winXP my wireless card was not supported

wireless card - broadcom 4318 or some sh*t took me about 6 hrs to find the fix for this but it worked and havnt had a problem since...

to fix wireless you need the 43xx Linux driver or the windows driver with ndiswrapper

"""ndiswrapper - uses the windows driver for the wifi card"""

i found a complete file that has both in the package---------- plus it had an installer program "like an exe"  that installes the drivers for you... easy right.. you can get the file here 

[http://darkn00b1971.googlepages.com/bcm43xx-gtk-installer-0.1.tar.gz](http://darkn00b1971.googlepages.com/bcm43xx-gtk-installer-0.1.tar.gz)

ok after you download that unzip it to the desktop......
 now open the folder and double click th file named

"""    installer.py    """

select " RUN "

a window pops up you can use the " firmware" driver or "ndiswrapper" the windows one.......

the firmware is limited to 11mbs..... so i used the windows driver  "ndiswrapper"

when using the windows ndiswrapper driver you must be connected to the internet while you install it....

ok so it gave me some trouble the first time i tried to install it i just uninstalled the firmware... its and option on the same menu.... and tried the ndiswrapper again and it worked.....

the howto for that is also located here   [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

REMINDER GET ALL UPDATES NOW - should be an update icon blinking in the dekbar after being connected to the net for a little bit

ok now that your wifi is working you will want to enable your ati xpress 200m video card...

this is easy

look at the task bar see where it says "system"? good click it

go to """" system/administration/restricted drivers manager """""


easy right just click enable and restart..

now the hard part for me was getting the 3d desktop effects working which by the way i figured out thanks again to this awesome forum!

 there is a complete how to at the page im about to list here.....  but remember  if you dont want the beryl effects... "which are the sh*t super cool" just stop where this howto tells you to  LOG OUT and login to gnome xgl.....
i suggest the beryl effects!

anyhow that having been said here is the howto

[http://ubuntuforums.org/showthread.php?t=399643&highlight=xgl+feisty](http://ubuntuforums.org/showthread.php?t=399643&highlight=xgl+feisty)



well thats my post hope it helps some people....

---

### Post by -Vampyre- on 2007-06-26
Man lucky you. I just tried that exact same method for Beryl and when I log in to check the xgl session. I loose my wireless connection. says it is there, but I can't ge tto the internet. will try again another time.

---

