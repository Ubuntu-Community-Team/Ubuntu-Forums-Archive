---
title: "Xfree86 Resolution Problem,,"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Balvinder25 on 2007-07-01
hi all,
         i have installed ubuntu on one of the partitions on the computer and was 

just having a few problems setting up the display.The probs is i have a 14'microtek 

model 36f1 which is not listed in the monitor data base so i had to select a 

general one and specify the vertical and the horizontal refresh rates..ie..

HorizSync 35.5-55.5
VertRefresh 65.5-85.5
,,now it appears to be fine but somehow i  noticed that if i use the pc for more than 3 hours at 

one stretch i have an headache and the eyes start paining but the same dosent 

happen when i use windows xp..so it has to be the X settings ..so could please any 

one tell me the exact refresh settings for my monitor.?any help would be 

appreciated.

---

### Post by annda on 2007-07-01
in xorg.conf you can enter exact values, not only ranges. so the way to go would be to find out the exact values you use with windows and enter the same numbers in xorg.

my advice is to check your monitor menu when running windows (all monitors are different so i can't tell you what buttons you should use), note down the numbers and modify xorg.

---

### Post by Balvinder25 on 2007-07-01
hi ,
     thxz for the response...how do we find out the refresh rate in windows??i would just like to use my monitor at 800*600 @85hrtz..i know this is the setting needed but what are the exact refresh rates..dont we have a calculator some where  from where we could convert these and then modify the conf file??

---

### Post by annda on 2007-07-01
can you try your monitor? the 85 is the vertical refresh rate, but it is not necessarily exact - it can be 84.6 or 85.4... when you use the monitor's menu, you can go through all the screens and one of them should show you at what rates it is currently running. mine shows 64.4 kHz and 60 Hz (it's an LCD, so that's why it's so low). can you do that too?

---

