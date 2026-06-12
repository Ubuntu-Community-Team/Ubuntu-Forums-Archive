---
title: "Log on sound and preview sound not working all of a sudden."
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2007-05-08
The last thing I installed on my Dapper build was Google's Picasa. Though I can't recall if when the last time I logged out or shut down, my shut down file sound went off. 

Now however, I've noticed that when I hover over any Mp3 file as usual, I don't get the preview as per usual, and I'm also not seeing the little icon pop up of the musical notes which always accompany the preview either.  I just rebooted and noticed that the shut down sound didn't go off either. Sound in general is working, as I'm able to play music files, and when the Ubuntu log on screen popped up, I did get the percussion drum roll thing.  This is an odd succession of non working events, and I can't pinpoint where the problem lies. 

Erm, stupid question: How can I uninstall Picasa to see if it is the culprit ?

---

### Post by Sweet Spot on 2007-05-09
Anyone ? Bueller.....  Bueller......   Bueller...

---

### Post by Sweet Spot on 2007-05-10
Nothing ?  I'd hate to have to resort to a reinstall at this particular moment, since I'm so busy with school and such....  Besides, I always see a reinstall as the last option when all others are exhausted. I haven't even seen any reasons for why this happened. 

I'd really appreciate any insight that anyone may be able to offer. 

Doug

Edit: To note, I uninstalled Picasa, and still nothing.

---

### Post by Sweet Spot on 2007-05-10
Well, searched a bit more, and found something that fully worked:

```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
sudo reboot
```

So for anyone whom may run into this problem, and I totally suspect it was not due to the Picasa install, but because I had installed Enlightenment via Synaptic, along w/several other E17 packages, and then had totally uninstalled them, probably without looking at what was being uninstalled.....

So, all is back to normal.

---

