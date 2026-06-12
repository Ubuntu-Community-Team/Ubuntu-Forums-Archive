---
title: "Weird and frustrating &quot;Time&quot;..."
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by pommattski on 2006-07-04
Hi.  I'm having a strange problem with Time.
I've just installed Ubuntu Dapper - no problem...

...But then I booted into WindowsXP and noticed that the time was incorrect - significantly.  I reset the time in WinXP, then booted into Ubuntu... found that the time was wrong, reset it and booted into WinXP and guess what... the time was wrong again!
Looking at my PC's bios clock between boots revealed that Ubuntu is setting it to UTC, whist WinXP is setting it to my local time.

Though it appears that it is Windows "doing the wrong thing", I have not had this problem before with Ubuntu Breezy and Kubuntu Dapper.

This is something I need to fix... Any ideas?..... Please...

---

### Post by mlind on 2006-07-04
If you're using gnome, this must the the "UTC annoyance" thingy you're experiencing. 

Right-click time on top panel and select Preferences. If you have UTC selected,
untick it - if it's not, check the box. This should solve the timing issues you're having.

---

### Post by pommattski on 2006-07-04
Thanks, mlind.

Selecting "Use UTC" in the clock preferences has provided a 'work-around' for the clock on the panel...

... but in OpenOffice, for instance, if I select insert->field->time, it will insert an incorrect time (not local UTC).  
So I guess other application whcih uses time will also use/display/log the wrong time also.

---

### Post by pommattski on 2006-07-04
... a bit more searching and I found this: [http://www.ubuntuforums.org/showpost.php?p=698200&postcount=5](http://www.ubuntuforums.org/showpost.php?p=698200&postcount=5) which basically says edit /etc/default/rcS and change "UTC=yes" so it reads "UTC=no" has fixed it for me.

Cheers, Matt.

---

