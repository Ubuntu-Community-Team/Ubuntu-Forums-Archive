---
title: "Wine 0.9.21 crash old fix no work!"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by nu2this on 2006-09-25
I just installed Wine 0.9.21 & it crashes when the audio tab is clicked. So I used a fix  from a thread on this topic. When I used that fix for 0.9.15 it worked but as all can see it's not working for 0.9.21 does anyone have any ideas?



rleeish@EMMA-desktop:~$ winecfg
__driCreateNewScreen_20050727 - succeeded
__driCreateNewScreen_20050727 - succeeded
Creating link /home/rleeish/.kde/socket-EMMA-desktop.
can't create mcop directory
rleeish@EMMA-desktop:~$ mkdir/tmp/ksocket-rleeish
bash: mkdir/tmp/ksocket-rleeish: No such file or directory

---

### Post by pay on 2006-09-25
Do you have a link to the patch?

---

### Post by nu2this on 2006-09-25
Solved:D  No More wine mcop stuff!!!
this thread [http://ubuntuforums.org/showthread.php?t=153509&highlight=wine+crash+alsa](http://ubuntuforums.org/showthread.php?t=153509&highlight=wine+crash+alsa)
That's what did it Thanks & Praise Be for topgi!

---

### Post by pay on 2006-09-25
So how did you do it? I couldn't find a file called /usr/lib/wine/winearts.drv.so

---

