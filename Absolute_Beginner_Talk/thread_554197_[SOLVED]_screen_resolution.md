---
title: "[SOLVED] screen resolution"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-09-18
I dual boot with XP and can get up to 1440 X 900 on my monitor withit. I can't get close to that in Ubuntu 640 x 800? I tried "sudo gedit /etc/X11/xorg.conf, and putting 1440x900 as the first figures in each line. Then I saved the file and did ctrl+alt+backspace. When the screen came back, I went to the screen resolution (under prefs) and they did not change. How can I change these settings. Step by step please...:(

---

### Post by PurposeOfReason on 2007-09-18
What graphics card are you using? If it's a nvidia you'll need restricted drivers.

---

### Post by crjackson on 2007-09-18
> **skyjacker said:**
> I dual boot with XP and can get up to 1440 X 900 on my monitor withit. I can't get close to that in Ubuntu 640 x 800? I tried "sudo gedit /etc/X11/xorg.conf, and putting 1440x900 as the first figures in each line. Then I saved the file and did ctrl+alt+backspace. When the screen came back, I went to the screen resolution (under prefs) and they did not change. How can I change these settings. Step by step please...:(

I don't really have an exact answer to this question as of yet, but you will get more help if you include more information about current graphics card/driver being used.

---

### Post by skyjacker on 2007-09-18
> **PurposeOfReason said:**
> What graphics card are you using? If it's a nvidia you'll need restricted drivers. I have an  NVIDA GeForce4 MX. What are restricted drivers and how do I get them???:confused:

---

### Post by PurposeOfReason on 2007-09-18
System > Administration > Restricted Drivers

Or something along those lines. Install and restart.

---

### Post by alienexplorers on 2007-09-18
Try using the ENVY script to load your nvidia drivers.  You must run ENVY to remove any old drivers you have, then run ENVY again to load the new drivers.  This way you will have access to nvidia-settings to configure your video board. To run nvidia-settings run in terminal:
> sudo nvidia-settings

---

### Post by skyjacker on 2007-09-18
> **alienexplorers said:**
> Try using the ENVY script to load your nvidia drivers.  You must run ENVY to remove any old drivers you have, then run ENVY again to load the new drivers.  This way you will have access to nvidia-settings to configure your video board. To run nvidia-settings run in terminal:  Worked like a charm:)... One question tho - Envy web site says to remove the driver it installed before updating Ubuntu. How do I do that, as I plan to update to 7.10?

---

### Post by alienexplorers on 2007-09-18
Just run ENVY again and remove your current driver before installing 7.10...  After you install 7.10 you would run ENVY again to reload your drivers.

---

### Post by skyjacker on 2007-09-18
> **alienexplorers said:**
> Just run ENVY again and remove your current driver before installing 7.10...  After you install 7.10 you would run ENVY again to reload your drivers.
Thanks for your quick replies and the help... Ubuntu rocks:guitar: and so does this forum

---

