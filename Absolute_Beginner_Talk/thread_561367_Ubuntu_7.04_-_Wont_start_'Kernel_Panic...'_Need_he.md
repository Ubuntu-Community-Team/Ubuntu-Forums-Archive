---
title: "Ubuntu 7.04 - Wont start: 'Kernel Panic...' Need help!!!!"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by jannen on 2007-09-27
First please know im a beginner!!! :)

Today Ubuntu 7.04 didnt want to start, I get the message: **Kernel Panic - not syncing VFS - Unable to mount fs on unkown block..**. I have checked the forum for this and googled it, but still dont know what to do. I get stuck here, I can only get out with the laptop's power button.

Im running Ubuntu now on the 'Generic 15 option' (thanks to this I can access Internet and write this!) But I cant make any updates on this, if I try that I get this error message:  [B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

Should I reinstall Ubuntu, if, how do you do that? (I have Ubuntu CD, but I also have Windows 2000 installed which dont want to loose...)

Any other way to solve this problem? And what might have caused it?

**Big hug to anyone willing to help!!!!**

---

### Post by ddrichardson on 2007-09-27
Have you, from the terminal, run ```
sudo dpkg --configure -a
```

---

### Post by jspangler on 2007-09-27
When my kernel starts to panic, I speak slowly and softly to it, and stroke it's hair. :lolflag:

OK, I'm so sorry. I promise never to do that again.

---

### Post by Natsuko640 on 2007-09-27
I'm having the same problem with my laptop. I put in that line and things ran fine, but then the computer froze and now it won't start. Any idea how to fix it?

---

### Post by jannen on 2007-09-29
Back online again... thought I lost everything. Luckily after few trials DdRichardsons (above) suggestion worked!

Very happy & big thanks for the help!!! Great!

:guitar:

---

