---
title: "[SOLVED] Trouble with 1440 resolution"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by H3retic on 2007-09-23
I know there are other forum topics adressing this, but as an abslute beginner I'm looking for something "idiot proof".

Running ubuntu studio, and can't use the change resolutions functions in 'System' to change to **1440x900**.  Allready installed nvidia drivers through restricted drivers manager.  Don't know what to try next.  Help!

---

### Post by overdrank on 2007-09-23
> **H3retic said:**
> I know there are other forum topics adressing this, but as an abslute beginner I'm looking for something "idiot proof".

Running ubuntu studio, and can't use the change resolutions functions in 'System' to change to **1440x900**.  Allready installed nvidia drivers through restricted drivers manager.  Don't know what to try next.  Help!

Hi maybe this link will help
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by H3retic on 2007-09-23
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg

Worked fine for me.
Thanks for the good advice!

---

