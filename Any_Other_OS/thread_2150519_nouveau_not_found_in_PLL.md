---
title: "nouveau not found in PLL"
date: 2013-06-01
forum: Any Other OS
---

### Post by arranskye on 2013-06-01
Hi, I have just got my g.daughters interested in Linux. They choose mageia 2 but this support community is small and replies are a long time comming.

They installed mageia 2 and dual booted with windows xp. no problems. Played around with the system for  a week then decided to download the updates.

During the time that the os system was working correctly a nvidia screen showed briefly as well as the mageia screen during boot up, and all worked fine.

After updating the nvidia screen no longer showed and a small black & white text box appeared very briefly . No time to read but just caught the words Xorg & nouveau.
 Now the screen continually flashes and jumps around like a demented demon. A message appears in the top left corner
 Register 4.5518701 Nouveau not found in PLL 0x00004028
I have been on the internet tyring to source help and it would appear that this has been either a bug or a problem in ubuntu in the past so although its not a ubuntu distro I thought someone might be able to offer some help.  if this is not acceptable please advise. thanks

---

### Post by Frogs Hair on 2013-06-01
Is this an rpm or debian package system ? I ask because Ubuntu uses Debian and the package system commands would be different for rpm. I know this distro is Mandriva based which uses rpm. The procedure for removing or adding drivers may be different from the shell.

---

### Post by coffeecat on 2013-06-01
*Thread moved to **Other OS/Distro Support**.*

---

### Post by arranskye on 2013-06-01
> **Frogs Hair said:**
> Is this an rpm or debian package system ? I ask because Ubuntu uses Debian and the package system commands would be different for rpm. I know this distro is Mandira based which uses rpm. The procedure for removing or adding drivers may be different from the shell.

Hi FH    Its mandriva  mageia i586 Gnome 32 bit.  Sorry my  knowledge is too limited to offer anything more concise than that but looked on 'net and found Mageia is a RPM based Linux distro Hope that helps.

Between the jumps & flashes i managed to get into the control centre and found this: graphics:  gallium 0.4 on NVAA. There was a option for forced fallback mode.
I turned this on, rebooted and now we have got a stable usable screen but Oh dear the most awful desktop  ugh  I dont know anything about the differences in the various distro desktops but I think the may be a unity desktop. UGH

please can you help us to sort the drivers and get the gnome desktop back

---

### Post by Frogs Hair on 2013-06-01
I am out of my element with this distro and I see they offer a number of different window managers . I could probably get and Idea what the fall-back session is with a screen shot. I would look for a graphics or additional drivers utility for adding and removing drivers because it may display what driver is installed.

---

### Post by arranskye on 2013-06-01
Thanks a lot for trying so hard.   I have now discovered that the desktop is is a limited version of gnome.  no icons just dropdown menus.
The fallback mode as you probable know is to permit the os to run even if the video card is not totally supported, although this was not the case as everything was working ok prior to the updates being installed

The video card in the laptop is  Nvidia  GeForce 8200m G. The desktop version now running is stated as gnome 3.4.1

On boot up  originally we had the options of mageia 2   mageia safe mode   window xp  Now we have these plus desktop 586 3.3.6 & 3.3.45 as listed below.  i still just choose mageia 2 and it appears to boot into 3.3.6 586-mga2



/lib/modules/3.3.6-desktop586-2.mga2/kernel/drivers/gpu/drm/nouveau
/lib/modules/3.3.6-desktop586-2.mga2/kernel/drivers/gpu/drm/nouveau/nouveau.ko.xz
/lib/modules/3.4.45-desktop586-1.mga2/kernel/drivers/gpu/drm/nouveau
/lib/modules/3.4.45-desktop586-1.mga2/kernel/drivers/gpu/drm/nouveau/nouveau.ko.xz
/usr/lib/libdrm_nouveau.so.1
/usr/lib/libdrm_nouveau.so.1.0.0
/usr/lib/dri/nouveau_dri.so
/usr/lib/dri/nouveau_vieux_dri.so
/usr/lib/xorg/modules/drivers/nouveau_drv.la
/usr/lib/xorg/modules/drivers/nouveau_drv.so
/usr/share/man/man4/nouveau.4.xz

Hope this helps.  i will do my best to provide any more info you require.  Its all part of learning linux but with the help available on these forums ubuntu is a doddle compared to mageia.    Thanks again.

---

### Post by Frogs Hair on 2013-06-01
[COLOR=#000000]It reads like the you are possibly using the gnome fallback session and most of the screenshots I can find are of the KDE desktop environment that is why I was curious about the DE .  Nouveau is the default open source driver on Ubuntu  and a driver utility may offer other options . Log and update history files may also offer some information about what went wrong. 

[/COLOR][COLOR=#000000]Mageia 2 originally came with the option for Gnome  3.4 which is is what is under the hood on Ubuntu 12.04.   [/COLOR][COLOR=#000000]Mageia 3 has a Gnome 3.6 option. [/COLOR]

---

### Post by arranskye on 2013-06-02
Hi, yes it was a fallback limited gnome.  Anyway looked in the mageia software centre, graphics/nvidia. instructed that dependancies need to be downloaded. Did that reboot. No change still had limited gnome.  Installed KDE, back to jumping flashing screen/desktop. However KDE desktop was easier to navigate and also to access hardware. Installed Xorg rebooted and got message suggesting nvidia driver was more appropriate for my system.  Removed Xorg. installed nividia plus dependancies and all ok.

Much as I like the gnome destop I have found Kde is much better for "nuts & Bolts" learning so I will stick with it for a while.

Thank you for trying so hard to help. It was very much appreciated because as yet no response from mageia forums.

kind regards  margaret

---

