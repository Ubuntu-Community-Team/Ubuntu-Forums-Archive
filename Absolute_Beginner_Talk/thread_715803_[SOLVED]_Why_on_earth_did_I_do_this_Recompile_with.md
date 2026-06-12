---
title: "[SOLVED] Why on earth did I do this? Recompile with kernelcheck"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by camini on 2008-03-05
ok, so I wanted to make the video quality of movie playback better..
followed some advice to recompile using master_kernel threads and kernelcheck..
all went fine and now I have all these new boot options, and none work correctly..
My beautiful setup is lost.. snif..

All I have left is terrible resolution, wrong keyboard layout during login, no nvidia driver etc..
I'm so lost and sad.
For me this will be a lesson: don't do stuff that you don't understand.

I think I will do a fresh re-install now and cry :(

---

### Post by camini on 2008-03-05
Well.. a couple of reboots later it seems I can stop crying and enjoy a working system again.
I had to uninstall nvidia driver, re-install with envy, reconfigure xorg.conf and that's it.
At first I got a nautilus/bonobo error, which now does not seem to happen again..
phew.. I got scared.
Sorry I panicked..

So now I'm running the latest kernel..

and the movie video quality is no better (which was the whole purpose really) - it ain't bad, but I just get these horizontal 'break lines' in the image..  wish I could find a way to resolve this..

---

### Post by camini on 2008-03-05
Solved the video problem as well - which was actually 'tearing', affecting the whole X.
Had to set Sync to VBLANK in nvidia settings and ccsm as well as setting my monitor's refresh rate in both to 75hz.
Not sure which of the settings solved the tearing but my X and videos are now smooth like they should be - happy!

---

