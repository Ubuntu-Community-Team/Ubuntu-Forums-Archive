---
title: "How to remove xpti.dat from Mox/ Opera dir"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by Blur-king on 2006-05-13
Hello everyone, I am new to ubuntu so please bear with me if I ask silly Qns. Anyway I got a copy of Ubuntu Breezy from a pal who gave up. Had been fiddling with and by scanning the forum managed to get the Computer to run. Was able to install Opera also after many... tries. Anyway, after installing flashplayer from adobe had the above message. I have been living in the windows world for a long time and had been fortunate with ubuntu til now. 3 days and counting. Can anyone help or direct me to the correct howtos as for the last 4 hours unable to find anything on the forum yet. seeing lots of **** already.  thank you ( I need a break )

---

### Post by Papa-san on 2006-05-13
I am currently looking for the same information... Just installed the flashplayer, and have never manually removed anything...

---

### Post by oli_88 on 2008-03-11
I'm still learning too, but this seems to have done the trick.
 cd .mozilla/firefox/h6zpac4w.default
Thats the directory it was in.
Then rm -i xpti.dat
Deleted the file

I ran locate xpti.dat first to make sure that I was in the right directory and after to make sure it was gone.

Hope that helps.
If its wrong, someone let me know? Thanks.

---

### Post by SGT Smilez on 2008-05-23
Thanks that worked perfectly.

---

