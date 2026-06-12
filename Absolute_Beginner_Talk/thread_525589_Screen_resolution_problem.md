---
title: "Screen resolution problem"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by TRStealthX on 2007-08-14
Hey there. Well I just started using Ubuntu now, and I'm THE noob for this linux stuff. I don't know how to do anything yet. When I used Windows XP, it allowed me to have a resolution of 1280x1204 and in ubuntu, I don't get that. It recognizes my graphics card which is an Ati radeon xpress200 (this is an old computer) but still doesn't give me the option that I want.

Please help...

Thanks.

---

### Post by heimo on 2007-08-14
You could start here:
[Fix Video Resolution]("https://help.ubuntu.com/community/FixVideoResolutionHowto")
[Fixing Resolution/refresh rate problems]("http://ubuntuforums.org/showpost.php?p=454217&postcount=1")

---

### Post by riven0 on 2007-08-14
Open the terminal, (Applications >> Accessories >> Terminal) and copy and paste this: **sudo dpkg-reoconfigure xserver-xorg**

Select options by hitting the space bar, NOT enter. Then restart the xserver by hitting CTRL+ALT+Backspace. Hopefully, that'll work.

---

### Post by Hospadar on 2007-08-14
Sometimes screen resolutions are not automatically detected correctly upon setup
in a terminal (Applications->accessories->Terminal) enter this:
```
sudo dpkg-reconfigure xserver-xorg
``` (just use your regular user password when it asks)
you'll be able to just skip through most of the options, leaving things as default, but then you will come to a screen that looks like [this]("http://tuxicity.files.wordpress.com/2006/12/screenshot-terminal-5.png").  scroll down and use space to select 1280x1024 and all the resolutions below it.

Then, once you get all the way through that dialog, do a ctrl-alt-backspace to restart gnome (this will log you out) then log back in, and pick your resolution from System->Preferences->Resolution

---

### Post by TRStealthX on 2007-08-14
> **Hospadar said:**
> Sometimes screen resolutions are not automatically detected correctly upon setup
in a terminal (Applications->accessories->Terminal) enter this:
```
sudo dpkg-reconfigure xserver-xorg
``` (just use your regular user password when it asks)
you'll be able to just skip through most of the options, leaving things as default, but then you will come to a screen that looks like [this]("http://tuxicity.files.wordpress.com/2006/12/screenshot-terminal-5.png").  scroll down and use space to select 1280x1024 and all the resolutions below it.

Then, once you get all the way through that dialog, do a ctrl-alt-backspace to restart gnome (this will log you out) then log back in, and pick your resolution from System->Preferences->Resolution

None of the guides here worked :(. My screen went out of proportion now, and I don't have the refresh rates I used to have. =\

---

