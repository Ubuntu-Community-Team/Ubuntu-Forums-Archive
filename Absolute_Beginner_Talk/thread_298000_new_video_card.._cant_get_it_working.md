---
title: "new video card.. cant get it working"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by ironslave on 2006-11-12
i upgraded to a newer card.. from a radeon 9250 to an x1300 but now i cant get the desktop up... i tried recinfiguring the xorg file with dpkg-reconfigure xserver-xorg... but now i cant even get a prompt... can anyone help me?

---

### Post by joshsherman on 2006-11-14
When booting, do you see the splash screen?

Once booted try doing alt+ctrl+F1 it should give you a login prompt.  From there you should be able to editor your xorg.conf file manually to attempt to fix the issue.  The file's in /etc/X11/xorg.conf  Perhaps you need to use a different driver for the new card?

-j

---

### Post by ReaderRat on 2006-11-14
> **ironslave said:**
> i upgraded to a newer card.. from a radeon 9250 to an x1300 but now i cant get the desktop up... i tried recinfiguring the xorg file with dpkg-reconfigure xserver-xorg... but now i cant even get a prompt... can anyone help me?
Try this:

[**Radeon Driver Info**](https://help.ubuntu.com/community/RadeonDriver)

---

