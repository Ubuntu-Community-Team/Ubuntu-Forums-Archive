---
title: "Desktop Off Centre"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by A.Scotchmer on 2006-12-23
Hi

Just got a new Medion PC and Ubuntu install with no problems.

The PC came with a 15" flat screen monitor but the desktop is off centre.  When Windows XP boots (the wife's chosen OS because the IME is better for her when typing Japanese) the desktop is bang in the middle.  With Ubuntu it is off to the right.  Its only slight but obvious as half the power off button (top right) and half the waste bin icon (bottom right) are mssing.

I have fixed it using the horizontal controls on the monitor but that throws Windows out.

Is there a setting within Ubuntu that will position the desktop right in the middle of the monitor.  

Thanks and merry xmas
Andrew

---

### Post by PriceChild on 2006-12-23
I get this on my nvidia card if I have the nv driver enabled... switching to the proprietory "nvidia" driver puts it in the same place.

What graphics card do you have?

---

### Post by A.Scotchmer on 2006-12-23
Its an AGP VIA/S3G Unichrome IGP

not the best from what I here but perfectly fine for my use (I'm not a gamer).

Andrew

---

### Post by ajgreeny on 2006-12-23
I have an ati 9200SE card running the open source ati driver and have the same problem as you but overcome it with the auto setting button on the monitor; a single click put everything centred again.  I so seldom use windows that I don't care about this any more, though it did annoy me at the start when I was using windows mostly.
If your monitor has an auto button give it a try.

---

### Post by A.Scotchmer on 2006-12-23
Thanks for that tip.   My monitor does have an auto button and it worked with one press.  Doesn't solve the issue but an efficient work around.

Thanks

Andrew

---

### Post by trtech on 2007-01-16
Same problem here. I have a 17" Dell Flat panel (E171FP, to be exact). In kubuntu, I have to set the monitor's horizontal position to 37 (centered = 50). But for me this is a problem not only when I boot this machine to Windows. I have 4 other machines on a KVM switch... Sorta defeats the purpose if I have to adjust the screen settings every time I leave/return to kubuntu.

I believe the problem has to do with KDE. I had the same issue w/ SuSE 9.1, and I fixed it using SaX2. (Easy - open SaX2 and a few clicks to nudge the screen...)

I think we need something similar in kubunu.

Cheers,
Chris

---

### Post by trtech on 2007-01-16
**SOLVED:**

Open terminal, type "xvidtune", press enter, **READ THE WARNING**, then use left and right buttons to nudge. Use the test button to test and then apply when it's right.

I *think* you cannot harm your monitor as long as you don't change the synch rates but _I don't know for sure_.

Cheers, 
Chris

---

### Post by trtech on 2007-01-16
Oops - not solved. 

The setting does not stick after rebooting. Anyone know how to make it stick?

Cheers,
Chris

---

### Post by trtech on 2007-01-16
Ok, once again, solved! (I think I'm going crazy, carrying on a conversation with myself.)

You have to edit xorg.conf:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)
Scroll down to **How to adjust position of your screen?**

---

### Post by xpod on 2007-01-16
>  	Ok, once again, solved! (I think I'm going crazy, carrying on a conversation with myself.)

Just dont get  banned for saying something about yourself you might regret;)

---

### Post by old_geekster on 2007-01-16
I have the same problem after installing Ubuntu 6.10.  I found that the problem is caused by the "Refresh Rate".  My cure is to do the necessary adjustments and then set the "Refresh Rate".  Everthing is in the middle when I get done and it stays.  As long as, I leave the "Refresh Rate" the same.

---

