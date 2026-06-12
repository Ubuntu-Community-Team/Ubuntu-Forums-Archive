---
title: "[SOLVED] After Enabling Desktop Effects Cannot Boot"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by WorldTripping on 2007-09-13
Morning,

I have an nVidia 'GeForce4 420 Go' graphics card in a Toshiba 'Satellite' 1.6GHz 256MB RAM laptop.

I enabled 'Desktop Effects' and was told that I needed to enable the 'restricted drivers', and reboot; which I did.

Now when I boot the entire screen is white/grey and flashing, the login screen is still under there somewhere, it's just not visible.

I can boot into command line recovery mode, but what I do I need to edit to get this resolved ?

Many thanks in advance.

---

### Post by Perfect Storm on 2007-09-13
in CLI,

```

sudo nano /etc/X11/xorg.conf
```


check if the driver is set to "nvidia"

Save (ctrl)+(o) exit (ctrl)+(x)

```

sudo reboot
```


If the driver is set to "nvidia" change it back to "nv" to get your X back.

---

### Post by WorldTripping on 2007-09-13
BRILLIANT !!

Thanks for that, it worked a treat.

On a side note, any idea what is happening ?

I'm wondering if my card cannot handle the 3d acceleration properly.

Anything I can do about this ?

Thanks in advance.

---

### Post by Perfect Storm on 2007-09-13
Which work? Are you using "nv" or "nvidia" driver now?

---

### Post by WorldTripping on 2007-09-14
It was set to 'nvidia' and I reset it to 'nv'.

I'm assuming that this card can't handle the 3d stuff properly, and I'm going to have to stick with the normal desktop.

Cheers for the help.

---

### Post by splintercellguy on 2007-09-14
It may be worth a shot to try Envy or the nVidia driver installer, but at your own risk of course.

---

### Post by WorldTripping on 2007-09-14
Cheers for that, I'll give it a shot this weekend.

Thanks for all the help.

---

### Post by LowSky on 2007-09-14
i bet your card can hadke it, use envy and everything should work

---

