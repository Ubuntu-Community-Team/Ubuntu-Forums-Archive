---
title: "How to get time right in all OSes in multiboot system"
date: 2007-10-25
forum: Apple Intel Users
---

### Post by PaulFXH on 2007-10-25
I have three Linux OSes (Gutsy, openSUSE 10.3 and Sidux 2007-3) as well as OS X (tiger), on my MacBook (C2D) and I have a big problem trying to get the time right on all four OSes. Almost inevitably, whenever I boot a different OS, the time shown is either an hour ahead or an hour behind.
So, I adjust the time after the boot. Nevertheless, when I boot into this OS again, the time is once again an hour out.
Can anybody point me to a link where a remedy for this problem is explained.
(I realize that has little if anything to do with the MacBook)
Thanks
Paul

---

### Post by ldesilva on 2007-10-25
I configured NTP for all my OS on 1 single machine. Let the time servers sync my time as long as I have the correct timezone config.

---

### Post by PaulFXH on 2007-10-25
OK, that sounds good but would welcome a little more detail on exactly what you did.
I set all my OSes manually (with, obviously, the correct time zone). This was simply because I didn't have the name of an appropriate server for my timezone (or any timezone).
Any more clues what more I can do here?
Thanks
Paul

---

### Post by cyberdork33 on 2007-10-25
> **PaulFXH said:**
> OK, that sounds good but would welcome a little more detail on exactly what you did.
I set all my OSes manually (with, obviously, the correct time zone). This was simply because I didn't have the name of an appropriate server for my timezone (or any timezone).
Any more clues what more I can do here?
Thanks
Paul

The timeserver should be irrelevant to timezone. the server gives time in a standard (like GMT) and it is altered by your system's settings. I don't know how things work in Brazil, do you have Daylight Saving type changes down there? are all your distros set to handle that the same way? having them all only 1 hour off is quite strange.

---

### Post by PaulFXH on 2007-10-26
Yes, Brazil does have DST changes.
Indeed, the problem I have seems to have started when the clocks went forward by one hour 2-3 weeks ago.
Now, if I set the timezone at São Paulo, Brazil (this is the closest to where I am) and synchronize my clock, it invariably sets the clock one hour earlier than it really is. This is just as if the time server was unaware that the clocks went forward.
This is the reason that I had set all my clocks on manual. But, this doesn't seem to work as the clocks seem to get re-adjusted with respect to the computer clock when the system is shutdown/started up.
Anyway, setting the clocks to one hour ahead of my actual time zone has now allowed me to leave the clocks in automatic synchronization and everything looks fine.
Weird, though. Maybe somebody out there understands what's going on as I certainly don't.

---

### Post by cyberdork33 on 2007-10-26
> **PaulFXH said:**
> Yes, Brazil does have DST changes.
Indeed, the problem I have seems to have started when the clocks went forward by one hour 2-3 weeks ago.
Now, if I set the timezone at São Paulo, Brazil (this is the closest to where I am) and synchronize my clock, it invariably sets the clock one hour earlier than it really is. This is just as if the time server was unaware that the clocks went forward.
This is the reason that I had set all my clocks on manual. But, this doesn't seem to work as the clocks seem to get re-adjusted with respect to the computer clock when the system is shutdown/started up.
Anyway, setting the clocks to one hour ahead of my actual time zone has now allowed me to leave the clocks in automatic synchronization and everything looks fine.
Weird, though. Maybe somebody out there understands what's going on as I certainly don't.

My guess is that 2 of the distros did not change DST yet, and the others did. (In the US we just made a change in the way DST works, we will not turn back clocks for another couple weeks, and my guess is that someone thought that change applied to all DSTs) I am not sure where, but there should be a way to adjust the dates when the DST changes takes place, and these are set incorrectly. Setting to the timezone ahead of you should work though until the DST date comes on the OS with the error.

---

### Post by PaulFXH on 2007-10-26
Thanks for this.
While this nicely provides a mathematically valid explanation for the anomaly I had on my computer, it is perhaps less easy to understand the monolithic approach to global DST management assumed by the NTP servers (or rather by those who manage them).:confused:

---

### Post by cyberdork33 on 2007-10-26
> **PaulFXH said:**
> Thanks for this.
While this nicely provides a mathematically valid explanation for the anomaly I had on my computer, it is perhaps less easy to understand the monolithic approach to global DST management assumed by the NTP servers (or rather by those who manage them).:confused:

As I was trying to explain before. the timeservers are always the same. They do not change for DST or for timezone, they send out the same exact GMT time. Adjustments to GMT are made on your machine. I would ask about the DST settings in the forums or look in the documentation for your other distros. I did a quick look in Ubuntu for a way to adjust this, but I didn't find anything.


Timezone definitions are in /usr/share/zoneinfo , but they look like binary files.

---

### Post by Gen2ly on 2007-10-27
In Gentoo it may be different, but you can check your other distros and see.  We set our timezone in /etc/conf.d/clock.

Timezone info is in /usr/share/zoneinfo

Check and be sure your have the settings to Universal Time(UTC).

---

### Post by cyberdork33 on 2007-10-27
> **Dirk.R.Gently said:**
> In Gentoo it may be different, but you can check your other distros and see.  We set our timezone in /etc/conf.d/clock.

Timezone info is in /usr/share/zoneinfo

Check and be sure your have the settings to Universal Time(UTC).

I thought of that, but the difference should be more than 1 hour if that what the issue. This setting is in some weird file in Ubuntu anyway.
[https://help.ubuntu.com/community/UbuntuTime?action=show&redirect=ChangeTimezoneHowto#head-7f2edfd2f352f7f015759cd8eb7652deb69088aa](https://help.ubuntu.com/community/UbuntuTime?action=show&redirect=ChangeTimezoneHowto#head-7f2edfd2f352f7f015759cd8eb7652deb69088aa)

You can symlink the appropriate /usr/share/zoneinfo file to /etc/timezone like you do in gentoo though.

---

### Post by nick4mony on 2007-12-11
Hi guys,

I'll chip in with a late reply: my belief is **the only way to get the time to behave across all distributions is to set the BIOS clock to UTC.**

I'm not entirely sure what that means for Mac OS X, but if you run Windows, you'll have to put up with UTC-ish times in that OS (set to London and **disable daylight saving**).  This comment obviously applies to multiboot WinTel hardware as well.

You should be able to get all the Linux OSs to behave (ie to give the proper local time).  If someone has Mac OS X, maybe they can provide a comment whether it can be made to read the hardware clock in UTC.

The other comment I might make is that if you live in Brisbane or somewhere that has no daylight saving, you can obviously get away with setting the hardware clock to local time.

---

### Post by cyberdork33 on 2007-12-11
this is not necessarily true, although probably a good practice. However, Windows expects the hardware clock to be the local time, so if you are using that you have to keep it at the local time.

Macs don't have an adjustable hardware clock such as most PCs, (in fact, they do not even have a BIOS).

---

