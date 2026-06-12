---
title: "[SOLVED] Did Updates, Restarted &amp;amp; Can't Connect to Wireless"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by luger on 2007-09-15
I just did a fresh install and installed my wireless drivers using the latest ndiswrapper and got my device (TrendNet TEW-423PI) to start working. I got on my wireless, entered the WPA (which it added to the keyring) and then I proceeded to go into Synaptics and marked all upgrades, installed them and then was told to restart. 

After the restart, the keyring asked for my password and proceeded to attempt to connect to my wireless network but now it didn't succeed. So I clicked on my network again and it won't connect. I rebooted and still nothing.

So, I got my connection working, performed a few updates, restarted and now I can't get it to work. Any suggestions?

There is nothing wrong with the actual connected itself, as I can see the strength of it (and am on it now through Windows).

---

### Post by bone2006 on 2007-09-17
Where did you get the latest ndiswrapper?  Was it from their offical site or from the repository?  I did an update once in ubuntu that the new kernel broke my wifi and everything I tried wouldn't get me up and running.  I actually had to go to ndiswrapper and get the latest version, might have been a beta and it was the only thing that worked for me, wasted a few hours figuring it out though.

---

### Post by Mark_in_Hollywood on 2007-09-17
Look under System/Administration/Restriced Drivers Manager

you may need to activate a "restricted" driver

as a reminder, if this works, please close the thread with success in thread tools

---

### Post by luger on 2007-09-20
I located and removed all files associated with ndiswrapper then reinstalled from scratch and was able to get things running smoothly.

Thanks guys.  Problem solved.

---

