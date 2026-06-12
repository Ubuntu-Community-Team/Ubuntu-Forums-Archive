---
title: "Problems adding z600 driver for lexmark printer"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by suki on 2007-01-03
Having issues with Lexmark X1150 Printrio. I scanned with it no problem but printing with it is an issue. It will stop the job and not even attempt to print. 

I installed alien and followed the how to guide here: [http://www.ubuntuforums.org/showthread.php?t=49714&highlight=X1150](http://www.ubuntuforums.org/showthread.php?t=49714&highlight=X1150).

Then going to System -> Administration -> Printing, I tried to add a new printer it would not automatically find the driver and when adding a driver no .ppd or .ppd.gz file was found. 

Solved by the following method found on the last page of the previously stated how to thread:
> **BLTicklemonster said:**
> Click install driver, then use the lexmark ppd in /usr/share/cups/model
and let it set up. Then try to print. If it won't, open your printer dialogue, delete the printer you just set up, then go through set up again, and you will probably see Z600 listed this time. That's what I had to do. 

---

### Post by StormGuy on 2007-01-04
I had to mess with my settings a lot to get my printer to appear too.  It isn't automatic, I don't believe.

Hopefully somebody with more intimate knowledge can explain it a lot better than me.

---

### Post by StormGuy on 2007-01-04
bump

---

