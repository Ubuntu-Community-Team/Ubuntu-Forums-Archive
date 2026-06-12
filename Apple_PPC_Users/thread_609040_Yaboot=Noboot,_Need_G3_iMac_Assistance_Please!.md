---
title: "Yaboot=Noboot, Need G3 iMac Assistance Please!"
date: 2007-11-10
forum: Apple PPC Users
---

### Post by CREEPING DEATH on 2007-11-10
A friend of mine has a dark blue slot-loading iMac that was given to her, I'm trying to fix it up with Xubuntu because the OS 9.1 install that was on it was messed up.  Now it's totally hosed!
Specs are:  400 mhz, 128 mb ram, 10 gb hdd.
When I started Thursday night, it booted into 9.1 with some error messages.  I installed Ubuntu 7.10 with the Alternate CD, telling it to use the entire hdd, intending to apt-get install xubuntu-desktop then apt-get remove ubuntu-desktop on it after it was installed.  Instead, now the thing won't boot into anything.
If I try to boot, everything seems to go fine until it says "Loading, please wait..."  Then it sits there for a few minutes, until it decides that /dev/hda3 doesn't exist and drops me to a BusyBox terminal.  Ugh.
So I try to reinstall using a Xubuntu 7.10 LiveCD, it won't boot to the CD.  It won't boot with a Xubuntu 7.10 Alternate either.  It tries to boot from the CD when I tell it to but ends up trying to boot from the hdd and the same no-boot.
I'm not sure what the problem is, but I really need to get this thing going soon.  I've already pulled the battery and let it sit overnight, no changes in the morning when I started over again.

HELP!

CD

---

### Post by CREEPING DEATH on 2007-11-10
Even better, I found the fix here on the forums.  Sort of, at least.
**Why is there no sticky that yaboot on 7.10 doesn't work???**
Since the last install I'd tried was a Net Boot CD, once I got it running I did an ```
sudo apt-get install xubuntu-desktop
```
Now the damn thing shuts down while trying to boot!  The light stays on but the screen goes black and the drive stops.  WTFO?
I think I'm going back to strictly X86 machines once I get this hting running....

CD

---

### Post by bodycoach2 on 2007-11-10
With the older iMacs, I recommend loading Xubuntu 6.06.1. It the only one that seems to go on with no problems. Once you get that installed, you can upgrade from there, if you decide. Once you upgrade to 6.10, you'll need to adjust the xorg.conf. There's a link in the stickies. You can upgrade from there to 7.04, but I wouldn't recommend going to 7.10 yet. I haven't seen any real need to yet.

---

### Post by CREEPING DEATH on 2007-11-10
> **bodycoach2 said:**
> With the older iMacs, I recommend loading Xubuntu 6.06.1. It the only one that seems to go on with no problems. Once you get that installed, you can upgrade from there, if you decide. Once you upgrade to 6.10, you'll need to adjust the xorg.conf. There's a link in the stickies. You can upgrade from there to 7.04, but I wouldn't recommend going to 7.10 yet. I haven't seen any real need to yet.

I downloaded the Xubuntu 7.04 Alternate CD, now I need to try to find a blank CD to burn it to and try again.  I need Gnash and FF 2.0 or better what version has these?

CD

---

### Post by Auria on 2007-11-10
> **CREEPING DEATH said:**
> I downloaded the Xubuntu 7.04 Alternate CD, now I need to try to find a blank CD to burn it to and try again.  I need Gnash and FF 2.0 or better what version has these?

CD

you can get them on this version.
PS not sure if you've ever tried gnash but don't rely on it too much

---

### Post by CREEPING DEATH on 2007-11-11
Gave up and installed Lenny...

CD

---

