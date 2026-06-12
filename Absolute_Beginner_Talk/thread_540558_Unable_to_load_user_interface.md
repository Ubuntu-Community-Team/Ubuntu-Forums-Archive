---
title: "Unable to load user interface"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by DerekDrees on 2007-09-01
Okay, so my video card failed, and when i switched back to the onboard ubuntu didn't load, i got an xserve message that said my gui coulnd't load, it worked when i had my failed video card in, i can't even boot from the live cd, all of this happend when i tried to install beryl with the instructions for the auto-intstall, i broke the cd in anger, and i am downloading the .iso, just in case.

Thanks 
Derek

---

### Post by taurus on 2007-09-01
You probably need to reconfigure your X again since now you use a different video card.  Boot into recovery mode and at the prompt, run

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
dpkg-reconfigure xserver-xorg
```
When done, reboot and see what happens.

```
shutdown -r now
```

---

### Post by DerekDrees on 2007-09-01
ok, will do

---

