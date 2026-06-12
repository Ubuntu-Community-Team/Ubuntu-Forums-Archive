---
title: "[SOLVED] My Desktop won't display. Warning, im abit of a n00b with linux."
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by jospinlase on 2008-04-13
i fancy myself as semi-computer savvy, but im utterly lost when it comes to linux.
i know nearly everything there is to know about M$ and Apple systems, but decided to try my hand in the free software world... and hit a bit of a speed bump

My problem is this, i Just installed Gutsy on a custom comp. When i built the computer i bought a cheap graphics card to reserve my funds for other things... (VGA SAPPHIRE ATI 100173L X1550 512MB) 

I searched everywhere for drivers for my card, so i could set the resolution properly. I came across the Restricted Driver thing in the Admin menu. It had what i thought to be the driver ready to be installed. I enabled it, restarted and let it go through the boot process like normal. It cleared all of the boot menus and splash screens perfectly. However when I got to the desktop, it was absolutely blank. 

Distraught with my self destruction, i left it alone for the night. I thought of how i could best fix my problem, then i realized i was using a DVI connector and my card has a VGA and DVI port. I decided to try an old VGA LCD out on it to see if i could view my desktop. I was in luck, it let me see things again, albeit rather distorted due to the resolution, but i could tell what i was doing. First order of business that made sense to me, was to disable the driver and revert back to the VESA graphics that were on by default before. Man, was i wrong about that.

I booted it up just like before, this time with both monitors attached for good measure.
both displays were the same Artifact ridden decay of my desktop.

My internet is via a satellite which means it will take forever to download the updates again, so i'd like to find a solution that doesn't involve re-installing (as was the advice in this thread [http://ubuntuforums.org/showthread.php?t=664051](http://ubuntuforums.org/showthread.php?t=664051) ). 

If there isn't a solution readily available with this graphics card, i would not be at all opposed to purchasing a new card that would be better supported. In which case i wouldn't mind some recommendations. (NVIDIA would be a god send right about now ;) )

Thanks in advance to any advice you can give.

---

### Post by warbread on 2008-04-13
First and foremost, I suggest never buying ATI anything ever again for any computer that you'll use Linux on.  No, it's not impossible to get working, and in most cases it's no different from an nVidia card.  Still, out of the 5 or so computers I have runniing Linux, I have the most trouble with the ones that use ATI chips.  Getting a cheap nVidia card should help a lot.

However, a proper fix now would be to boot into recovery mode (press escape at the Grub bootloader before the 3 second countdown finishes) and type in :

```
sudo dpkg-reconfigure xserver-xorg
```

That will reconfigure your xorg.conf file, the file used by the X windows system for just about everything.

---

### Post by jospinlase on 2008-04-14
@warbread

Dude, you have no ******* clue how thankful i am. I am forever in your debt. 

I was short on cash at the time of building this computer, and as such cheaped out on the vid card. 

I had trouble with my card on my XP install aswell, so needless to say lesson learned with cheap ATI cards. 

nVIDIA all the way from now on for me, and ill be careful to look for Linux ready drivers this time around too.

Thanks again.

---

