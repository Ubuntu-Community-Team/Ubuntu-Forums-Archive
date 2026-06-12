---
title: "How To: Beryl After Fresh Ubuntu Feisty Install With nVidia 6200 Card."
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Presto123 on 2007-10-27
I know that there's more out there with this information, but this is the ONLY way I could get it to work. I hope this helps someone who is experiencing the same problems.

GeForce 6200 256mb (PCI) with Beryl after Fresh Feisty Install:

Install all updates, do not enable restricted drivers yet.
Let it restart, then goto add/remove programs and search for "nvidia" and use the "NVidia binary X.Org driver" (4 star rating).

Install that and restart (this step may be removed if you think it doesn't matter).

NOW...Go to "Restricted Drivers Manager" in "System/Administration" and enable the NVidia driver and let it restart.

NOW...Goto "System/Preferences" and enable desktop effects.

Now Add/Remove, then type in "Beryl" and install "Beryl Settings Manager". (I restarted after this.)

Right Click and create a launcher, type: launcher, (Name: whatever you want.) with this command & click "Ok": gksudo nvidia-settings

Double Click it and set it up how you want. Remember the best way to do it is "Save to X Configuration File" and quit.

I enabled both monitors here, "Twinview" after all of this checked out, and "Ctrl+Alt+Backspace" to restart Ubuntu to log screen.

And when/if the minimize disappears, type this in "Terminal" and "Ctrl+Alt+Backspace" :
 sudo nvidia-xconfig --add-argb-glx-visuals -d 24

This whole process may throw some "Useless" steps in to everyone else, but for me, it worked without fail. (So far ;D )

Beryl works and I enjoy having it back...**Spins Cube**

---

### Post by Presto123 on 2007-10-27
If this works for you on another Nvidia card, please post the card type and we will see how many it works for.

---

### Post by Presto123 on 2007-10-28
I have edited the information; changing "Beryl Manager" to "Beryl Settings Manager". I have both installed, but I believe "Beryl Settings Manager" will suffice. If you have problems with just that app, just add the "Beryl Manager" (Ruby icon in "Add/Remove") as well.

Also, this works in both 32 bit and 64 bit OS's.

---

