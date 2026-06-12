---
title: "LiveCD on ppc"
date: 2006-07-07
forum: Apple PPC Users
---

### Post by Auria on 2006-07-07
I downloaded Ubuntu-powerpc-6.06 and burned a live CD... then i tried booting up from it - the ubuntu progress bar loads completely, but after i get this message:

"Failed to start the X server.
It is likely it is not set up correctly.
Would you like to see the X server output
to diagnose the problem?"

i've found other threads mentionning it but i couldn't understand what to do (and i'm not even sure it's the same problem)

i have a powerpc G4 right now... (os X 10.3.9) what can be the problem? is there a fix? thanks!

---

### Post by 3rdalbum on 2006-07-08
After that message appears, you will have a command line on your screen. Type:

```

sudo nano /etc/X11/xorg.conf

```

When asked for a password, just hit the Return key.

Use the down arrow key to scroll down to Section "Device". In that section, it should say:
```

     Driver      "ati"

```

If it doesn't say that, then change it. Press Control-X to quit nano, save your changes back to the same file. Then type:
```

startx

```

and see what happens.

If that doesn't work, then try changing the Driver to "vesa". If your computer has a nvidea card rather than ATI, change it to "nv".

---

### Post by Auria on 2006-07-08
thanks for your reply, i'm trying right away!

---

