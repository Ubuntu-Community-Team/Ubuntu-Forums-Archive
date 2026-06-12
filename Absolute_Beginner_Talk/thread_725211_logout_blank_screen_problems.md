---
title: "logout blank screen problems"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by 00arthuryu on 2008-03-15
heya
i have a very strange problem
when i logout, the screen goes blank or press alt+ctrl+F1 there is sound and i can hear the ubuntu startup sound.
But the first time i login after a reboot, the startup screen works fine

Also at the starting splash screen (when ubuntu is loading) the screen says its out of range but it still displays the ubuntu loading bar. Are these related?

I've recently changed monitors, is there a quick way to fix this? or is a reinstall the best way??

Thanks!
Arthy

---

### Post by dokdoom on 2008-03-15
While a reinstall would fix the problem (or 'should') it's really not the first option you want to think of. What happened is when you changed monitors you didn't tell your OS. While it may know something different is connected it doesn't know how to handle it. This is going to require you to alter your xorg.conf file. It can be very easy, just chaning resolutions and refresh rates. If you are not familiar with your xorg.conf you may just want to run:

dpkg-reconfigure xserver-xorg

This will take you through several steps but reading them you'll be able to figure out which to choose. I would definatley try this before thiking of a reinstall.

---

