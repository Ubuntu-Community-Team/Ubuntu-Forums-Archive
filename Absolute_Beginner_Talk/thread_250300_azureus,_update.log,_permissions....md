---
title: "azureus, update.log, permissions..."
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by kpm on 2006-09-03
I just used Automatix to install Azureus, along with a bunch of other useful stuff... When I ran Azureus, I encountered a problem.  On start up, Azureus runs an update; I encountered an error that said /opt/azureus is not writeable, so it could not complete the update.  On restart, Azureus informed me which library was not updated: SWT Library for gtk 'SWT is the graphical library used by Azureus'.  Then Azureus pops up an error that says "Installation of at least one component failed - see 'update.log' for details."  (I wish it told me where the update.log was located... this is one of my biggest hurdels in my switching to Linux... I have no idea where to look for such files).  Can anyone give some advice on how to update this library, or find the update.log??
Thanks

---

### Post by arnieboy on 2006-09-03
> **kpm said:**
> I just used Automatix to install Azureus, along with a bunch of other useful stuff... When I ran Azureus, I encountered a problem.  On start up, Azureus runs an update; I encountered an error that said /opt/azureus is not writeable, so it could not complete the update.  On restart, Azureus informed me which library was not updated: SWT Library for gtk 'SWT is the graphical library used by Azureus'.  Then Azureus pops up an error that says "Installation of at least one component failed - see 'update.log' for details."  (I wish it told me where the update.log was located... this is one of my biggest hurdels in my switching to Linux... I have no idea where to look for such files).  Can anyone give some advice on how to update this library, or find the update.log??
Thanks

to update azureus, run it as root
```
sudo azureus

```after successful completion of upgrade, close it and run it as normal user.

---

### Post by kpm on 2006-09-03
thanks! got it to work (but first had to navigate to /opt/azureus/azureus to get it to run from cmd line).

---

### Post by TwoAyEm on 2007-12-29
I'm geting the same problem, 
```
sudo ./azureus
```
 still complains that an update has not been applied...

Have tried 
```
sudo chown -R user azureus
```
from /opt/ but still nothing... Can anyone suggest anything else to try. I really want to get to grips with this beast and avoid going back to MS if at all humanly possible.

Any help appreciated.

---

### Post by rogers45 on 2008-01-03
I have the same problem, and i have to add "sudo azureus" but no nothing changes!? Only thing happened is a Azureus started as a browser Vuze window??

//

---

### Post by Perfect Storm on 2008-01-03
Try read this: [http://ubuntuforums.org/showthread.php?t=144546](http://ubuntuforums.org/showthread.php?t=144546)
Though it's a guide how to install Azureus the latest version (non repo), it also explain how you can get access to update Azureus and then close it again (safty reasons).

---

### Post by rogers45 on 2008-01-03
> **Artificial Intelligence said:**
> Try read this: [http://ubuntuforums.org/showthread.php?t=144546](http://ubuntuforums.org/showthread.php?t=144546)
Though it's a guide how to install Azureus the latest version (non repo), it also explain how you can get access to update Azureus and then close it again (safty reasons).

ok thank you,, i am trying this one,,

//

---

