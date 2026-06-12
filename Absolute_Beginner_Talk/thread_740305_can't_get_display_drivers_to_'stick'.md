---
title: "can't get display drivers to 'stick'"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by steve_steve on 2008-03-30
After giving up on getting Compiz to work, I'm not able to get this old IBM box to run the nvidia legacy drivers, at least not for more than one re-boot.

If I:

sudo dpkg-reconfigure -phigh xserver-xorg

and re-boot, it works fine, using the nv legacy driver( it's got an old TNT or Riva card).

If I re-boot again, it reverts to the Vesa driver where the best it'll do is 800 x 600.  If I try to uninstall or reinstall the legacy driver I get this error:

E: /var/cache/apt/archives/nvidia-glx-legacy_1.0.7185+2.6.22.4-14.9_i386.deb: subprocess pre-installation script returned error exit status 2

Being a total noob, I have no idea what to do about it.  I've deleted all the nvidea files in var/cache/apt/archive, I've uninstalled & reinstalled the Restricted Driver Manager.  I don't get why it'll use the nvidia driver just one session, then revert to Vesa (which looks terrible).

Forgive me if I've left out any useful details.  Please advise before I give up & reinstall Gusty altogether - sort of a pain, as I have WINE running with stuff that I'd have to reinstall as well.

Thanks in Advance.

---

### Post by c-ron on 2008-03-30
Have you tried Envy?: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

You can uninstall previous drivers and then 'Manually Install' the nvdia-legacy driver (71.86).

---

### Post by steve_steve on 2008-03-30
Thanks for the reply.  I did give Envy a try, but I still have the same problem.

If I sudo dpkg-reconfigure -phigh xserver-xorg & re-boot, it'll run in 1600 x 1200.  If I leave that alone, it's ok.  If I change the resolution to 1280 x 960 (where I'd like it) and re-boot, it reverts to the Vesa driver and displays at 800 x 600.  I don't mean to sound fussy, but 800 x 600 is way too big, and 1600 x 1200 is pretty small (although I did increase the font to 128, and it's a little more usable).  Any more clues are greatly appreciated.

---

