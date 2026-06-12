---
title: "View boot log in Gutsy?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by plain_jim on 2008-02-19
I'm having a problem with my Palm device. I tried a couple of the suggestions on this forum, and they have not worked.  I saw a reference to one of them while my computer was checking the hard drive (like it does every 20th bootup), but I was too ditsy to write it down at the time... but then I thought, "Aha!  I will check out the boot log!"

There wasn't anything IN the boot log.

I tried [(the solution this text links to)](http://ubuntuforums.org/showthread.php?t=49925), but, even though my /etc/default/bootlogd now shows "Yes", my /var/log/boot still reads "(Nothing has been logged yet.)", after two reboots.

Is there any way to get a useful boot log? I'm running
-Gutsy
-AMD64, 2.1gig
-2gig ram

---

### Post by Nxion on 2008-02-19
Unplug the Palm and reboot. 

Then when ubuntu is up and you are loged in, plug in the Palm and wait a min.

Then open your terminal and type 

```
dmesg
```Look for errors and post the output here.

---

### Post by dcstar on 2008-02-19
> **plain_jim said:**
> I'm having a problem with my Palm device. I tried a couple of the suggestions on this forum, and they have not worked.  I saw a reference to one of them while my computer was checking the hard drive (like it does every 20th bootup), but I was too ditsy to write it down at the time... but then I thought, "Aha!  I will check out the boot log!"

There wasn't anything IN the boot log.

I tried [(the solution this text links to)](http://ubuntuforums.org/showthread.php?t=49925), but, even though my /etc/default/bootlogd now shows "Yes", my /var/log/boot still reads "(Nothing has been logged yet.)", after two reboots.

Is there any way to get a useful boot log? I'm running
-Gutsy
-AMD64, 2.1gig
-2gig ram

The only workaround seem to be here (at the end):

[https://bugs.launchpad.net/upstart/+bug/98955](https://bugs.launchpad.net/upstart/+bug/98955)

---

