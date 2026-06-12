---
title: "Newbie woes (graphics and bootup problem)"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by keno.mentor on 2007-11-18
I've recently installed kubuntu and after much difficulty, got the wireless networking and sound to work (yay!)  But my graphics problem continues.  I have a via/S3 unichrome pro IGP onboard graphics card and my original problem was that the screen resolution was very poor and I could not set it to more than 800x600.  I then edited the xorg.conf using some command I can't remember to select the higher resolutions.  And now...I can't boot into kubuntu.  It shows the splash screen (with the progress bar) and then it gets stuck on "running local boot scripts".

I am utterly despondent.  I have years of PC experience but it seems you need a PhD in computer science to get a linux based OS setup.

Any suggestions?

Many thanks,
keno

---

### Post by jken146 on 2007-11-18
Hi there,

Please don't give up!! You will not regret it if you get everything working the way it should.  As for your graphics problems, if you backed up you xorg.conf file now would be a good time to replace it with the old one (you can do this with the live CD or in recovery mode with the console).  Failing that, boot into recovery mode and do
```
dpkg-reconfigure xserver-xorg
```

Good luck!

---

### Post by jken146 on 2007-11-18
And if you want to edit xorg.conf to set higher resolutions, follow this guide:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

