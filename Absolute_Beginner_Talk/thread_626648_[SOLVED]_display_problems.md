---
title: "[SOLVED] display problems"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by markiv on 2007-11-29
Hi!
I've been using Ubuntu for a while now...
Suddenly, today, something went wrong with the display.
When loading Ubuntu, everything's fine till the Splash Screen. It's when the userid/password stuff comes up when the display goes all wonky. I can't see a thing. It's simply a jumble of colours. I think it's a resolution problem but what can i do if i can't even log into Ubuntu?

is there anything i can do to change these res. settings (if they ARE the problem) using the 'recovery mode'?

thanks in advance
 - Vikram.

---

### Post by nixx on 2007-11-29
is there anything you might have done to cause this behaviour ? a rogue script, botched update or even a successful update, just something that might indicate what went wrong ? it shouldn't just *go wrong* out of the blue...

---

### Post by markiv on 2007-11-29
it did.
upgraded to gutsy some 3 weeks back (ok, it wasn't a clean, fresh upgrade). linux was working perfect with a 1280x1024. and windows with 1024x768.
i changed the resolution in *windows.* to something higher and **back**.

and then when i try load ubuntu, this happened...
it IS 'out of the blue'.

---

### Post by viking777 on 2007-11-29
Look in /etc/X11 and see if you have an older copy of xorg.conf. If you have then rename the existing one to something else and rename the older one to xorg.conf then reboot and see if it helps.

You will probably have to boot into recovery mode to do this unless you have another distro on the same drive or a live cd.

The commands would be 

```
cd /etc/X11
```
```
ls
```
```
mv xorg.conf xorg.conf.old
```
```
mv xorg.conf~ xorg.conf
```

---

### Post by markiv on 2007-11-29
ended up reconfiguring xorg. and everything works fine now.

thanks for the reply.

---

