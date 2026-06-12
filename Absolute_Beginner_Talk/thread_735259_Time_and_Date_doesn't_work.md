---
title: "Time and Date doesn't work"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by hp_pavilion_39 on 2008-03-25
I'm running on Ubuntu 7.10 *The Gusy Ribbon*  and the upper right hand clock..next to the power icon won't work.  It just stopped last night at 11:28 and it still reads "11:28".  Ive tried re-booting but nothing seems to make the clock restart.  Any suggestions on what to do?
--
Thanks

---

### Post by Oldsoldier2003 on 2008-03-25
> **hp_pavilion_39 said:**
> I'm running on Ubuntu 7.10 *The Gusy Ribbon*  and the upper right hand clock..next to the power icon won't work.  It just stopped last night at 11:28 and it still reads "11:28".  Ive tried re-booting but nothing seems to make the clock restart.  Any suggestions on what to do?
--
Thanks
If you can't adjust the date/time in the clock applets  preferences menu you could try:

```

sudo ntpdate ntp-1.mcs.anl.gov
sudo hwclock --systohc
```

or just remove and reinstall the clock applet from your panel. if all this fails you might want to reinstall it. I'm running 8.04 Beta so I can't remember the package name you will need to reinstall if it gets that far.

---

### Post by hp_pavilion_39 on 2008-03-25
ok, thanks.  i used the preferences menu, and it is working now.
--
Thanks

---

