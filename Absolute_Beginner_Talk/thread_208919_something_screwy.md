---
title: "something screwy"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by firebird45331 on 2006-07-04
I turn on ubuntu and it's in 640X480.  I goto change it in setup and the only thing available to me is 640X480.  It was running in 1024x768 earlier lastnight.  So I shut everything down go cash a check and buy a case of beer to come back and do some  tinkering.  When I reboot it's back in 1024x768.  Why?

---

### Post by someusernoob on 2006-07-04
I had this once, it was because i turned on my monitor _after_ Ubuntu booted. So when X and Gnome were allready loaded.

After a reboot with the monitor on it was, just like yours, normal again. So everytime i turn on my computer now i make sure the monitor is on.

---

### Post by steve.horsley on 2006-07-04
Good point someusernoob. This is probably the probem. If so, just turning the monitor on and then restarting X with Alt-Ctl-Backspace might do the trick. 

Ubuntu does a hardware check as it's starting X, and if it's not sure what monitor is there, it defaults to a safe 640*480. You can overcome this by editing /etc/X11/xorg.conf and setting the appropriate HorizSync and VertRefresh rates in the monitor section.

---

### Post by Jagot on 2006-07-04
You could try:

```
sudo dpkg-reconfigure xserver-xorg
```

---

