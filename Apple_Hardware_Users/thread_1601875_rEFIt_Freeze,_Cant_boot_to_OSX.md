---
title: "rEFIt Freeze, Cant boot to OSX"
date: 2010-10-20
forum: Apple Hardware Users
---

### Post by SevenDayFestival on 2010-10-20
Hey y'all!

I do not have ubuntu, but I have seen people talking about booting with and customizing rEFIt here, and this seems like a knowledgeable place to seek advice.

So here's my problem:

I have a macbook pro on which I have OSX 10.5.8 and Windows7 x64 (installed through bootcamp 3.1).  I downloaded rEFIt and tried to modify the rEFIt interface following the instructions here: 

[http://colinharrington.net/blog/2009/05/customizing-refit-an-efi-bootloader-intel-macs-slick/comment-page-1/#comment-3970](http://colinharrington.net/blog/2009/05/customizing-refit-an-efi-bootloader-intel-macs-slick/comment-page-1/#comment-3970)

After trying to change the background (hostname.bmg) to a different image rEFIt opened to show the new background (.bmg file) but nothing else (no mac or windows logos like previously) so I can't select an OS to boot to!! 

I can still hold down the option key during startup to bring up the regular bootcamp menu which allows me to choose between my bootcamp partition (with windows 7) and what is now called the rEFIt partition (previously called Macintosh HD before I installed rEFIt)  So I CAN boot to windows, but cannot boot into OSX without going through rEFIt, which is not showing me any options to choose from.

The modifications I made to rEFIt were through the rEFIt.const file in the rEFIt folder in the efi folder on my Mac partition.  This const file now reads:



 timeout 20
banner hostname.bmp
selection_big   selection-big-ring.bmp
hideui tools shell funcs hdbadges label
legacyfirst


I can see and read my mac partition in windows, but cannot save to it to reverse these changes I made to the .const file.  I was also hoping that the timeout in rEFIt would automatically talk me into OSX even though I cannot see any icons, but after 5+ minutes waiting on rEFIt nothing happens.  Also, I made sure not to list badges under hideui so they should still be shown.



So my Q is: 



How do I circumnavigate rEFIt to boot to OSX so I can reverse these bad changes I made


OR does rEFIt have shortcut keys that may let me circumnavigate its GUI?



OR is there a way I can change the rEFIt.const file on my OSX partition while booted in windows and save it back to the OSX partition?



Thanks!!

---

### Post by SevenDayFestival on 2010-10-20
Woops! had the wrong link to the tutorial I was using... the right one is: [http://colinharrington.net/blog/2009...el-macs-slick/]("http://colinharrington.net/blog/2009/05/customizing-refit-an-efi-bootloader-intel-macs-slick/")

---

### Post by SevenDayFestival on 2010-10-20
any by .const I definitely meant the .conf file

---

### Post by teejmya on 2010-10-21
> **SevenDayFestival said:**
> 
 timeout 20
banner hostname.bmp
selection_big   selection-big-ring.bmp
hideui tools shell funcs hdbadges label
legacyfirst


Does your mac have a firewire port? If so, you'll have to borrow another mac and connect them via Firewire. Boot and hold down T. You're hard drive should appear on the borrowed machine. You can then edit your refit.conf file, preferably without "hideui," (which I'm assuming is causing your problem.)

---

### Post by SevenDayFestival on 2010-10-21
@teejmya Hey thanks for the reply!

I got around it by booting to my OSX install CD, using the startup disc utility in the drop down menu and selecting the mac HD to boot from.

Now my question is if anyone has successfully changed the banner image of rEFIt?  I've tried it once more since with another bitmap and it did the same thing but with the different picture. If however, I leave out the banner hostname.bmp (like below) rEFIt works just fine with my other settings:

timeout 20
#banner hostname.bmp
selection_big selection-big-ring.bmp
hideui tools shell funcs hdbadges label
legacyfirst

so it is definitely the hostname.bmp that is messing things up...does this .bmp need to be a specific size?  Any ideas?

Thanks!

---

