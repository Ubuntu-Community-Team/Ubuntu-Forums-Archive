---
title: "cannot find episodes... and other related problems"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by beanco on 2008-04-01
I have been loaned a dvd of a series to watch.

If I put the disk in Totem launches and plays episode 1, no questions asked. 

I cannot find episode 2, or 3, etc.


If I try to watch it in vlc, I get goofy messed up stuff.. lots of  green and some redish squares. I can see a menu to choose episodes but it is not active.
(actually get this if I try to open the files in Totem as well...)

Mplayer does not read the disc for some reason *error opening/initializing selected video_out (-vo) device*


On the stand alone DVD player I can choose any episode and play it...


Actually, the episode I could watch in Totem was over one hour long... as fi all 3 episodes just playe back to back without any notification that there are seperate episodes... I will have to check the length of each ep. on the stand alone DV player.

The series is The Wire, BTW.

Robi

---

### Post by taavikko on 2008-04-01
change the video output module in vlc
tick the advanced settings box...
preferences->video->putput modules 
save settings.

And try again.

I would use vlc to watch dvd cause.
totem-gstreamer doesn't support menus quite yet :(

---

### Post by beanco on 2008-04-01
taaviko,

woudl that be out modules?

and in there what do I do?


thanks/kiitos (sp?)

robi

---

### Post by taavikko on 2008-04-01
> **taavikko said:**
> change the video output module in vlc
tick the advanced settings box...
preferences->video->**putput** modules 

putput modules, whups :) small typo.

Yes, video output modules change from : Default 
and try different ones.

Your welcome/Ole hyvä

---

### Post by beanco on 2008-04-01
kiitos!

will try later.

robi

---

