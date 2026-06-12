---
title: "Zenbook crash when unplug AC power"
date: 2012-08-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by wim.glenn on 2012-08-05
So it's basically the problem in the title, when I unplug the AC power cable while computer is on, I get a sudden shutdown.  It's not repeatable every time, but it is very frequently.  The power plug is already pretty crappy and loose fitting, so even just bumping it can cause this crash sometimes and it is very annoying.  How can I fix it?  I have the UX31 running 12.04.

---

### Post by sadeh on 2012-09-17
I've been having this same problem for a while now, probably after a kernel update to 3.2.29. I got to the point of trying a fresh install, which didn't help...

What seemed to have done the trick is a BIOS update to version 213.
There have been no freezing or shut downs due to unplugging or re-plugging since the BOIS update.

Cheers.

---

### Post by sadeh on 2012-09-18
Update - a day later the problem came back.
To summarize it:
[INDENT]
Asus Zenbook UX31E
Fresh install of Ubuntu 12.04
kernel 3.2.0-30
BIOS 213
[/INDENT]
Whenever the AC is unplugged or re-plugged, the system either stops responding completely or crashes.

---

### Post by Chonnawonga on 2012-11-20
I'm still having this problem with Ubuntu 12.10 and BIOS version 214. Does anyone have any idea why this is happening, and/or can anyone help us debug this? Thanks!

---

### Post by Chonnawonga on 2012-11-20
FYI, there's a bug report filed: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/989191]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/989191")

---

### Post by wim.glenn on 2012-12-04
> wim@wim-zenbook:~$ uname -a
Linux wim-zenbook 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:48:01 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


I'm still having this problem on quantal quetzal 12.10.  Very annoying problem because the UX31 zenbook has a crappy loose power plug anyway, so you can disconnect it just by bumping it while it's on your lap, and then the whole OS crashes.  Ouch!

If anyone knows a workaround or fix, it would be greatly appreciated...

---

### Post by rzach on 2013-01-06
I had the same problem but it went away after I changed the kernel flags to

quiet splash drm.vblankoffdelay=1 i915.semaphores=1 i915.powersave=1 i915.i915_enable_rc6=1 acpi_os_name='Microsoft Windows XP'

as suggested in 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/989191](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/989191)

Weirdly enough, it didn't recur even when restarted without flags or with the flags I had originally.

---

### Post by PipoPT on 2013-01-24
I believe this problem is not because of Ubuntu.. I have the same problem with Windows 8, as I also had with Windows 7.

Yes it is true, the power cord is crappy..

---

### Post by wim.glenn on 2013-07-18
I put those kernel flags in, sudo update-grub and restart, but it does not fix the problem for me..  :(   
This laptop kind of sucks on Ubuntu, a shame because it's nice in many other ways

---

### Post by jaymanu on 2013-10-22
I had the same problem on my UX31. VERY annoying, as the power plug is now so loose that i need to put some a pen under it to keep it connected, so then I can't move the zenbook anywhere without unplugging and having to restart the OS.
I tried many suggestions from this thread and others, nothing worked.

Then I found a purely hardware and very simple solution that is (for now) working for me : DISCONNECT then RECONNECT the BATTERY.
Though, on those netbooks, it's a bit trickier than ejecting a battery pack, it requires unscrewing the back plate, and carefully unplugging the connector without pulling on the cables.
But then, the issue disappeared for me since yesterday !! And if it reappears, i will try to repeat this.

I'm no expert in hardware, but I suppose that there must be a bug in the firmware of some charge processor. This bug could be triggered by some condition, ie bad recovering from sleep mode, full discharge or anything similar. And then, the only way I know to reset it, is to unplug the battery.

---

### Post by jaymanu on 2013-11-06
And : CONFIRMED !

2 weeks later, the issue re appeared. I again opened the laptop and unplugged the battery : PROBLEM GONE AGAIN...
I guess the charge firmware might get in a confused state at some point (while suspending ? when battery goes empty ? i can't tell)

Did anyone else try doing this ?

---

### Post by Chonnawonga on 2013-11-06
Hi jaymanu,

I've been doing this too. So far the problems haven't reappeared, but I haven't been using that computer much, so we'll see!

---

