---
title: "High CPU usage from Xorg"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Chaoticwhizz on 2007-06-03
I run Kubuntu 7.04. I have the Nvidia card and am using the 1.0-9755 driver off the Nvidia website. If I walk away from my computer long enough and then come back Xorg will take all free processor usage. I can switch to tty1 and reboot the PC. It acts normally again until I let it sit for awhile. I feel it is either linked to the screen saver which I have tried several different ones, or possibly the power saving settings.Other weirdness is if I turn off the power management settings from the System Settings --> Power and Display what will happen is my screen will go blank after 5 min instead of the actual screen saver coming. It does this on standard 2-D scrolling marquee screen saver as well as 3-d ones. I originally installed Edgy Eft and then upgraded to Feisty using Adept. This problem never happened in Edgy and I don't even think it always happened since I have been using Feisty. I tried reinstalling the Nvidia driver with no luck. All 3-d apps run fine. This is the only problem I have.

---

### Post by Chaoticwhizz on 2007-06-07
Fixed by disabling SuperKaramba applets. Launchpad link

[https://bugs.launchpad.net/kdeutils/+bug/109507](https://bugs.launchpad.net/kdeutils/+bug/109507)

---

### Post by kokiperex on 2007-07-12
Same problem here in Kubuntu 7.04 and Nvidia, but I really like Superkaramba and it never causes any trouble before  :( .I will try disabling it today.

---

### Post by joao82 on 2007-08-04
i have the same problem, but when I move around the mouse the cpu load goes back to normal after some seconds.
I don't understand why switching to tty1 and rebooting. does your pc gets unresponsive when xorg uses all the cpu?

also using superkaramba, and i don't want to stop using it. but it's not good to get the cpu on 100% all the time when i leave the computer.
is there any way to configure xorg to make it stop doing this?

---

### Post by kokiperex on 2007-08-04
> **joao82 said:**
> i have the same problem, but when I move around the mouse the cpu load goes back to normal after some seconds.
I don't understand why switching to tty1 and rebooting. does your pc gets unresponsive when xorg uses all the cpu?

also using superkaramba, and i don't want to stop using it. but it's not good to get the cpu on 100% all the time when i leave the computer.
is there any way to configure xorg to make it stop doing this?

The GUI of my PC gets unresponsive (Xorg), so, I can see the mouse pointer, but the PC doesn't response to the mouse. I have to enter to console mode (TTY) to kill the xorg and login again.

Well, I stop using Superkaramba, and I think that was the problem (the PC was all night without freezing).

Too bad, beacuse I really like Superkaramba.

---

### Post by Chaoticwhizz on 2007-08-04
> **joao82 said:**
> i have the same problem, but when I move around the mouse the cpu load goes back to normal after some seconds.
I don't understand why switching to tty1 and rebooting. does your pc gets unresponsive when xorg uses all the cpu?

also using superkaramba, and i don't want to stop using it. but it's not good to get the cpu on 100% all the time when i leave the computer.
is there any way to configure xorg to make it stop doing this?
Basically, the mouse pointer would move but nothing would respond when clicked. Even if I let it sit for several minutes it didnt' change. It only seemed to happen after coming back from standby. However, anything that didn't depend on Xorg worked fine, hence why going to TTY was the only solution I could find to fix it.

Since I turned off Superkaramba several months ago, I haven't had this problem at all. I stll kinda miss it. The launchpad link doesn't seem to be resolved either. I wonder if this problem still exists in the Gutsy Tribe version?

---

