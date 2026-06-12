---
title: "Kaffeine &amp; Noatun wont open"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2007-01-04
For some strange reason, Kaffeine & Noatun wont open any more.  They used to work but now they just say they are loading and then nothing??  I tried reinstalling them but still no luck. :-k 

Can anyone suggest a fix?

Russty.

---

### Post by sunexplodes on 2007-01-04
try running them from a terminal, see if it displays any error messages.

---

### Post by Russty of Oz on 2007-01-04
NO, nothing at all happens, not even an error.

---

### Post by Russty of Oz on 2007-01-05
Can anyone suggest something?  :(

---

### Post by ac7ss on 2007-01-07
I am having the same trouble with Kaffeine:

> ac7ss@ac7ss-laptop:~$ kaffeine --verbose
ac7ss@ac7ss-laptop:~$ kaffeine -v
Qt: 3.3.6
KDE: 3.5.5
Kaffeine Player: 0.8.2
ac7ss@ac7ss-laptop:~$      

Running KDE, Ubuntu Edgy.

Totem works fine.

---

### Post by Russty of Oz on 2007-01-07
Yesterday I finally got them both to work!

I used synaptic and selected "**mark for complete removal**" then I rebooted, then installed them again and rebooted again and BINGO! they now work fine.

So it seems that when they go wrong you just need to do a complete removal which it says removes the configuration files as well, then it seems to need the rebooting to fix it all up properly.  It did the same first without rebooting and it still didn't work, so rebooting seems to be necessary.

Russty

---

### Post by dyntryx on 2007-01-10
I had this problem, and immediately assumed it was probably my configuration files or something (same as you guys I guess).  However, it turns out I didn't have to remove it and reinstall.  I simply did this command:
```
killall kaffeine
```
After that it ran just fine.  Some sort of bug must be causing it to remain in memory after it has been closed--or more likely, after it has _crashed_.  Nonetheless, this saved me a reboot; hope it'll save someone else one as well.

If that still fails, try running this to reinstall:
```
sudo dpkg --purge kaffeine kaffeine-xine
sudo apt-get install kaffeine
```
That will, however, clear configuration files.  If that still fails, try [Russty of Oz's solution]("http://ubuntuforums.org/showpost.php?p=1982407&postcount=6"), which seems relatively failsafe to me.

Cheers. :)

---

