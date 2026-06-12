---
title: "Fresh 18.10 on Macbook Pro 2.80 Ghz Mid-2009 Graphics issues"
date: 2018-12-13
forum: Apple Hardware Users
---

### Post by airplaneit on 2018-12-13
I had a working install of 18.10 on my Macbook Pro Mid-2009 (dual graphics). It had been continuously updated since around Ubuntu 12.10.

I recently decided to wipe the drive, get rid of my MacOS and Windows partitions, and just go with Ubuntu.

First off, I think there's a bug with the live and installer. When I boot directly into the installer, I get a desktop image but no interface. Likely the same problem as with the live version. In the live version, Ubuntu boots as if my laptop display is the *second* monitor. That means it boots into the desktop and all I see is the wallpaper. I have to right-click and change the desktop settings to mirror the first monitor in order to get into the installer from the Live interface.

My issue I'm writing about here may be related to that. After my fresh install, which I've tried twice, I don't get a full boot into a login screen. It hangs on a black screen. If I function-control-alt-F2 into TTY2, I can log in, but I get an error involving "vga_switcheroo 0" and "vga_switcheroo stopping nouveau". Then I can actually switch back to TTY1 and login normally. This is using Nouveau, which the 18.10 installer decides to use by default, despite giving it permission to use proprietary drivers.

So then I switched to Nvidia-340.107 which was an option under Software & Updates->Additional Drivers tab. I applied changes and rebooted.

Now I get a somewhat normal boot but it takes a long time and the screen is flashing like it's trying to figure out graphics settings. And I can't function-control-alt-F# into another terminal, it just gives me a blank screen, but I can get back into the GUI with function-control-alt-F1.

Any ideas?

---

### Post by howefield on 2018-12-13
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by airplaneit on 2019-05-06
I would like to bump this post, if I may. I just did a clean install of 19.04 and I'm having the same issue. I have disc encryption on, so I can see the Ubuntu Splash, I enter my passphrase to unlock the drive, and then it continues to boot with the Splash. Then before seeing a login screen, the screen goes blank. If I switch to terminal 2 and back to 1, I get the Nvidia Splash and after a few seconds the login screen appears, and then things are normal after that.

I would really love it if someone can help with the troubleshooting here.

---

