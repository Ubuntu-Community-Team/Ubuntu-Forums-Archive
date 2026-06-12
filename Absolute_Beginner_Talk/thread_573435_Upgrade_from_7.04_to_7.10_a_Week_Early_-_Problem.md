---
title: "Upgrade from 7.04 to 7.10 a Week Early - Problem"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by MattyGabe on 2007-10-11
Hello all.  I'm trying to upgrade my distribution to 7.10 to check it out.  A friend of mine let me know that they were about to release Gutsy Gibbon and all the new features it had, so I wanted to check it out (the NTFS read-write is what I'm most interested in).  I ran the upgrade-manager -d command, it came up telling me there was a 7.10 upgrade available, so I checked it.  It installed the two items needed for the installer, then proceeded to start to upgrade the distribution.  Not far into it all three times I tried, I got this error message:

Getting upgrade prerequisites failed



The system was unable to get the prerequisites for the upgrade. The upgrade will abort now and restore the original system state.



Please report this as a bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

Now, I'm thinking perhaps my being behind a proxy may have something to do with it.  I have the proxy settings set for the system, and for Firefox as well (obviously).  Is there something I'm missing?  Please let me know what I can do.  Thanks all!

---

### Post by Paqman on 2007-10-11
Until Gutsy is stable I wouldn't throw out your Feisty install. If you've got a spare 10GB i'd make a new partition for Gutsy, and install it there using the LiveCD. If you've got your /home on a seperate partition you'll even be able to keep the same setup whether you boot into Feisty or Gutsy. Just make sure the only partition you format during installation is the new Gutsy root partition.

---

### Post by MattyGabe on 2007-10-11
I actually solved the problem, I apologize for cluttering the forum up.  The error I had was fixable with the FAQ on the Ubuntu Upgrade page.  I never saw the same error message since I ran the upgrade program from the Run box, not from terminal.

Thanks for your help!

---

