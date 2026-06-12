---
title: "X Server Saga"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by space2k on 2007-04-07
I've been working on this problem for days now - I've searched these forums endlessly and tried dozens of seemingly logical solutions, but can't seem to get anywhere. I'm desperate for help! Any assistance will be deeply appreciated...

First, I have a system76 Ratel desktop that I've owned for about 3-4 months. I cheaped out and went with the VIA onboard graphics. Everything was fine and I was really digging Ubuntu (this is my first linux experience) until last week, when suddenly my system won't load xserver - "Fatal server error: no screens found". 

So I search these forums and try dpkg-configure xserver-xorg. No progress. 

I edit xorg.conf. In various ways suggested by some threads here. Still the same error. OK - so I decide to completely re-install (I have to use the alternate CD, since X won't load). So I re-install 6.10. X Server failed to start. Damn. I try to install 6.06. Again X Server failed to start. 

At this point I think that maybe my on board graphic chip is bad - so I install an Nvidia 6200 AGP card. Same deal. I try to install the invidia drivers - nothing. Just for kicks, I pull the Nvidia card and re-install 6.10 while using the on board graphics again. Same deal.

So - I get the exact same errors every time -
* X Server fails to start.
* No devices found.
* No screens found.
* XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed with 0 events remaining
*WTF?

This seems crazy to me. I know a thing about troubleshooting - but the same issues with multiple hardware configs and after reinstalling different versions of an OS? I'm stymied.

I'll work with anyone who can help me. Please note that I'm posting from a windows laptop and may not be able to post entire log files - I'll do what I can, though...

Thanks...

---

### Post by ed-j on 2007-04-07
Hi space2k!
 
I'm a Novice so don't expect too much

Did you install the Nvidia drivers from inside Edgy: Add/Remove?

---

### Post by space2k on 2007-04-07
ed-j: nope - can't even get that far. Can't get to the GUI at all since X won't load.

---

### Post by ed-j on 2007-04-07
space2k

Restart, press[COLOR="SeaGreen"] esc[/COLOR] when the Grub is loading (it says on screen) choose something like safe or help mode (the other mode to normal). When it's finished doing it's thing, type [COLOR="SeaGreen"]sudo dpkg-reconfigure xserver-xorg [/COLOR]Follow the choices, press esc to skip anything you don't understand. Type [COLOR="SeaGreen"]exit[/COLOR] when it's all done.

Don't worry if it doesn't work or you think you've typed something wrong the first time, do a restart and........

Hope this helps!

---

### Post by space2k on 2007-04-07
Thanks - but I've done this dozens of times now and still get the same result.

---

### Post by ed-j on 2007-04-07
Oh? What system do you have?

---

### Post by space2k on 2007-04-07
I'm on a system76 Ratel desktop with integrated VIA graphics.

---

### Post by ed-j on 2007-04-07
Apologies, I should have taken note: I have no idea what a Ratel system is? Sorry!

---

### Post by space2k on 2007-04-07
bump! anyone else want to give this issue a shot?

---

