---
title: "Clamshell 466 screen problem dual boot OSX and Ubuntu"
date: 2007-12-04
forum: Apple PPC Users
---

### Post by ibech on 2007-12-04
Hi everybody!
As I am a newbie to linux and ubuntu, following problem. I have an ibook clamshell 466mhz running OS9, OSX 10.4.x and since las week Ubuntu 6.06. When I installed Ubuntu from the alternate CD, I got this awful "split screen", means the screen is split horizontal and the two halfs are swapped. After googleing one night and a crash course in console typing I found a solution that worked: In the xorg.conf I set the "HorizSync" from 28-51 to 30-40 and the "Vertfresh" from 43-60 to 60-70. Now Ubuntu looks fine. But Mac OSX is wrong now...no way to work with it without doing the setting back:( 
Anybody here who has both systems running fine on this clamshell? Can you post your xorg.conf, so I can set it up properly? Other ideas? Thank you!

---

### Post by ibech on 2007-12-04
Problem solved! 
Couldnt wait for an answer - just played around with different numbers... HorizSync 28-40 and Vertfresh 43-70 is the setting for both systems working:-)
(as the clamshell ibooks have different LCD screens built in, mine is a samsung LT121SU-123)
That was really easy! Now I have to look how to set up the airport card with WPA encryption, wahh...

---

