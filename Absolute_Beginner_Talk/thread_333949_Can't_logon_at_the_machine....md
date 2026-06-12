---
title: "Can't logon at the machine..."
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by mark_l_sanders on 2007-01-08
Problems logging in at the machine! - My password / username are accepted (no red error saying 'bad password'), but I just get returned to login screen - this is directly after a reboot!! When I deliberately put in a bad password, I get the expected error, so it's not a password issue.

I CAN login via ssh/telnet etc, so I know I've got the password right!!

Disk is very very full - might this be causing problems?

As I say, I can login remotely - anything I can do?

thanks

mark

---

### Post by Jussi Kukkonen on 2007-01-08
> Disk is very very full - might this be causing problems?

Yes, If I remember correctly the symptoms in that case are exactly those. X can't start because it can't create the temporary files it needs.

---

### Post by taurus on 2007-01-08
Boot into recovery mode from GRUB menu and at the prompt, clean up the archives.

```
apt-get clean
```
That would buy you some free space.  May want to empty trash, ~/.Trash, or anything else that you don't need.

---

### Post by mark_l_sanders on 2007-01-08
Genius - cleaned up apt-get and Trash, that bought me a login, so I could mount a usb hdd and backup some huge server archive files.
Thanks guys

mark

---

