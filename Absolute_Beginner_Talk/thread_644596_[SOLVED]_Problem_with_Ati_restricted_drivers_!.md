---
title: "[SOLVED] Problem with Ati restricted drivers !"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by sob7y on 2007-12-19
Hey guyz,
I installed ubuntu 7.10 yesterday nd everythin seems to work fine..but then i got that notification that my ATI restricted drivers aren't installed and unfortunately after installing them and restartin my PC my monitor screen is no more responding and gives me an error message "Out of Range" however the OS is workin fine and i can hear some sounds at the background while initiating some tasks.
My graphics card is ATI radeon X300 msi
and the monitor is BENQ FP72E
Any ideas?!! I think ther's a problem with the screen resolution or somthn but I donno how to change it from the boot-up screen

---

### Post by overdrank on 2007-12-19
> **sob7y said:**
> Hey guyz,
I installed ubuntu 7.10 yesterday nd everythin seems to work fine..but then i got that notification that my ATI restricted drivers aren't installed and unfortunately after installing them and restartin my PC my monitor screen is no more responding and gives me an error message "Out of Range" however the OS is workin fine and i can hear some sounds at the background while initiating some tasks.
My graphics card is ATI radeon X300 msi
and the monitor is BENQ FP72E
Any ideas?!! I think ther's a problem with the screen resolution or somthn but I donno how to change it from the boot-up screen

Hi and you can try and boot into recovery mode and reconfigure your xorg with this command
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then reboot with the command ```
reboot
``` and hopefully this will bring you to the desktop. Good luck!

---

### Post by sob7y on 2007-12-19
thank's for ur reply, appreciate it!
I'll check it out..

---

### Post by weblordpepe on 2007-12-19
The /etc/X11/xorg.conf file should have entries in there for each screen resolution and stuff. You should be able to put an entry in there which matches your resolution, color depth and refresh rate.

---

### Post by sob7y on 2007-12-19
> **weblordpepe said:**
> The /etc/X11/xorg.conf file should have entries in there for each screen resolution and stuff. You should be able to put an entry in there which matches your resolution, color depth and refresh rate.

but am actually not able to see except a black screen after rebooting with an error "Out of Range"...or should I add these entries before rebboting ?!

---

### Post by sob7y on 2007-12-19
> **overdrank said:**
> Hi and you can try and boot into recovery mode and reconfigure your xorg with this command
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then reboot with the command ```
reboot
``` and hopefully this will bring you to the desktop. Good luck!

Ok this one worked, but it actually just disabled the driver which I enabled and so the graphics card is still not utilised...and also now it seems that there are no more eye-candy graphical effects after disabling the restricted driver :confused:
If anyone has any suggestions, it would be really appreciated

---

### Post by NateMan on 2007-12-19
From there you can go back in and reenable the restricted driver for your ati card. did you install xgl after you enabled the restricted drivers? another thing you can try instead of just reconfiguring the xorg.conf to defaults is to try manually editing the xorg.conf file. When you do so, find the entry for your display and change the resolution to one you know works. you can bring up this file by typing in 
sudo vi /etc/X11/xorg.conf

doing this will and installing the xgl will allow you to have both monitor and eye candy.

---

### Post by sob7y on 2007-12-19
Ok i did this and it worked ! but the refresh rate becomes 75 and when i reset it to 60 or 70 (from the "Screens and Graphics" in the administration menu) the monitor doesn't respond again after rebooting, I donno wat's the problem and I donno how to edit the screen resolution or the refresh rate in the xorg.conf file, I mean i don't kno exactly where to modify or add a statement...

---

### Post by erginemr on 2007-12-19
This is part of my "/etc/X11/xorg.conf" file, where I have instructed the graphics card to use a refresh rate of 75 Hz:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV17 [GeForce4 MX 440]"
        Monitor         "SyncMaster"
        Defaultdepth    24
        SubSection "Display"
                Modes   "1024x768_75"   "800x600_75"    "640x480_75"
        EndSubSection
EndSection
```

You can try something similar.

---

### Post by sob7y on 2007-12-19
> **erginemr said:**
> This is part of my "/etc/X11/xorg.conf" file, where I have instructed the graphics card to use a refresh rate of 75 Hz:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV17 [GeForce4 MX 440]"
        Monitor         "SyncMaster"
        Defaultdepth    24
        SubSection "Display"
                Modes   "1024x768_75"   "800x600_75"    "640x480_75"
        EndSubSection
EndSection
```

You can try something similar.

I tried it and it's still not responding, I tried adding "1280x1024@60" or "1280x1024_60" and still am gettin a refresh rate of 75...here's ma xorg.conf (renamed to xorg.txt) after using the reconfigure command and then enabling the restricted driver, how shud i edit this file to get a refresh rate of 60 or 70?
is it possible that after enabling my graphics card, it will not support a refresh rate less than 75 like 60 or 70 for example ? :confused:

---

### Post by sob7y on 2007-12-20
Everythin is workin fine now, I installed xgl...but i would like the refresh rate to be 60 or 70 because i feel that the screen is kinda dim with the rate set to 75
Thanks guys for helpin

---

### Post by weblordpepe on 2007-12-21
Cool bananas. Mark the thread as solved. (Under 'Thread Tools' near the top of the page)

---

