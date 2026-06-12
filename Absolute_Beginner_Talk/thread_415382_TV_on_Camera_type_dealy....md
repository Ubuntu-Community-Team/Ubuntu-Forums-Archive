---
title: "TV on Camera type dealy..."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by SkonesMickLoud on 2007-04-20
So I installed Ubuntu 7.04, all went well with no problems until the restart.

Now, my screen reminds me of what a TV looks like when viewed through a camera.

With the horizontal lines going up the screen, only it appears in the center of the screen, and the lines are tiny.

It seems to show up more in some programs, and almost nonexistent in others.

I'd throw up a screen shot, but it's not showing up in pictures.

Anyone know what's going on?

---

### Post by lamalex on 2007-04-20
your refresh rate was probably detected wrong, boot into recovery mode (hit esc when it says grub stage 1.5) and then do this command
```

dpkg-reconfigure -phigh xserver-xorg

```
you'll need to know your video card drivers, monitor supported refresh rates, and your desired resolutions, for the most part just pick the defaults. If it fails try it without -phigh

---

