---
title: "ok more nvidia trouble"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by bertie81 on 2008-02-14
just installed 7.10
It boots just fine, and I can login...but thats as far as I can get.As soon as it starts loading the desktop, everything but the cursor freezes.
I have tried configuring the xserver-xorg manually.
Being the noob that i am, im not sure what else to try.
Also, I can only use the live CD in "video safe" mode.

system:
core 2 duo
2Gb DDR2 800
Nvidia 7800GT

---

### Post by KCormier on 2008-02-14
before you install, run the restricted driver manager under system->admin.  I've never run into the same issue but MAYBE that'll let you install the nvidia driver before/during the install....idk.  It's kinda a shot in the dark for me as i'm kinda new myself but maybe it'll help.  At least it's something to try while waiting for responses, right?

---

### Post by bertie81 on 2008-02-14
Well I kinda did that...but it wants a reboot .
So do i reboot  and let it go into regular live cd mode?
Will said driver load if i go ahead and install after the reboot?

---

### Post by jaytek13 on 2008-02-14
You say you've tried to configure xorg manually... You mean the /etc/X11/xorg.conf file? If so, under the device section, what does it say you are using for the driver?

If it says 'vesa', change it to 'nv'. I have a 7800 too and for some reason the livecd and default installation would always try to use the vesa driver which caused a lot of issues.

---

### Post by bertie81 on 2008-02-14
Sorry
What I meant by manually was   sudo dpkg-configure xserver-xorg
It was set to the NV driver...and nvidia was not an option in that list, which seems to have helped some people 
with similar issues.

---

### Post by jaytek13 on 2008-02-14
Well, at the GRUB loading screen, press escape and then boot into safe mode. Log in and then go into the directory where the file is
```
cd /etc/X11
```
Create a backup of the xorg file in case something goes wrong
```
sudo cp xorg.conf xorg.conf.backup
```
Go into the xorg file as root
```
sudo nano xorg.conf
```
and then go through the file looking for the Device section. It should look something like
```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        Busid           "PCI:2:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"

```

And check what you have for Driver. If it says vesa, change it to nv.

---

### Post by cwfloyd on 2008-02-14
Do you think that this would work for an old riva tnt2 agp as well?
I get a warning that I am running in low graphics mode at log-in.
When I dug around a little, says I am using the legacy driver, but will not keep the right settings for the monitor - every reboot says that the card and monitor cannot be detected properly.

---

