---
title: "System time jumps forward 7 hrs when dual booting back to Win2k"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by timzak on 2007-05-11
Okay, strange problem.  I used to use Win2k exclusively.  System time was always fine.  Now that I dual boot Ubuntu and Win2k, I find that when I restart the system from Ubuntu and boot into Win2k, Win2k's system time jumps forward 7 hours.  I have verified that both OSes are set up correctly for my time zone.  Any ideas?

BTW, I am using a non-standard dual-booting method (if it makes any difference).  I have each OS installed on its own hdd and Grub does not know about Win2k (I installed each OS with the other hdd unplugged).  By default, Ubuntu loads as if it's the only OS when I start my system up.  If I want to boot into Win2k, I hit F11 at system POST and my bios boot menu pops up.  From there I select the hdd that Win2k is installed on and Win2k loads from there. 

Thanks for any help.

---

### Post by bollix47 on 2007-05-11
Right click on the time and select preferences.  If UTC has a checkmark in it's box remove it.

---

### Post by NilsE on 2007-05-11
Windows is using local time and Ubuntu is using GMT time or something like that so here is how to make them both use local time

```
In a terminal:

gksudo gedit /etc/default/rcS

Look for  this line:  UTC=yes

Change it to: UTC=no

And save it:

```

Then set the time if it is wrong in the System/Administration/Time and Date 

Then either reboot or do this: 

sudo /etc/init.d/hwclock.sh restart

---

### Post by NilsE on 2007-05-11
> **bollix47 said:**
> Right click on the time and select preferences.  If UTC has a checkmark in it's box remove it.
Sure, do it the easy way:lolflag: 

If that does not work you can do it the hard way  :)

---

### Post by timzak on 2007-05-11
Thanks, but why is this happening?  Why bother setting the time zone in Ubuntu (I live in Southern CA so I set mine for Los Angeles in Ubuntu's settings) if it's not following that?  What does UTC do that adds 7 hours to my local time?

Why does the time display correctly in Ubuntu, but only changes after I boot into Win2k?

I appreciate the help in fixing the problem, guys.  Just help me understand the whys for my curiosity. :)

---

### Post by NilsE on 2007-05-11
You can see the definition of UTC in this wiki

[http://en.wikipedia.org/wiki/Coordinated_Universal_Time](http://en.wikipedia.org/wiki/Coordinated_Universal_Time)

Basically speaking it is a world wide standard to calculate the current time wherever you are.

Since the major poulation of Ubuntu users is not in the US, Ubuntu is defaulted to this standard instead of daylight savings time and GMT calculatiions. In other words Windows does it one way and Ubuntu does it another and that confuses Windows when it reads the BIOS clock.

I hope that helps.

---

### Post by timzak on 2007-05-11
I just checked in Ubuntu and UTC was not checked.  What else could it be?

---

### Post by icechen1 on 2007-05-11
> **timzak said:**
> I just checked in Ubuntu and UTC was not checked.  What else could it be?

You can set it to synchronize with internet servers ,it should fix it.
Go in System->Administration->Time and Date

---

### Post by NilsE on 2007-05-11
> **timzak said:**
> I just checked in Ubuntu and UTC was not checked.  What else could it be?
Just for the heck of it do it the way I posted above.  Mine was not checked either and it solved the problem.

---

### Post by timzak on 2007-05-12
> **NilsE said:**
> Just for the heck of it do it the way I posted above.  Mine was not checked either and it solved the problem.

Thanks, that fixed the problem.

Best regards!

---

### Post by mcduck on 2007-05-12
> **timzak said:**
> Thanks, but why is this happening?  Why bother setting the time zone in Ubuntu (I live in Southern CA so I set mine for Los Angeles in Ubuntu's settings) if it's not following that?  What does UTC do that adds 7 hours to my local time?

Why does the time display correctly in Ubuntu, but only changes after I boot into Win2k?

I appreciate the help in fixing the problem, guys.  Just help me understand the whys for my curiosity. :)

By default, all Unix (and Linux) systems run their clock in UTC, and then if you set another time zone the clock you see on the desktop will calculate time using that information (while the computer's clock still uses UTC).

So, your system time is UTC, and local time UTC+7. But Windows doesn't do it this way, it thinks that system time = local time. And that is what causes the time to change when you move between Windows and Linux.

---

### Post by Moosetek13 on 2007-05-30
> **timzak said:**
> Okay, strange problem.  I used to use Win2k exclusively.  System time was always fine.  Now that I dual boot Ubuntu and Win2k, I find that when I restart the system from Ubuntu and boot into Win2k, Win2k's system time jumps forward 7 hours.  I have verified that both OSes are set up correctly for my time zone.  Any ideas?

BTW, I am using a non-standard dual-booting method (if it makes any difference).  I have each OS installed on its own hdd and Grub does not know about Win2k (I installed each OS with the other hdd unplugged).  By default, Ubuntu loads as if it's the only OS when I start my system up.  If I want to boot into Win2k, I hit F11 at system POST and my bios boot menu pops up.  From there I select the hdd that Win2k is installed on and Win2k loads from there. 

Thanks for any help.
It's funny, but I was having the exact same problem and we have the same setup.
I have XP on the other drive, though.
I agree that it is a much nicer solution to dual-booting than letting Grub get its grubby fingers into my Windows MBR.

NilsE, thanks for the fix. When I went into the clock prefs UTC was unchecked, yet the time always changed.

Timzak, it was not a consequence of rebooting into Windows that changed the time, it was simply exiting Linux.
I started checking the time set in the BIOS when I changed boot drives and noticed that the time had changed after I exited Linux.

---

### Post by timzak on 2007-05-30
Thanks, Moosetek.  Another funny coincidence:  I just reinstalled Feisty (I was a noob on the first install and knew I mucked things up under the hood) and was looking for this thread to fix my time on the new install and you'd replied, so it was right in front of my face.  Thanks.  :p

---

