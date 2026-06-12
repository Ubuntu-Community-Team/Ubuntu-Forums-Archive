---
title: "Trackpad Does Not load at startup"
date: 2013-01-14
forum: Apple Hardware Users
---

### Post by NickSH on 2013-01-14
Hi,
I am running Ubuntu 12.04 on a 2011 macbook air.  

I have noticed over the last month that the trackpad does not always seem to load at startup.  I can log in ok, and the 'pointer' will appear on the screen, but will not respond to any touches, etc.
To make matters more confusing, this does not happen consistently.  It seems to happen approximately 1/3 of the time.  When it happens, it typically requires two reboots to get the system to boot (load/start up the trackpad) properly.

Any thoughts?  I'm not sure where to look (or if I should be looking) in the log files for answers.
Thanks,
Nick

---

### Post by NickSH on 2013-01-14
After a bit more searching....would using mkinitrd be a possible fix?

---

### Post by cellocgw on 2013-01-15
This may not be the sanest approach, but here's something I did on an old PPC laptop (Ubuntu 12.04) because the trackpad settings failed to "stick" across a reboot.
Inside my .bashrc file, added the lines

sudo chmod 777 /dev/adb <<endsu
{my password}
endsu
trackpad tap
trackpad drag

And that works just fine.  If you want to be more careful, you could add a couple followup lines to return /dev/adb to 511 permissions.

---

### Post by NickSH on 2013-01-15
Thanks for your reply.  I'm not sure that this will work for me though, since /dev/adb does not seem to exist.

Nick

---

### Post by cellocgw on 2013-01-15
> **NickSH said:**
> Thanks for your reply.  I'm not sure that this will work for me though, since /dev/adb does not seem to exist.

Nick

Sorry -- you're correct, as only older Macs w/ ADB (Apple Desktop Bus) -based trackpads have this.  But you should have a corresponding tool in /dev which the "trackpad" command accesses.

---

