---
title: "No sound after installs"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by Mileeta on 2007-01-25
I'm pretty new to Ubuntu, going on a week now without Windows (yay me!)  I have enough things up and working that I don't think I will go back, but there's still a few kinks to work out.

I've installed a few games under wine (Diablo II, WoW) and other than during the initial install, I don't get any sound.  Specifically, I get the music that plays when you first install the game (whether that is from the CD like with Diablo or the login screen with WoW) but once the game has been shut down once, the sound won't work again.  Sound works just great with Rhythmbox, but doesn't work at all with flash stuff like YouTube.  I'm not exactly sure what I need to fix, but I'm thisclose to getting everything happy!

AMD Athlon 64 3600+
Sound Blaster Live!
ATI Radeon 9600 XT
Ubuntu 6.06 Dapper Drake
Wine 0.9.29

-M

---

### Post by Shatrat on 2007-01-25
For the Youtube thing you might need to install Flash9, its in the backports repositories I believe.
For wine you might need to mess with the audio settings in 'winecfg', namely make sure it's using ALSA. (I think SB Live uses alsa anyway...)

---

