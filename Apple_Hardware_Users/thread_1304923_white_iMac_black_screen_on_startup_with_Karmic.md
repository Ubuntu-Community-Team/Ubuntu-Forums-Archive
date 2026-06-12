---
title: "white iMac black screen on startup with Karmic"
date: 2009-10-29
forum: Apple Hardware Users
---

### Post by Geeb on 2009-10-29
Sorry if this has been done already, if it has I couldn't find it.  I am using an intel iMac with 9.1 but when I boot into it I get a black screen.  This happened on the live cd too until I turned ACPI off in the boot options for the live cd so I'm assuming this would fix the problem, but I get a black screen before I can even see a login screen.  I'm not able to get to the terminal with ctrl alt F1 and with the new grub I'm not sure how to get to single user mode.  I'm some what of a newbie so any help would be appreciated.  I'm probably just doing something dumb so if you could point that out to me that would be great :D

---

### Post by Geeb on 2009-10-30
OK well I think I got it just FYI if anyone else has the same problem.  I had to append i915.modeset=0 in grub to get it to start.  I know it says not to, but hey if it fixes the problem...

---

### Post by Nadav34 on 2009-11-14
> **Geeb said:**
> OK well I think I got it just FYI if anyone else has the same problem.  I had to append i915.modeset=0 in grub to get it to start.  I know it says not to, but hey if it fixes the problem...

Hey, how did you modify the modeset in grub? When I always boot from the liveCD, I have to boot it in safe mode, instead of normal because normal gives me a black screen and no keyboard activity.

---

### Post by Geeb on 2009-12-11
As it comes up to the Ubuntu screen on the live cd hit F6 for other options then select acpi=off this should allow you to get into the live cd.  Also appending the i915.modeset=0 only works until the next kernal update.  When the new kernal is updated grub is reconfigured and you have to put the i915.modeset=0 back in.  To do this the first time, get to grub and hit e.  then append i915.modeset=0 to the end of the line right after where it says "quiet splash".  This will get you into the GUI.  You then have to get into /boot/grub/grub.cfg and edit it there.  In order to edit that file you have to make it writable.  YES this is a ton of work each time you have a kernal update, but it's the only way I've found so far to do get it to work.  If anyone knows how to edit the /etc/grub.d/40_custom file to get it to do this each time the kernal updates it would be very appreciated.  In the mean time I hope this works as a work around.  I'm still very much a linux newbie so I apologize if I'm saying things wrong, but this worked for me at least until I can figure out something better.

---

