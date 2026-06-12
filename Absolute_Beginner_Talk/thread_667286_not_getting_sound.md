---
title: "not getting sound"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by ravikrishnakatta on 2008-01-14
i installed ubuntu before two days only it was busy with configuring stuff till the time i realised was not having sound output


my touchpad controller(HP pavillion dv6516tx) always shows red muted i even tried to reboot logged in to vista unmuted the sound as i keep it muted most of the time in it then re booted and entered in to ubuntu and as ubunut loads the light turns red tough the touch pad button works i mean if i tap it mutes and unmutes in ubuntu but remain red i.e the device is still off

---

### Post by torakiki on 2008-01-21
I've the same issue.
A fresh installation on my new HP Pavillion dv9670el.
I found tons of posts of people having problems with sound using Gutsy on HP laptop but i didn't find a solution.
Any suggestions?
Thanks
Andrea

---

### Post by emarkd on 2008-01-21
Have you tried specifying your sound device?  Under System-Preferences-Sound on your menu, the default setting for each item is 'autodetect'.  On one of my systems, I got no sound playback until I specifically selected a playback device.  In other words, 'autodetect' didn't work for me.  I just tried everything in the 'sound playback' list until something worked.  Worth a shot...

---

### Post by torakiki on 2008-01-22
Didn't work. I'm going to follow an HowTo to update alsa drivers. It seems there is a lot of people with problems using ubuntu on hp dv 9000 serie...

---

### Post by torakiki on 2008-01-22
found the solution [here]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller") method G but it seems it's a workaround abyway it worked.
Andrea

---

