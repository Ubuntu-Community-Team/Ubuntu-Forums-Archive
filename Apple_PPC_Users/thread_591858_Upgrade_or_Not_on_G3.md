---
title: "Upgrade or Not on G3"
date: 2007-10-25
forum: Apple PPC Users
---

### Post by bodycoach2 on 2007-10-25
I've been watching the forum, and it seems that upgrading a G3 is an absolute misery. I know that the forum is usually full of problems, as most who have success rarely need to post. So:
Has anyone had a successful, no issue upgrade of a G3?

---

### Post by dnichols on 2007-10-28
I'm happy after upgrading my white G3 ibook to 7.10.

Wireless roaming now works for me for the very first time.  And the system seems faster and more responsive.

I've had the following problems:

1.  I got dumped to busybox after the install reboot but the solution at [http://ubuntuforums.org/showthread.php?t=581280](http://ubuntuforums.org/showthread.php?t=581280) worked for me.

2.  My display resolution went back down to 800x600 and reconfiguring xserver-xorg didn't help.  Then I read the logs and found an error with the refresh rates.  I tweaked my refresh rates and my resolution is back to normal.

3.  There was a gnome daemon that was giving me an error message when I logged in to the gnome-desktop, but I switched to xubuntu with kdm, which I'm happier with anyway, and that is no longer an issue.

---

