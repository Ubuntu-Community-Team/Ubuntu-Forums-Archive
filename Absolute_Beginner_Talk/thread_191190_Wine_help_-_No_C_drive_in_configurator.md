---
title: "Wine help - No C drive in configurator"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by xx75 on 2006-06-07
To he/she who seems interested......

I have installed wine and just run winecfg. I erased the "C drive" under the drive tab (I highlighted the wrong drive, long story - oops) and no matter what I do it just won't save it back on again. I can add it to the list and apply but it won't save. So whenever I get winecfg running I always get the message "You do not have a C drive, this is not a good thing"

I have uninstalled it three times now and when I reinstall it I still get the same result.


Any clues?

Thanks
xx75

---

### Post by Sukarn on 2006-06-07
If you do not have any windows programs installed that you do not wish to lose, then can you try to perform **sudo dpkg --purge wine** and then remove ~/.wine (**rm ~/.wine**).
After that try installing wine again and running winecfg.

There was another way to it that I knew, but I forgot which file needed editing for it.

---

### Post by xx75 on 2006-06-07
Thanks Sukarn

Worked like a charm!

cheers
xx75

---

### Post by nintendorulz55 on 2008-03-02
THANK YOU! i had the same problem and tried until my fingers hurt from typing, and then i find this thread.

---

### Post by Oldsoldier2003 on 2008-03-02
> **Sukarn said:**
> If you do not have any windows programs installed that you do not wish to lose, then can you try to perform **sudo dpkg --purge wine** and then remove ~/.wine (**rm ~/.wine**).
After that try installing wine again and running winecfg.

There was another way to it that I knew, but I forgot which file needed editing for it.

Sometimes you have to reboot your system (**after purging wine and deleting `/.wine but before reinstalling wine**) in order for that to work.  After installing wine running winecfg should work correctly

---

