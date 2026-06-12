---
title: "Live CD boots to Black Screen"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by dmiller622 on 2006-10-29
Well I have done so many searches in this forum and found users with the same issue but unresolved. 

 My wife system has a similar PC as mine but she has a ATI 9600 and she is using the on Nvidia Sound Storm sound plus she has a standard CD-Rom drive and the Live CD works.

 I am using the same video card drivers as her but I have it down to 2 items they may be causing my issue. One the Audigy 2 ZS or I do not have a standard CD ROM Drive.

 Is there a known issue with the Audigy sound cards with the live cd. I really would like to try it out before I install it and it looks good on my wifes PC. But she does not want it installed on her PC. It is frustrating not able to view on my PC. I get to the menu and then I choose VGA and I did choose safe mode the same thing black screen.

 I hope I get some help from anybody in the community or from Ubuntu. This is my last try and I am moving on and sticking with Microsoft which I hate to do.

Thank you



System
XP1800+
Abit NFS -2.0
2 gig of Corsair ram
ATI 9700 PRO
Creative Audigy 2 ZS
DVD-CD drive/burner
I do not have a standard CD-Rom Drive
View sonic 19 P95f + Monitor
Western Digital IDE HD

---

### Post by Scunizi on 2006-10-31
I've had the same problem and filed a bug [https://launchpad.net/distros/ubuntu/+bug/69609](https://launchpad.net/distros/ubuntu/+bug/69609).  I have a dual head nVidia 6600gt with two monitors plugged into it, one CRT and one DVI.  If I unplug one of them everything boot fine.

---

### Post by devilsadvocate1987 on 2006-10-31
There is a possibility that this is a combination of a couple of things. 

On some (very) older cards, for instance, the bootsplash doesnt really work too well. It has something to do with the settings as well. It could be that there is something wrong with the splash. From the boot up kernel arguments remove the splash and the quiet keywords and check at which point it gets stuck. You can change the flags in the Advanced Boot Options if I remember correctly

---

