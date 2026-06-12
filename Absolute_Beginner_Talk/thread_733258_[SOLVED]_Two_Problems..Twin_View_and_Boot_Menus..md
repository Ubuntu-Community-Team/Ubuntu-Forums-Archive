---
title: "[SOLVED] Two Problems..Twin View and Boot Menus."
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Daveg4otu on 2008-03-23
JUst got started with Ubuntu - 7.10....

First  (minor) thing - how can I edit the boot menu to put XP at the top (default) position?

The other more involved problem is with twin view.

Situation is that the two monitors- whem system boots to XP - have the "Master" monitor on the right (seen facing) and slave on left - both monitors on 1024 x 768,independant screens with desktop  across both - in other words - icons and taskbars on right- just wallpaper on left.

Trying to achieve same on Ubuntu the first problem is that  it seems to prefer the LH monitor - in fact without rwin view it would only run on the LH one(which is connected to the DVT socket on the Ti4200 card) unless I disabled the LH monitor  at which point it would if rebooted  use the RH one.

I have enabled and installed the Nvidia GLX drivers and tried every possible way of setting things up....They show as installed and I get the NV splashscreen on bootup (and shutdown)

The nearest I can get is to use "Mirror" using (for both monitors)these settings

MONITOR  CRT 1024 x 768,Scr Res 800 x600,55hz (would like to get Sc Res to be consistent at 1024/768 - but half the time it presents a screen that is too long horizontally and scrolls.).....
with LH as Sc1 and RH as Sc2- Mirror.

Even this is not consistent - doesn't appear to save the settings from one boot to the next...occasionally failing to boot at al(Monitor shows "out of Range"l and requiring resetting via the Recovery mode back to basics.

Any ideas- thoughs or whatever very welcome - but try please to keep it in words iof one syllable- this is a new   ballgame for me.

Sorry this is so long...
Dave

---

### Post by herbster on 2008-03-23
Okay, for your GRUB boot menu to have XP at the top, that's easy as hell, just paste the results of

```
cat /boot/grub/menu.lst
```


For the Twinview issue, paste the results of

```
cat /etc/X11/xorg.conf
```

And have you tried using nvidia-settings? Hit ALT+F2 and type

```
nvidia-settings
```

hit ENTER and you should get a little program whereby you can tweak your display settings. Post what **your** nvidia-settings shows on this menu:

[img]http://www.bobgill.net/nvidiasettings.jpg[/img]

---

### Post by ad_267 on 2008-03-23
You will need to be root to run nvidia-settings as it needs to edit the xorg.conf file, so you use

```
sudo nvidia-settings
```

Edit: Sorry, didn't read the last post fully. If you're just looking at the settings you won't need to use sudo

I found that nvidia-settings worked a lot better for setting up my two monitors with twin-view than the gnome tool

---

### Post by herbster on 2008-03-23
ad_267, you're right he will need to use sudo, I just want to know what his current settings are.

---

### Post by Daveg4otu on 2008-03-23
Thanks all for quick replies -got to work now - will try all suggestions in morning...

Dave

---

### Post by Daveg4otu on 2008-03-24
Thanks for the nVidia  settings info - got the two screens working OK now with only two problems - I seem to  have lost the Title Bar (top colored Bar) on all windows - can still drag windows using alt and grab  but would like to get the bar back if at all poss.

Have the screens set as master on L .slave on R and desktop extends across both. Screen Overall resolution is 2560-1024

In addition it  prevents (some how ) access to the Terminal unless I go back to single screen working

D

---

### Post by herbster on 2008-03-24
The title bar is perhaps an issue with Emerald. Do you have desktop effects enabled? System > Preferences > Desktop Effects. What's there?

Can you be more specific how the terminal isn't running? Are you clicking Applications > Accessories > Terminal and it won't open?

---

### Post by Daveg4otu on 2008-03-24
Herbster - thanks - but got Titlebar and Terminal sorted no.

---

