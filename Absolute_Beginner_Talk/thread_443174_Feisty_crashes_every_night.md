---
title: "Feisty crashes every night"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by linuxuser28 on 2007-05-14
With Feisty when I go to use my computer in the morning, everything is locked up. The only thing I can do at that point is turn off the computer then turn it back on. Is this a common problem and is there a fix?
  I am using a IBM P4 2.5 GHz computer with 512 MB of RAM.

---

### Post by starcraft.man on 2007-05-14
> **linuxuser28 said:**
> With Feisty when I go to use my computer in the morning, everything is locked up. The only thing I can do at that point is turn off the computer then turn it back on. Is this a common problem and is there a fix?
  I am using a IBM P4 2.5 GHz computer with 512 MB of RAM.

You using Beryl/compiz? If your not, did you install your cards drivers at all? If so, do you leave anything in particular on all night? Ubuntu doesn't crash less something goes wrong, its completely stable far as I know when not using the other window managers... Did you have any problems installing originally and had to use workarounds to get it in?

---

### Post by srt4play on 2007-05-14
Continuing with starcraft.man's train of thought, my first suspicion would be combination of a 3d screensaver running and no 3d drivers installed.

---

### Post by silent1643 on 2007-05-14
mine used to freeze and log out every time the screen saver loaded, i made my screen saver just a black screen and it solved the problem.

---

### Post by linuxuser28 on 2007-05-14
I have been using the MatrixView screensaver, so I have switch it to the blank screen. I will see if that helps.

---

### Post by lazyart on 2007-05-14
This sound familiar to me as well-- 3d screensaver locked up my dapper (onboard video) plenty of times.  Gone to Edgy and now Feisty and even have dedicated graphic card but haven't yet turned on the screen saver.

My theory-- Screensavers are like bumper stickers.  They look real cool when you put them on, but how much time do YOU really spend looking at it?

---

### Post by linuxuser28 on 2007-05-15
I turned off the screensaver yesterday, unfortunately when I went to use it this morning it was locked up again.:(

---

### Post by silent1643 on 2007-05-15
very odd, check your power management settings.. 
are you running any programs in the background that could crash?

---

### Post by RyanVanDiemen on 2007-05-15
Something similar happened to me last time I hibernated Feisty. After waking up (the computer), everything looked working fine except my keyboard. I had to reboot and then everything worked. I didn`t try it since, but when I think of it, I didn`t have  my graphics installed correctly at the time.

---

### Post by stewvmusic on 2007-05-21
In my case screen savers, restricted drivers and Compiz/Beryl had nothing to do with this.

My wife's machine (see spec's in signature) would not respond to anything from the keyboard or mouse in the morning.  Had all power management turned off.  Power light would blink.  The best response I got from the machine was by pressing the power button.  It would attempt to restart, but the screen would shut back off.  Had to completely unplug the machine at the power supply to restart.

I simply went into BIOS and changed suspend mode from S3 to S1.  And this took care off it of the lockup problem.

Mind you, I don't use suspend so this did not bother me (I shut my monitor off every night), but for those that use suspend you may not be satisfied with this resolution.  I think there is a bug in Feisty with regards to suspend.

---

