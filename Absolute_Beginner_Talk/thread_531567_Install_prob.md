---
title: "Install prob"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by clickquick on 2007-08-21
I downloaded ubuntu 7.04 and made a cd for it. Rebooted system and it booted from the CD. selected the install and it goes through it's thing then came up with an error 

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

Any ideas what my problem might be?

---

### Post by clitmaster on 2007-08-21
yea i had a similar issue a while back

it turned out the problem was that i was trying to mount a FAT32 partition as /home...

actually, maybe it was something else. nevermind!

---

### Post by sumguy231 on 2007-08-21
> Any ideas what my problem might be?
Something's wrong with the configuration, maybe it's trying to use the wrong video driver or something. When you get to the terminal, type:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and enter your password. Go through the configuration there. If you don't know what to answer for something, leave it alone or ask.

---

### Post by clickquick on 2007-08-22
Well not entirely sure how to get to the command prompt so I tried to hit F4 and change the resolution then do an install. I had the same error but for some reason doing it this way put me at teh command propmt after the error message unlike whne it was on the default setting. I was able to set it to an ati driver but after that i didn't know how to get the install going again so I was stuck.

Had to unplug the machine to get it to turn off even cause after hitting the power button it kinda froze up on me. Guess this section is deffinately for me lol (newbie)

---

