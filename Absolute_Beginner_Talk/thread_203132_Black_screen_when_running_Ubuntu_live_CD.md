---
title: "Black screen when running Ubuntu live CD"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by pizzat104 on 2006-06-24
I tried to run Ubuntu off the live cd to give it a test run on my HP laptop. Using the default boot options, I get through most of the setup without any problems. I hear the startup chime but then my screen is black.

I can get to the console by pressing ctl+alt+F1. All the messages seem to say okay. The last thing that appears is xscreensaver-command: no screensaver is running ondisplay :0.0.

I think the problem is with my video card/its drivers. I have an ATI Mobility Radeon graphics card. 

I've tried searching around the forums for answers, but haven't found anything explicit telling me how to take care of this. Please help!

---

### Post by CarpKing on 2006-06-28
I have this problem with the Dapper Live CD as well (ATI Radeon too).  If I go into console mode and follow the procedures for installing the ATI binary drivers ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI))  I can get x to start; however, the background is screwed up and it pops up an error about another panel running and then I get kicked back into console mode.  I got a dapper install working with a similar procedure, but it had to be restarted to work properly, which is a problem on a live CD.  I'd suggest maybe getting the 5.10 live CD, as this worked fine for me.  It won't be exactly the same as Dapper, but it will give you some idea of what Ubuntu is like.  Then you can install 6.06 if you want.

---

