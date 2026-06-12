---
title: "Display problem upon start-up"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by dualityim on 2007-12-01
Hello, I just installed Ubuntu 7.10 desktop for the first time and registered on these forums for the first time, apologies in advance if the problem I'm about to describe is a known and documented issue.

It seems upon starting up Ubuntu, both from the LiveCD and from my local installation, immediately after the loading screen with the progress bar finishes, the monitor would go into standby mode. Sometimes, it would remain in standby mode for only a second, then wake up from standby and proceed to the log-in screen (or, in the case of the LiveCD, proceed to the desktop). However, other times, the display would remain in standby mode. The computer appears unresponsive at that point, however I'm not certain if it has crashed or if it is simply not sending signal to the display.

I can't discover any patterns of this behavior, and it seems it is random whether the display wakes up from standby or not during any booting session. I suspect that the graphics driver may be the problem, since when I try starting up with the safe graphics option using the LiveCD, so far this problem has not happened. But I can't be certain that it won't happen since the problem appears at random.

The graphics card I'm using is an ATI All-in-wonder 8500DV. Could the default ati driver used in Ubuntu be having problems with this particular card? If so, is there anything I can do about it? The new proprietary drivers from ATI does not work with this older card, and the older version of the proprietary driver that ATI indicates would work with it, version 8.28.8, doesn't seem to work with gutsy gibbon, or at least I can't find any documentation for getting it to work with gutsy.

Thanks in advance for any help or pointers that anyone could provide on this matter.

---

### Post by chuckyp on 2007-12-01
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

See the above for documentation on getting your driver working.  There is also a hardware list on help.ubuntu.com with each card listed and which drivers to use.  Its under the user documentation section.

---

### Post by dualityim on 2007-12-01
> **chuckyp said:**
> [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

See the above for documentation on getting your driver working.  There is also a hardware list on help.ubuntu.com with each card listed and which drivers to use.  Its under the user documentation section.

I had previously found this page: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Which has detailed instructions on getting version 8.42.3 of the ATI proprietary drivers to work with gutsy, as well as instructions on getting other ATI drivers to work with feisty. But I can't find anything about getting the older version of the ATI drivers that I need (8.28.8) to work with gutsy. (Since 8.42.3 doesn't support any cards earlier than 9700).

Do you have any ideas on how to apply this earlier driver to gutsy? Should I follow the feisty instructions, or follow the instructions for 8.42.3 on gutsy?

---

### Post by dualityim on 2007-12-01
Upon further reading I found that it is pretty much hopeless to try to get the older version of the ATI proprietary drivers to work with gutsy. I'm using the open source ATI drivers right now and it seems to support the AIW 8500DV just fine. What's strange is that for the times that the display do wake up from standby after the loading screen, everything works well. But I have to restart several times in order to get it to work. Could this possibly be a known issue with the open source drives with the 8500DV card? Or some other kind of problem? I tried switching NumLock and Capslock after the screen goes into standby, and neither of these are responsive. So it seems the system did indeed lock up after the loading screen.

---

