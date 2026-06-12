---
title: "Help with trackpad stupid mistake in  a MBP 5,1"
date: 2009-07-08
forum: Apple Hardware Users
---

### Post by GeneralSunTzu on 2009-07-08
I have a very jumpy cursor on my MBP 5,1.
Followed what's in the wiki, installed pommed, etc., all to no avail.
In one of the latest attempts I unchecked by mistake the box, in "trackpad", which says "use trackpad", and of course I now have a frozen cursor, without any idea on how to defrost it...
I have no external mouse at home.
Can I do anything different from re-installing JJ again?
Thank you.

---

### Post by GeneralSunTzu on 2009-07-10
Bump...

---

### Post by alexmurray on 2009-07-10
Hit Alt-F2 then type gnome-terminal and type in the following:

```
gconftool-2 --toggle /desktop/gnome/peripherals/mouse/touchpad_enabled
```

this should reenable your trackpad.

---

### Post by GeneralSunTzu on 2009-07-10
Thank you, I tried, but the cursor stay frozen.
Now, I had previously amended a file named …policy.inf I think, but I cannot remember the complete path name.
Using your trick I can gedit it and maybe stop this disaster.
Alternatively, a pal is bringing me tomorrow a USB mouse, which should work (I cross my fingers...).
Thanks for the head-up. Won't forget it.

---

